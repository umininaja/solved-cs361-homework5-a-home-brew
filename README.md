Download Link: https://assignmentchef.com/product/solved-cs361-homework5-a-home-brew
<br>
This homework has the following learning objectives:

Learn how to follow a network protocol (in this case, http)

Learn network/socket programming Learn some simple multithreading

<a href="https://www.google.com/url?q=https%3A%2F%2Fclassroom.github.com%2Fa%2FatZ2E85c&amp;sa=D&amp;sntz=1&amp;usg=AFQjCNF_spkjogP0UfhmjJSTqxRzTQFLSw"><strong>Github classroom invitation link</strong></a>

In this homework, we’ll look at the HTTP protocol as a Web server. After creating your personal repository, you will find that the hw5 directory contains:

homework5.c: Skeleton code for the server side of a TCP application. This will be the primary file for this assignment, but feel free to modularize and create other files if you prefer to do so.

WWW/: A directory containing example files for your Web server to distribute.

thread_example.c: Example code that illustrates a very simple threaded programming scenario. You are not required to use or make any changes to this file, but you should understand what it does.

A Makefile. If you modularize your code into different files, make sure those changes are reflected in the Makefile (and don’t forget to git add those files to your personal git repo!).

Your server program will receive two arguments: 1) the port number it should listen on for incoming connections, and 2) the directory out of which it will serve files (often called the document root in production Web servers) For example:

https://sites.google.com/uic.edu/cs361summer2020/homeworks/hw5?authuser=1

document root in production Web servers). For example:

<a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">CS 361 Summer 2020</a>                            <a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">Home</a>         <a href="https://sites.google.com/uic.edu/cs361summer2020/schedule?authuser=1">Schedule</a>          <a href="https://sites.google.com/uic.edu/cs361summer2020/homeworks?authuser=1">Homeworks</a>

$<a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1"> ./homework5 8080 WWW</a>

This command will tell your Web server to listen for connections on port 8080 and serve files out of the WWW directory. That is, the WWW directory is considered ‘/’ when responding to requests. For example, if you’re asked for /index.html, you should respond with the file that resides in WWW/index.html. If you’re asked for /dir1/dir2/file.ext, you should respond with the file WWW/dir1/dir2/file.ext.

<h1>Requirements</h1>

In addition to serving requested files, your server should handle at least the following cases:

<ol>

 <li>HTML, text, and image files should all display properly. You’ll need to return the proper HTTP Content-Type header in your response, based on the file ending. Also, other binary file types like PDFs should be handled correctly. You don’t need to handle everything on that list, but you should at least be able to handle files with html, txt, jpeg, jpg, gif, png, and pdf extensions.</li>

 <li>If asked for a file that does not exist, you should respond with a 404 error code with a readable error page, just like a Web server would. It doesn’t need to be fancy, but it should contain some basic HTML so that the browser renders something and makes the error clear.</li>

 <li>Some clients may be slow to complete a connection or send a request. Your server should be able to serve multiple clients concurrently, not just back-to-back. For this homework, use multithreading with pthreads to handle concurrent connections. We’ll try event-based concurrency in a future homework assignment.</li>

 <li>If the path requested by the client is a directory, you should handle the request as if it was for the file html inside that directory. Hint: use the stat() system call to determine if a path is a directory or a file. The st_mode field in the stat struct has what you need.</li>

 <li>The Web server should respond with a list of files when the user requests a directory that does not contain an html file. You can read the contents of a directory using the opendir() and readdir() calls. Together they behave like an iterator, that is, you can open a (DIR *) with opendir and then continue calling readdir(), which returns info for one file, on that (DIR *) until it returns NULL. In lab8, you will be provided with and example code on how to read in contents of a directory and print them to stdout. Note that there should be no additional files created on the server’s disk to respond to the <span style="text-decoration: line-through;"><u>r</u></span>equest. The response should mimic result of running python -m SimpleHTTPServer</li>

</ol>

https://sites.google.com/uic.edu/cs361summer2020/homeworks/hw5?authuser=1Wh t       ti            h       ld b     bl         t           t i               b t    f                 b t       i        f fil   f

W<a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">hen testing, you should be able to </a>retrieve byte-for-byte copies of files from your server.

Us<a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">e wget or curl to fetch files and md</a><a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">CS 361 Summer 2020</a> 5sum or dif<a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">Hom</a><a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">f to co</a><a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">e</a>mp<a href="https://sites.google.com/uic.edu/cs361summer2020/schedule?authuser=1">are the fe</a><a href="https://sites.google.com/uic.edu/cs361summer2020/schedule?authuser=1">Schedule</a> tc<a href="https://sites.google.com/uic.edu/cs361summer2020/homeworks?authuser=1">hed fil</a><a href="https://sites.google.com/uic.edu/cs361summer2020/homeworks?authuser=1">Homework</a><a href="https://sites.google.com/uic.edu/cs361summer2020/homeworks?authuser=1"> with t</a><a href="https://sites.google.com/uic.edu/cs361summer2020/homeworks?authuser=1">s</a>h<span style="text-decoration: line-through;">e</span>

original. We will do this when grading. <em>For full credit, the files need to be exact replicas of the original.</em>

<h1>Tips</h1>

Please read the skeleton code to get a feel for what is available and what you should be doing.

As of the release of this assignment, we have not covered the concepts related to networking in class; to start on this homework, take a look at chapter 11 (especially 11.5 and 11.6) from the textbook to learn more about the network programming in C.

The labs on 3/30 and 4/6 will help you get started on the assignment as well.

Take compiler warnings seriously. Unless it’s an unused variable, you should address the warning as soon as you see it. Dealing with a pile of warnings just makes things more difficult later.

Test your code in small increments. It’s much easier to localize a bug when you’ve only changed a few lines.

If you need to copy a specific number of bytes from one buffer to another, and you’re not 100% sure that the data will be entirely text, use memcpy() rather than strncpy(). The latter terminates early if it finds a null terminator (‘ ’).

If you’re trying to do some sort of specific string or memory manipulation, feel free to ask if there’s a better/recommended way to do it rather than brute force. Often there may be a standard library function that will make things easier.

<strong>Roughly, your server should follow this sequence:</strong>

<ol>

 <li>Read the arguments, bind to the specified port, and find your document root (you might find the chdir() system call helpful).</li>

 <li>Accept a connection, and hand it off to a new thread for concurrent processing.</li>

 <li>Receive and parse a request from the client.</li>

 <li>Look for the path that was requested, starting from your document root (the second argument to your program). One of four things should happen:

  <ol>

   <li>If the path exists and it’s a file, formulate a response (with the Content-Type header set) and send it back to the client.</li>

   <li>If the path exists and it’s a directory that contains an index.html file, respond with that</li>

   <li>If the path exists and it’s a directory that does NOT contain an index.html file, respond</li>

  </ol></li>

</ol>

https://sites.google.com/uic.edu/cs361summer2020/homeworks/hw5?authuser=1

p y     , p <a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">with a directory listing.</a>

<a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">CS 361 Summer 2020</a>                            <a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">Home</a>         <a href="https://sites.google.com/uic.edu/cs361summer2020/schedule?authuser=1">Schedule</a>          <a href="https://sites.google.com/uic.edu/cs361summer2020/homeworks?authuser=1">Homeworks</a>

<ol start="4">

 <li><a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">If the path does not exist, respo</a>nd with a 404 code with a basic error page.</li>

</ol>

<ol start="5">

 <li>Close the connection, and continue serving other clients.</li>

</ol>