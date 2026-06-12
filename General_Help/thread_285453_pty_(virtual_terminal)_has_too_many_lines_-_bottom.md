---
title: "pty (virtual terminal) has too many lines - bottom line off the screen"
date: 2006-10-26
forum: General Help
---

### Post by anewbie on 2006-10-26
I'm running dapper 6.06 (will switch to edgy soon - first time user). Anyways - I have a problem thatthe virtual terminal has too mnay lines (in case I'm using the wrong term - if you type ctr-alt-Fn to switch out of X and get a terminal). The terminal has too mnay lines so the bottom line is off the screen. I tried resize command which didn't do much - just set lines to 25 and columns to 80. I have a fairly common setup - ti4200/dell 2001fp lcd. 

I've never seen this problem before and alas I have no idea how this aspect of the system is configured. A pointer (or solution) would be very helpful.

---

### Post by anewbie on 2006-10-26
I think i found the answer in another post once i figured out what to search for - you need to set vga on boot line

---

### Post by anewbie on 2006-10-26
yep: in case someone else has the same problem - you need to edit /boot/grub/menu.lst and add vga=0 (the previous post had vga=795 but the mode have changed) to the boot line - example:

kernel     /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash vga=0

notice at end of line vga = 0

---

