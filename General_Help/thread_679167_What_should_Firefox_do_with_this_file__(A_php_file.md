---
title: "What should Firefox do with this file?  (A php file)"
date: 2008-01-26
forum: General Help
---

### Post by drdont on 2008-01-26
I have php files on an external website and Firefox handles them correctly.  If I try and view the files locally Firefox pops up a dialogue box and asks:  What should Firefox do with this file?
What does it take to make this work?  (I think it was mozilla on Red Hat 7.3 that knew what to do).  I'm using Ubuntu 7.10.

Thanks,

Don Tveter, don@ dontveter.com

---

### Post by nemilar on 2008-01-26
PHP files have to be parsed/processed by a web server (e.g, apache) first.  When they're being served externally, the server is doing that work before it sends it to your browser (firefox).  So if you have the files locally, trying to open them in firefox is basically skipping a step.

If you want to work on PHP files locally, you'll need to install Apache (or another webserver) and PHP, put them in your web server directory (/var/www) and then use firefox to view them through [http://localhost](http://localhost)

---

### Post by fireman biff on 2008-01-26
Maybe it just doesn't know that its an html file because it has a php extension, or its actually php code which can't be opened directly in Firefox.

If it's a page you saved, try renaming it to have a '.html' extension. If it's php code you'll probably need to use a web server to view it (or just keep viewing it online).

---

