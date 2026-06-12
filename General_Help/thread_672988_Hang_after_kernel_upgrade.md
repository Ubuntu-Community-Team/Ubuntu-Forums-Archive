---
title: "Hang after kernel upgrade"
date: 2008-01-20
forum: General Help
---

### Post by bortolo on 2008-01-20
Hi all,
I've installed Xubuntu 7.10 on my home router (an old PIII 500mhz), and everything was fine, at least until yesterday.
I did a simple: apt-get upgrade, because it was something like a month that I didn't it.
The system was upgraded and a new kernel: 2.6.22-14 installed. After the first reboot the system hang after printing "Setting system clock".
With a recovery cd (that boots without any problem) I installed another kernel, the -i386 branch, but nothing changed, after many tests I made it work with the -server branch. Today, just to be sure, I rebooted my machine and guess what... Once again the system hangs! And this time I didn't do any upgrade, right now I'm quite stuck coz I really don't know what to do to make it run again... Do you have any advice for me?

Thanx a lot in advance!

---

### Post by Butthead on 2008-01-20
Hmm, hopefully you still have a copy of the old (working) kernel in your /boot directory.  Look in that directory and see if you have something like "config-2.6.15-29-amd64-generic" listed in there (using that just as an example).  I believe you can edit the Grub menu (/bootgrub/menu.lst) to re-load the old kernel (just leave off the "config" part of it).

While you are "editing" menu.lst, remove any references to the offending new kernel that was downloaded.

I assume you know how to go about editing text files as root? :confused:

---

