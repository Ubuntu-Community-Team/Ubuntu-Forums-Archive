---
title: "GRUB Error 17"
date: 2007-12-24
forum: General Help
---

### Post by TangerineSkyy on 2007-12-24
I'm not a newb. I've used linux before

Command lines scare me, but I do have some background in using dos, and I know a little java

Problem: GRUB 1.5 Error 17

System: ASUS G2S-A4 laptop
2gb 667 ddr2 
160gig hitachi
Nvidia GF8600GT (mobile) 256mb
Intel centrino C2D 7500 2.20ghz
Origonally was booting vista

OK, so I made a live DVD and installed ubuntu onto 10gb that I freed up using the windows partition manager. 

I did NOT elect to use any swap space- partitioning confuses me and I figured since I had 2gb of RAM, I would not encounter any issues.

I'm using my live DVD right now.

I screwed around with my BIOS boot settings because I heard this worked for somebody. No dice.

I really dont know if super grub is going to help (and I've never burned an iso with linux). Would no swap space cause this problem?

What exactly is Error 17?

I know I'm going to have to use the command line from my live dvd... What do I do? 

Help is much appreciated.

---

### Post by zhouxing on 2007-12-24
boot with live cd, find /etc/grub/menu.lst, post it here for more information.

also the info with df -h and fdisk -l will help.

by the way, you MUST set up a swap (1GB or 2GB will do according your specs) when install ANY linux distro.

---

### Post by ~LoKe on 2007-12-24
Error 17, if I recall, is simply that it can't find your hard drive.  When grub is loading, press escape and you should be presented with a list of kernels/things to boot.  Use the arrow keys to move down the list to the kernel you're trying to boot (usually the first option), then press "e".  That should allow you to modify the line, look for something like (hd0,1) and try changing it to something like (hd1,0).  Keep messing around with it until it works.

---

