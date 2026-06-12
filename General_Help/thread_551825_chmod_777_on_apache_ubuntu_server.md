---
title: "chmod 777 on apache ubuntu server"
date: 2007-09-15
forum: General Help
---

### Post by bone2006 on 2007-09-15
I wanted to share a directory on a server, so I created a directory on /var/www/share and I applied chmod 777 to the directory and I can see that people can now view it, but my question is should I be concern about writing?  The only thing that will be posted there will be compressed files with one way traffic, so I was wondering if I should maybe apply another command besides 777 for security?

Thanks in advance

---

### Post by rivalarrival on 2007-09-15
I would do 744, not 777...  

744 = user: read/write/execute; group: read; other: read.

This page has a good explanation for the octal permissions settings with chmod
[http://www.december.com/unix/ref/chmod.html](http://www.december.com/unix/ref/chmod.html)

---

### Post by bone2006 on 2007-09-16
with 744 nobody could access the folder, I had trouble even accessing it, so I put it back to 777.

Update:  All folders are 755 and only a few folders that I want people to upload files to are 777

---

