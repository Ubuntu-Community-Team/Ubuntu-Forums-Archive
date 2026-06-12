---
title: "Question about file permissions"
date: 2008-06-17
forum: General Help
---

### Post by jellystones on 2008-06-17
Hi I have a file that has its permissions set to 777.

This file is viewable on the network, but for some reason remote computers can only read this file, and not write to it.



Anyway I have a theory that since the remote computer is a user that is not defined in /etc/passwd, it cannot write to the file even when when its permissions are 777 (I cant test this theory until my system administrator gets back).

Anyway is this correct, or does anyone else have any other ideas?

---

### Post by pytheas22 on 2008-06-17
How are remote users trying to access the file (i.e. are they logging in via ssh, using a samba or NFS share, or is this file hosted on a web server)?  I don't think /etc/passwd is the problem.

---

### Post by jellystones on 2008-06-17
> **pytheas22 said:**
> How are remote users trying to access the file (i.e. are they logging in via ssh, using a samba or NFS share, or is this file hosted on a web server)?  I don't think /etc/passwd is the problem.

Its via an NFS share.

---

### Post by pytheas22 on 2008-06-17
I don't know much about how NFS works but I don't see why they shouldn't be able to write to it remotely.  Are you sure the permissions are 777?  Did you set them from the command-line?  If you did it using Nautilus, sometimes it screws up.  What does an ls -l of the file tell you about permissions?

---

### Post by jellystones on 2008-06-17
> **pytheas22 said:**
> I don't know much about how NFS works but I don't see why they shouldn't be able to write to it remotely.  Are you sure the permissions are 777?  Did you set them from the command-line?  If you did it using Nautilus, sometimes it screws up.  What does an ls -l of the file tell you about permissions?

I set them via command-line with chmod. ls -l shows me rwxrwxrwx.

So for the 3rd 7 in 777, which refers to *all* users, does *all* refer to any user, or is it restricted to the set of users defined in /etc/passwd

---

### Post by pytheas22 on 2008-06-17
I think that 777 means anyone can write.  But I'm wondering if the problem might lie with permissions on the share itself.  Did you mount it read-only, and did you make sure that directory you're mounting as a share has write access for everyone?

---

### Post by bodhi.zazen on 2008-06-17
How did you configure NFS ? what is in your /etc/export

---

### Post by jellystones on 2008-06-17
Hey it turns out there was an extra security layer installed that overrides the default linux permissions (an ACL).

Ive figured everything out, thanks for the help.

---

