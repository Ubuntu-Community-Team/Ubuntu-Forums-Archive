---
title: "ftp"
date: 2006-10-09
forum: General Help
---

### Post by lemonsCC on 2006-10-09
I have seen countless guides on how to set up ftp servers and have a couple questions. From what I have read the most used server is proftpd.


[LIST]
[*]When I set up my ftp user and create their "home" folder can I specify this to be a partition on my HD?  I want to do this so that when my family uploads stuff they can later move it to their home folders, etc.

[*]How do you access this server from other computers?

[*]How secure is this ftp server?  It will hopefully only have acess to that shared partition but need I worry about the rest of my data and computer?
[/LIST]

Thanks!:KS

EDIT:  Also is ftp the best way to go for my needs?  I just want my family to be able to upload (maybe download) simple word documents, etc.

---

### Post by taurus on 2006-10-09
1.  Why not create an account for each member of your family on your machine so they can upload/download from their home directory!!!

2.  You can access your machine by using IP address...

3.  It's as secure as you want it to be.  I would turn off the anonymous account in proftpd.conf.  Also, don't allow users to go anywhere except their own home directory.

Just so you know, vsftpd is real easy to set up too and it's in the repos as well.

---

### Post by lamego on 2006-10-09
It is safer to not use FTP at all, just use sshd on the server, and an SFTP over SSH capable client like FileZilla on the clients (I assume they are Windows clients), SFTP will make sure all the traffic is encrypted during the transfers.

---

### Post by lemonsCC on 2006-10-09
lamego,

How would I go about using sshd and setting up ssh?

---

### Post by lemonsCC on 2006-10-09
ok i got vsftpd up and running.  I set my ubuntu box to have a static ip at 192.186.1.130

I can connect to it from inside my home network.  **How do I connect from an external computer?**

For example sake my ISP IP is :12.123.123.12

---

