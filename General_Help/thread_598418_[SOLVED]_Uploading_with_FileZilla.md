---
title: "[SOLVED] Uploading with FileZilla"
date: 2007-10-31
forum: General Help
---

### Post by btaylor101 on 2007-10-31
Whenever I upload a index.html file to my web folder, /var/www/foldername, with FileZilla I get the dreaded 403 error. Once I log into the box and change the permissions of the file the web page can be seen. How do I get FileZilla to stop changing permissions? The end goal is to have a user upload their webpage using FileZilla, but not have them log into the linux box and change the permissions. If anyone knows the fix I would appreciate it.

---

### Post by timcredible on 2007-10-31
if you're using ftp for the file transfer, try gftp, i've been using it to upload files to web server for quite some time and it works fine.  Alternatively, there are apps out there that make web server management easier, notably kompozer and joomla.  for a short overview of  them, check out [http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=16&Itemid=32](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=16&Itemid=32)

---

### Post by btaylor101 on 2007-10-31
I must have missed the setting earlier, but I am able to change the permissions of the document now by right clicking and choosing File Attributes. I was curious if there is any other way of having the file automatically set with the correct permissions.

---

