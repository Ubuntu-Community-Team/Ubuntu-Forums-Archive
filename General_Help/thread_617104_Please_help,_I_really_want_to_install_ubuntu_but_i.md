---
title: "Please help, I really want to install ubuntu but it doestn work"
date: 2007-11-19
forum: General Help
---

### Post by ale2283 on 2007-11-19
hi Im a new user i need some help, im tried to install ubunto with WUBI but after i reboot and choose ubuntu a black screen appears with this message and a command:

bustbox v 1.1.3 (debian1:1.1.3.5ubuntu7) built in shell (ash)

(initramfs) _

What does this means, and why doesnt start ubuntu?

---

### Post by ago on 2007-11-19
Type 
cat /casper.log

and post here any error message

---

### Post by ale2283 on 2007-11-19
ok thanks for your help
I get this error message 

Failed to mount '?dev?sda1 input/output error
NTFS is either inconsistent or you have hardware faults or have a soft raid/fakeraid hardware

then it tells me that i have to use DMRAID, i tried to use this program before with ubuntu live cd but it doesnt work

---

### Post by ago on 2007-11-19
Install on a regular partition (not on raid) and make sure it is scanned with chkdsk first

---

### Post by ale2283 on 2007-11-19
ok thanks, but how do i make a partition that is not on a raid array?
I made a 70 Gb ntfs partition with partition magic and the same thing happens

---

