---
title: "usbmgr removes core components, kernel, ubuntu-desktop, and more"
date: 2008-01-14
forum: General Help
---

### Post by acketon on 2008-01-14
ok, first of all, this was caused by my own stupid fault of not paying enough attention when using apt-get in the console. 

I was trying to work on getting my sister's new Sansa e250R working. It wasn't mounting properly, and so I searched here on the forums and found a suggestion to try usbmgr in this thread: 

[http://ubuntuforums.org/showthread.php?t=333466&highlight=usbmgr](http://ubuntuforums.org/showthread.php?t=333466&highlight=usbmgr)


Well, did a sudo apt-get install usbmgr and didn't read the console completely at first glance before hitting yes. Switched back to firefox to continue reading the forums and then noticed something was wrong when network manager disappeared...switch to the terminal window and see that  apt-get is removing dozens of core applications, including network-manager-gnome, ubuntu-minimal, ubuntu-desktop, every kernel version, kernel-image, amarok, various apps, both critical and non-critical. 


I killed the process, but was left with a system that would not connect to the net nor mount the ubuntu CD, so I had no way to reinstall the packages. Had to shutdown, and reinstall fresh from a CD. Now luckily I have been keeping my /home on a separate partition so I did not loose too much, mainly just a lot of time tweaking and configuring and installing various apps and hacks and so forth over the past year or two....*sigh* Like I said, it was my own fault for not watching closer.


However, for whatever reason usbmgr wants to remove all of those packages...is that proper? if so, maybe there could be some sort of more obvious warning when removing key packages that affect the operating system's ability to boot up. (at least in synaptic)



found a thread with someone else apparently having had a similar  problem: [http://ubuntuforums.org/showthread.php?t=586637&highlight=usbmgr](http://ubuntuforums.org/showthread.php?t=586637&highlight=usbmgr)


In any case, it gave me something to do yesterday :lolflag:

---

### Post by mccorkle on 2008-01-14
Not that it helps you Acketon, but I wanted to provide more information for anyone watching this thread.  usbmgr does the same thing on my server which is a fresh Ubuntu 7.10 server install.  I have pretty much everything on in /etc/apt/sources.list:

> 
username@servername:/var/lib/mysql$ cat /etc/apt/sources.list | egrep -v "^#" | egrep -v "^$"
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


And it looks like usbmgr is coming from my "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe" sources list.  For anyone's info, universe is "unsupported", but still should be QA'ed.  Sorry you got bit by a bad package.

---

