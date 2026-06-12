---
title: "[SOLVED] use of e2fsck"
date: 2007-03-28
forum: General Help
---

### Post by anyoneseenmypenguin on 2007-03-28
I have found alot of info about e2fsck and the warnings about the use on mounted hard drives. My question is I would like to run a file system check at any time similar to running scandisk. I cannot "unmount" my drive for some reason either before ubuntu loads or at the splash screen(ctrl>alt>F1) comes up with unknown command. Is there a way to do a live file system check or force a check at the next start up like a windows system. Arggggh I hate using that word (Windows) I'm using ubuntu 6.10 on a Mac G3. I have only one hard drive and nothing fancy on this laptop.  /dev/hda file system ext3

---

### Post by acormack on 2007-03-28
Running fsck on a mounted drive is a very bad idea. 

What you need to do is force a fsck on the next reboot.  Unfortunately the -F flag on the shutdown command is missing from [k]ubuntu (according to the man page) so you need to create an empty file in the root directory called forcefsck.

You can do this with the following command

sudo touch /forcefsck

Then reboot.  

There is a very thorough article on this topic at 

[https://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/](https://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/)

Hope this helps.

Alec

---

### Post by anyoneseenmypenguin on 2007-03-28
Hi Alec thanks for your reply works perfectly your answer was exactly what I was looking for short and straight to the point. Also the article is very good as well. Many thanks your  help is appreciated. :)

---

### Post by anyoneseenmypenguin on 2007-03-28
Would also like to know where the file is located that controls the file system check every 30 bootups and if we can modify it.:p

---

### Post by confused57 on 2007-03-28
> **anyoneseenmypenguin said:**
> Would also like to know where the file is located that controls the file system check every 30 bootups and if we can modify it.:p
See this thread:
[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

and this website:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by anyoneseenmypenguin on 2007-03-29
Thanks for your help the links are very good very useful information.
Thanks again. :) :)

---

