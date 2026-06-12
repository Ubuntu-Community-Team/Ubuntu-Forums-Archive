---
title: "Executing Python in Apache"
date: 2007-09-11
forum: General Help
---

### Post by srunni on 2007-09-11
Hi,

Does anyone know how to enable execution of Python scripts in Apache on Ubuntu Feisty?

Thanks in advance for the help!!!

---

### Post by LaRoza on 2007-09-11
There are a few things you need to do:

* Make sure Apache will execute them, sorry, don't know how exactly to do this, look at the documentation, google will help here.
* Make sure the shebang line is correct
* Make sure the file extension is right, on my home server, which I use for testing, the extension for all CGI scripts is CGI, whether it is written in C, Python or Perl.
* Make sure the directory is allowed to execute scripts.

In this case, google will help, sorry I can't say more, because the Apache I use is on Windows, where all my browsers are (Web dev testing)

---

### Post by srunni on 2007-09-11
Anyone else? The one thing I need help with is changing the settings in Apache so I can execute the scripts.

---

### Post by fragos on 2007-09-12
I don't recall the actual configuration for CGI but warn you that it's different between Apache and Apache2.

---

### Post by srunni on 2007-09-13
Well, I'm running Apache2, if that's any help.

---

### Post by fragos on 2007-09-13
[http://httpd.apache.org/docs/2.0/howto/cgi.html](http://httpd.apache.org/docs/2.0/howto/cgi.html)

---

