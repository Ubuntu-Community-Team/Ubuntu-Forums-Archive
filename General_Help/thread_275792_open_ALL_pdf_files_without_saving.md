---
title: "open ALL pdf files without saving"
date: 2006-10-11
forum: General Help
---

### Post by bollocks00 on 2006-10-11
I've installed acrobat reader and associated pdf files with it according to
[http://ubuntuguide.org/wiki/Dapper#How_to_install_PDF_Reader_.28Adobe_Reader.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_PDF_Reader_.28Adobe_Reader.29_with_Plug-in_for_Mozilla_Firefox)

Seems like everything works. If I double click a saved pdf file it opens with acrobat, and if I click on certain web links, it opens in acrobat without asking where to save it.

Problem is: When I try to view pdf files from one of my class websites, it still always needs to save them first. I'd like for it to just open, like the rest of the links.

The links that ask to be saved look like:
.../servlet/ShowFile?contentid=408570

The links that just open look like:
[http://www.copyright.gov/legislation/dmca.pdf](http://www.copyright.gov/legislation/dmca.pdf)

That's the only way I can really think to describe the problem.  Anyone know of a way to describe the solution? :cool:

---

### Post by bollocks00 on 2006-10-18
no solutions?

---

### Post by mssever on 2006-10-18
I'm guessing that it's a server configuration issue. When web servers serve files, they can send a header that causes browsers to try to save the file rather than displaying it. It sounds like that's how your server is set up, and you should contact the server admin to resolve the issue.

Now, if other computers/browsers/OSes behave like you want, then I don't know what the problem is.

---

### Post by aysiu on 2006-10-18
Try the [PDF Download Firefox extension](https://addons.mozilla.org/firefox/636/). It allows you to specify what to do with PDFs every time... or to ask what to do every time.

Theoretically, Firefox already does this, but PDF Download actually works that way. Firefox doesn't always.

---

### Post by bollocks00 on 2006-10-18
Annoying thing is, it works fine with firefox in windows.  I tried downloading the extension, but it doesn't seem to make any difference.  Any other ideas?

---

### Post by mssever on 2006-10-18
Here's a stab in the dark: let's find out what headers the server is sending. Firefox probably has extensions available to find the headers, but you can also get them from the terminal.

In these instructions, <hostname> refers to the hostname of your server. If the URL was http://www.example.com/bad_file.pdf?use=1, then the hostname would be www.example.com. <path> refers to the path and filename, /bad_file.pdf?use=1 in our example. <blank line> means a blank line (obviously).

Type the following to get started: ```
telnet <hostname> 80
```Once it connects, type the following, preserving the line breaks. Note that if you make a mistake, you can't go back and fix it. You have to start over from the beginning. ```
HEAD <path> HTTP/1.1
Host: <hostname>
<blank line>
```Post the results here.

---

### Post by bollocks00 on 2006-10-19
```

lenny@IBM:~$ telnet coursework-g.stanford.edu 80
Trying 171.67.16.246...
Connected to cw-app18.stanford.edu.
Escape character is '^]'.
 HEAD /coursework/servlet/ShowFile?contentid=408459 HTTP/1.1
Host:coursework-g.stanford.edu^[[D

HTTP/1.1 400 Bad Request
Date: Thu, 19 Oct 2006 04:06:51 GMT
Server: Apache/2.0.54 (Unix) mod_ssl/2.0.54 OpenSSL/0.9.7g mod_jk/1.2.14 WebAuth/3.2.8
Content-Length: 376
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>400 Bad Request</title>
</head><body>
<h1>Bad Request</h1>
<p>Your browser sent a request that this server could not understand.<br />
</p>
<hr>
<address>Apache/2.0.54 (Unix) mod_ssl/2.0.54 OpenSSL/0.9.7g mod_jk/1.2.14 WebAuth/3.2.8 Server at coursework-g.stanford.edu Port 80</address>
</body></html>
Connection closed by foreign host.

```

The site is SSL secured (https), so would I have to login with telnet first for this to work?  If so, how is this done?  Also, the site is coursework-X, where the "X" is a different letter each time I log in.  Unfortunately, I have not been able to find another site that makes me download pdfs instead of opening them straightaway.  Though everything works with firefox in windows.  I think it's a conspiracy.

Edit: forgot to mention that I tried it with HTTPS/1.1 too, but no luck.

---

### Post by mssever on 2006-10-19
I don't know how to use telnet to talk to SSL sites. I suggest that you look for a Firefox extension that captures the HTTP headers. If I'm not mistaken, there's one known as Live HTTP Headers.

Given that the problem is site-specific, I'm quite certain that this is a server issue. However, it would be good to diagnose the problem before complaining to the server admin. Hence, the headers.

---

### Post by bollocks00 on 2006-10-19
hmmm, unfortunately the latest live HTTP headers isn't compatible with firefox 2.0.  I guess I will endure and try again in a while.

Thanks for the help!

---

