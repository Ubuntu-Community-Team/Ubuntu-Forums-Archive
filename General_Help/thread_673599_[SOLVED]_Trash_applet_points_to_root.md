---
title: "[SOLVED] Trash applet points to root"
date: 2008-01-20
forum: General Help
---

### Post by goodfella on 2008-01-20
For some strange reason the trash applet points to my root partition.  Anybody know how to fix this?  I am using edgy eft.

---

### Post by FXEF on 2008-01-20
> **goodfella said:**
> For some strange reason the trash applet points to my root partition.  Anybody know how to fix this?  I am using edgy eft.

You should have two .Trash directories. 

One in /root/.Trash 
root@earth:~# cd /root/.Trash
[email]root@earth:~/.Tras[/email]h# 

and one in /home/your_username.
bob@earth:~$ cd .Trash
[email]bob@earth:~/.Tras[/email]h$ 

When you delete files they should go to  /home/your_username/.Trash

When you empty the Trash; the files will no longer appear in /home/your_username/.Trash and you will no longer have access to them. For all practical purposes they are gone.

---

### Post by goodfella on 2008-01-21
Thanks for the reply.  But on my system there is no /root/.Trash directory.  Also, the .Trash directory in my home folder is empty.

---

### Post by imbjr on 2008-01-21
This might apply:

[http://ubuntuforums.org/showthread.php?t=633329](http://ubuntuforums.org/showthread.php?t=633329)

---

### Post by goodfella on 2008-01-21
Thanks for your help imbjr.  By following the link you suggested I was able to fix my problem thanks.

---

