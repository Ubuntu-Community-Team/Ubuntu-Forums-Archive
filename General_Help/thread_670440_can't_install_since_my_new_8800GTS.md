---
title: "can't install since my new 8800GTS???"
date: 2008-01-17
forum: General Help
---

### Post by sethfc on 2008-01-17
Hey guys,

So I upgraded from my 7800GT to an 8800GTS.

I tried performing the dpkg-reconfigure type command through the recovery mode (as i had 7.10 64 bit already installed on my computer).

I had no success fixing the xorg via the recovery mode, so i figured why not reinstall.

So, i put my 7.10 64bit disk in, I boot from the CD, I can see the main menu, and if I select
"install ubuntu in safe mode"
or the regular
"install ubuntu"
i get a black screen.  there's a connection, as my monitor doesnt go into power save mode, but no picture

monitor = Samsung SyncMaster 226BW

help :(

---

### Post by sethfc on 2008-01-17
I just tried clicking the "check for CD errors" type option on the CD boot up menu,

same thing.  screen black.

o_0

-seth

---

### Post by sethfc on 2008-01-17
I've tried hitting F6 on the CD's menu, and changing quiet splash to no splash.


did not work.

---

### Post by bodhi.zazen on 2008-01-17
You need the nvidia driver.

See this link :

[http://ubuntuforums.org/showpost.php?p=4148573&postcount=3](http://ubuntuforums.org/showpost.php?p=4148573&postcount=3)

---

### Post by Borbus on 2008-01-17
When you are at the menu, press F6 for options, remove "quiet" and "nosplash". Then choose the boot into safe graphics mode option. Your screen might still go black, but after a while it should load the live CD. I have the same problem with my 8800GT, except my monitor does go into power save mode.

---

