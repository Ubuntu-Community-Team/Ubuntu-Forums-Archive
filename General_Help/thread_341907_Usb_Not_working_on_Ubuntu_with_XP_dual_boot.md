---
title: "Usb Not working on Ubuntu with XP dual boot"
date: 2007-01-19
forum: General Help
---

### Post by redjim on 2007-01-19
I am using edgy on a hp media center computer.  I have a dual boot with windows XP (which I try to never use).  

Everything worked fabulous for months, then I started having problems with my usb wireless mouse, then the keyboard.  I can't use any usb devices now.  I thought it was a hardware issue, but I booted into XP and I can print to my USB printer.  SO I have something hosed on my ubuntu install.  

When I boot I can see something like:
Hardware devices           FAIL

I don't have any idea how to fix this.  I have searched the threads.

I would really appreciate any help.](*,) 
Thanks, James

---

### Post by kebes on 2007-01-19
First thing to do is gather some error messages. Try looking at the files in the directory "/var/log/" check "syslog", "kern.log", etc. You should run the command "dmesg" and see what it outputs. Look through it and see if there is any mention of USB devices.

The exact error message may provide a clue. Also, check if it's all ports or only some ports that are not working. Try moving your mouse to different ports... See if the USB mouse and keyboard actually work in Windows XP.

---

