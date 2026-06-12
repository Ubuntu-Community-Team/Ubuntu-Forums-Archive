---
title: "FTP Server administration"
date: 2006-09-21
forum: General Help
---

### Post by andnos on 2006-09-21
Hi I'm running 6.06.1 Server and I need to add about 30 FTP users and specify the directory that they can log-in into and that they can read/write to that directory, how do I handle this?

Thanks for any help,

Andy

---

### Post by dcstar on 2006-09-24
> **andnos said:**
> Hi I'm running 6.06.1 Server and I need to add about 30 FTP users and specify the directory that they can log-in into and that they can read/write to that directory, how do I handle this?

Thanks for any help,

Andy

You can do it one by one manually in System-Administration-Users and groups, or have a look at "man adduser" for a way that you may be able to automate it via a script.

---

### Post by towsonu2003 on 2006-09-24
I wonder whether there is a way of doing this with a web page (like, how does a web hosting company let's you create a new account and ftp to it). that way, you can just let your users create their own accounts.

---

