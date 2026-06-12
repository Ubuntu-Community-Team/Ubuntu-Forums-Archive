---
title: "Help with AUFS"
date: 2008-05-25
forum: General Help
---

### Post by Fox5 on 2008-05-25
Hey all,
I was following this tutorial
[https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash#head-0899d94561ba3cca25dac60474756d2e3f8fab05](https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash#head-0899d94561ba3cca25dac60474756d2e3f8fab05)
For how to mount / as read only to speed up system performance.

I originally followed the tutorial with a single partition, and it worked, but I didn't like having to delete aufs=tmpfs from the grub menu list in order to save ANY files.

So I reformatted and made two partitions, one for /home and one for /, with the idea that /home would always remain writable.
I assumed that the same procedure that worked for a single partition would work for two. I was wrong.

Booting up with aufs=tmpfs, the system can't find my /home partition. Trying to log in just causes me to be logged back out immediately. 
Booting up normally (without aufs=tmpfs) results in many errors about a read only file system. What gives, I didn't have this problem previously. It still gives me errors not being able to find my home partition, and on top of that I'm kicked to a terminal screen.
Unfortunately, I'm not familiar with Linux scriping or AUFS, so I'm not sure what's wrong, but it just seems so weird that my home partition disappears to the system and that my root partition gets locked as read only.

---

### Post by Perkins on 2010-06-05
I am not 100% certain, but I remember reading about somebody with a similar problem, and it turned out that it was due to the scripts being used replacing /etc/fstab on startup...  I don't remember precisely what they did about it, but the thread was on this forum, so you should be able to find it.

---

