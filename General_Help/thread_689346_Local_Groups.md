---
title: "Local Groups"
date: 2008-02-06
forum: General Help
---

### Post by tortue17 on 2008-02-06
Hi,

I just have a simple and little question :
How can we known the utility of a local group ?
For example, we known the effect to add a user in the cdrom group or the floppy group, but there are some groups that I have no idea, for example, dip, uucp, gnats, utmp,....

How can we know the effect of a group ?

Thanks

---

### Post by geraldm on 2008-02-06
dip - Dial In Program
uucp - Unix to Unix CoPy 

A line in /etc/group means nothing unless it is connected to a line in /etc/passwd.  
Use "grep" or "ls" command to find its uses.

~.1% grep gnats /etc/group
gnats:x:41:
~.1% grep gnats /etc/passwd
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
~.1% ls -l /var/log/btmp
-rw-rw-r-- 1 root utmp 384 2008-02-04 17:01 /var/log/btmp

utmp is the group used by programs such as: who, w, finger

~.1% ls -ld /etc/ppp/peers
drwxr-s--- 2 root dip 4096 2007-11-28 17:04 /etc/ppp/peers
~.1% ls -l /etc/ppp/peers/provider
-rw-r----- 1 root dip 267 2007-11-28 17:03 /etc/ppp/peers/provider

Gerald

---

### Post by tortue17 on 2008-02-07
Thanks for your answer.

But for some groups, we don't known exactly, what they do (sasl for example)

else I make 
find / -group **group** -print 
to find files associate to this group

There is no best way to know about the group ?

---

