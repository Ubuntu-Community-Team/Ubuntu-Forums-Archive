---
title: "[SOLVED] Media Server (ftp? ssh?)"
date: 2007-11-02
forum: General Help
---

### Post by ghandi69_ on 2007-11-02
Hey guys,

I'm setting up a home server for myself and all of my roommates.  I will be the admin of sorts.  The server is already working, I can connect remotely to the machine using ssh(command line or using filezilla), and I can copy and send files.  

However, I wish to be able to set it up so I can log in using a certain username and password, and be able to read/write, but my roommates will only be able to read(copy) from the server remotely.  Both of us would need access to the same files (all of which are located under /home/adminz .  adminz is what I currently login with.

I guess the trick is to log under a different name and still be able to read from adminz home folder?

---

### Post by ghandi69_ on 2007-11-02
Oh..

Well that was easy enough.  If using simple SSH to connect, I just created users as needed 

useradd jimi

passwd jimi

and gave them a password.  I didn't even have to give them a home directory.  They can remotely login using ssh with filezilla, and grab whatever they need, and they do not have permissions to do anything!

---

