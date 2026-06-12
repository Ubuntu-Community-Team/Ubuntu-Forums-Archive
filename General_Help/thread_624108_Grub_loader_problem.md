---
title: "Grub loader problem"
date: 2007-11-26
forum: General Help
---

### Post by greaseyknight on 2007-11-26
I'm having this problem with my dell that has XP pro that I have installed Ubunto 7.10 
It has 2 hard drives the first is an 8 gig that has XP on it on 1 partition and a 200 gig that has about 5 of 6 partitions on is that is set up as a slave 
I Installed Ubunto on the 200 gig on one if it's partition every thing went fine until I rebooted and a got a 
grub error 21 
so what do I do
this is my first Linux dual boot?

---

### Post by PeterJS on 2007-11-26
Reboot with the live cd and find /boot/grub/menu.lst from your installed environment and post it here, and a description of what's supposed to be where on the disks. Error 21 is the error for disk not found, so it looks like grub isn't configured correctly to find the right hard drive.

---

### Post by greaseyknight on 2007-11-26
found the problem thanks for the help
The problem was that the second hard drive was turned off in the BIOS 
I changed it to AUTO and it works

thanks

---

### Post by ericartman on 2007-11-26
One to mark "Solved" huh? Thanks I'll put it in my Linux notebook never thought of this one.

Cart

---

