---
title: "uninstall 14.04.1 from windows dual boot"
date: 2014-10-09
forum: General Help
---

### Post by debroos on 2014-10-09
I have recently uninstalled a flaky dual booting 12.04 from an XP netbook and installed 14.04.1 with Wubi and the 14.04.1. iso in the same folder.  I had a couple of goes installing it online but as soon as it installed I had "Permission denied....etc", - hence the method I used.  The new install doesn't work with "serious errors found whilst checking the disk.. and so on."  I had a look at a log and it appears "read only files" could be the cause.  I don't wish to waste any more time grappling with Ubuntu, much as I like it on the few occasions when it has worked smoothly, so I would like to remove it completely from the PC.  Unlike the 12.04 install, this edition created and installed itself on a partition (fat 32).  Can I simply uninstall it from windows and remove it from the boot menu via 'boot ini' as with 12.04, or should I simply delete the partition?  If I do this, how do remove the boot entry and will I need to reformat the deleted partition.

Thanks for any help

---

### Post by yancek on 2014-10-09
Wubi is no longer supported by Ubuntu although people still occasionally get it to work on some systems.  I've never used it myself but, my understanding is that you can remove it the same way you do any other program in windows.  The link below is the official wubi guide and Section 4 discusses removing it.  

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by debroos on 2014-10-10
Thanks for that Yancek.  I have uninstalled and reinstalled it to see if upgrading to 14.04.1 online does the trick.  If it doesn't, I yield. :p

---

### Post by hakuna_matata on 2014-10-11
> **debroos said:**
> I have uninstalled and reinstalled it to see if upgrading to 14.04.1 online does the trick.  If it doesn't, I yield. :razz:
If you use Wubi and 14.04.1, maybe this [thread]("http://ubuntuforums.org/showthread.php?t=2217829&p=12992482#post12992482") helps. Especially post [#10]("http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696") and surrounding posts

---

### Post by debroos on 2014-10-11
Many thanks for that Hanuka - changing the ro to rw enabled the boot up.  I opened the terminal to do the same with the text editor as described, which I did, but I am unable to save it because it's a read only file.  Do you know how I might change its properties?

---

### Post by hakuna_matata on 2014-10-11
> **debroos said:**
> I opened the terminal to do the same with the text editor as described, which I did, but I am unable to save it because it's a read only file.
The solution should be post [#29 ]("http://ubuntuforums.org/showthread.php?t=2217829&page=3&p=13035996#post13035996")

---

### Post by debroos on 2014-10-12
Thanks again Hanuka.  I prefixed the gedit code with gksudo and here's an edited version of the result - 
 "The program 'gksu' is currently not installed. You can install it by typing:sudo apt-get install gksu" - which I did and the message came up -

"Reading package lists... Done 
Building dependency tree       
Reading state information... Done
E: Unable to locate package gksu"

This is very illustrative of one of the reasons I despair of Ubuntu.  Any suggestions would be appreciated. If it's impossible to fix then the OS will be removed and consigned to outer darkness. ;)

---

### Post by debroos on 2014-10-12
Further to the last post, updates have since arrived and have been installed and gksu became available.  Problem sorted.  Many thanks again:p

---

