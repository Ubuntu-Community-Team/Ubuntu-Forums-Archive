---
title: "hibernation problem on 8.04 after meddling with swap"
date: 2008-05-24
forum: General Help
---

### Post by Borzo on 2008-05-24
Hi All,

I needed to move and resize my swap partition, and i noticed that afterwards hibernation stopped working. I mean it seems it goes to hybernation but does not restore it, it simply goes to the login screen.

any ideas?... thanks!

---

### Post by jimbob on 2008-05-24
Do a top command on a terminal and see if there is swap space available for use.

Chances are the system assigned a new UUID to your swap partition and it no longer matches the UUID in /etc/fstab.  Do a blkid command in the terminal and compare the two.

---

### Post by Borzo on 2008-05-24
I changed the UUID in fstab right after doing the changes, swap seems Ok, top is Ok, here's a free printout:


             total       used       free     shared    buffers     cached
Mem:        506276     479240      27036          0       1064      62536
-/+ buffers/cache:     415640      90636
Swap:      1477940     194464    1283476

I don't know how relevant this may be, but I also installed compiz-fusion after the changes, i don't see how that could affect hibernation, but i thought i'd mention it.

Another thing I noticed is that swapoff is not working, it spews out:
/dev/sda5: Cannot allocate memory


thanks!


> **jimbob said:**
> Do a top command on a terminal and see if there is swap space available for use.

Chances are the system assigned a new UUID to your swap partition and it no longer matches the UUID in /etc/fstab.  Do a blkid command in the terminal and compare the two.

---

### Post by Borzo on 2008-05-26
I found a an instance of the old UUID for swap in 

/etc/initramfs-tools/conf.d/resume

however changing it to the new swap partition UUID did not help...

---

### Post by jimbob on 2008-05-26
You can generate an updated initramfs with this command:

**[COLOR="Blue"]update-initramfs -u[/COLOR]**

---

### Post by mooz123 on 2008-05-27
Hi,

this post helped me to get hibernation working, I want to log my experiences. I also changed my swap partition sometime ago. 

>top (in terminal) told me that there was no swap memory available
(>free gives the same answer, it returns just the first few lines that >top returns)

I had some problems with >blkid, then I realised I should type >sudo blkid.
this gives the current uuid's of the various partitions.

I opend etc/fstab and saw that the value there was wrong. Copy-Paste ready!

Thanks for discussing it.

---

### Post by undecisive on 2008-11-11
Yay! Thank you all - was going mad, this post saved the day. I actually did all the things suggested in this post without testing at each stage, but the combination of getting the UUID (sudo blkid) and using that in /etc/fstab, changing the uuid in /etc/initramfs-tools/conf.d/resume, then running "sudo update-initramfs -u", then hibernating... after that, hibernation was as before! Splendid! :)

Actually, that last command spat a warning at me: 

WARNING: found more than one resume device candidate:

Not sure what it was basing that on, but it didn't seem to affect my ability to hibernate successfully, so probably not an issue. At least, not for now...

Thanks once again!

---

### Post by kigali on 2009-06-01
It has worked for me. I had the same symptoms as the thread author, apparently updating /etc/initramfs-tools/conf.d/resume solved the problem.

Big thanks!

---

