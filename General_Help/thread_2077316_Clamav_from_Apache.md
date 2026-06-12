---
title: "Clamav from Apache"
date: 2012-10-28
forum: General Help
---

### Post by kozlojak on 2012-10-28
I have a python script running from Apache that calls clamdscan to scan a file when it is uploaded. But it always get a access denied error, it does work when I manually run the scan from the terminal.

I am sure this has something to do with permissions or App Armour, I am just not sure where to look. Any insight or help would be great.

---

### Post by Lars Noodén on 2012-10-28
You can open up a terminal and monitor Apache's error log for activity when you try to upload a file.  

```

tail -f /var/log/apache2/error.log

```

Usually it will give you a good hint at what to look at next.

---

### Post by kozlojak on 2012-10-28
The only error is this:

ERROR: Can't access file /webapp/tmp/780559/*
ERROR: Can't access file /webapp/tmp/780559/rar/*

/webapp/tmp/780559/ is the directory the compressed file is extracted to and /webapp/tmp/780559/rar/ is just a subdir of the compressed file

---

### Post by Lars Noodén on 2012-10-28
Do you have a [Directory](http://httpd.apache.org/docs/2.2/mod/core.html#directory) configured for /webapp/tmp/780559/ in your virtual host's configuration file?

---

