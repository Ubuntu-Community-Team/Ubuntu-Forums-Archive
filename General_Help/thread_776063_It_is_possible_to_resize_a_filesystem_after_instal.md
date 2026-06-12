---
title: "It is possible to resize a filesystem after installation ?"
date: 2008-04-30
forum: General Help
---

### Post by ienabellamy on 2008-04-30
Hello, the situation is this:

i've installed a Hardy Heron AMD64 in my entirely hard disk.
I've make only a big partition (/) . + swap, naturally.

So, because, i wish to play windows games seriously, not with wine, my question is this:

it's possible resize the entire filesystem ext3 after an installation ? and if it's possible, if i install windows, the windows loader may boot my ubuntu ? 

i need a workaround !

thanks !

---

### Post by bodhi.zazen on 2008-04-30
Yes.

Boot a live CD, the Ubuntu desktop will do, and resize with gparted.

Documentation: [Gparted Documentation](http://gparted.sourceforge.net/documentation.php)
    Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

Keep in mind you need to install Windows into a primary partition.

---

### Post by picopir8 on 2008-04-30
You can use gparted to resize a partition.  However, it will do you no good as windows likes to take over when it installs.  You will spend a lot of time getting grub working again.

The easiest option, just wipe the hard drive and install windows.  Then install linux.  When installing linux, resize the windows partition and put linux on the remaining space.

---

### Post by ienabellamy on 2008-04-30
Thanks for the help !

but the solution for erase the hd and reinstall it's not possible...i'm too lazy for reinstall all. I coming from gutsy..this installation has 8-9 months.

So, resize is possible, but the problem is grub no ?

reinstall grub after windows installation, from live cd, is hard ?

---

### Post by bodhi.zazen on 2008-04-30
No it should be easy.

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

