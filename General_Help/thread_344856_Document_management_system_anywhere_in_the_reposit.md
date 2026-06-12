---
title: "Document management system anywhere in the repositories?"
date: 2007-01-23
forum: General Help
---

### Post by ranarion on 2007-01-23
I am looking for a document management system that facilitates cataloguing, indexing and tagging scanned documents, images, PDFs and HTML pages. Is there anything suitable in the Ubuntu repositories? Or does anyone have an idea how I could do this "manually", by using console tools etc.?

---

### Post by Jussi Kukkonen on 2007-01-23
Haven't used it, but I know MyDMS is in the repos: [http://dms.markuswestphal.de/about.html](http://dms.markuswestphal.de/about.html)

---

### Post by ranarion on 2007-01-23
Thank you for the hint. Additionally, I just discovered knowledgetree is in the universe repository, and I'll have a look at the two. I'd appreciate any further hints, however -- just in case there are better ones out there :-)

---

### Post by nhenry on 2008-01-12
I'd reccomend mydms

Install a [LAMP Server]("https://help.ubuntu.com/community/ApacheMySQLPHP")

from command line:
administrator@ubuntu:~$ sudo apt-get install mydms
administrator@ubuntu:~$ sudo ln -s /usr/share/mydms/www /var/www/dms

Go to [http://localhost/mydms]("http://localhost/mydms")
Username: admin
Password: admin

---

