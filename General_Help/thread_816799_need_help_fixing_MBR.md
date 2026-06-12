---
title: "need help fixing MBR"
date: 2008-06-03
forum: General Help
---

### Post by BlackSwordD2 on 2008-06-03
set up the comp to dual boot XP and ubuntu

ubuntu runs great, but XP no longer runs

i have reason to believe that somewhere along the line XP's mbr got corrupted

i finally dug out my boot disk (or what i believe to be) and i was told to boot from the disk and use a string of commands to fix the mbr

my issue is that when i try to boot from the disk i get an endless loop of the bios screen "press any key to boot from disk" followed by "checking system hardware..." the back to the bios and so on

am i using the wrong disk? is it possible that i have the right one but scratched? (it looks a bit sketchy...) or maybe is there another way to repair my MBR?

---

### Post by PmDematagoda on 2008-06-03
Download the [SuperGRUB]("http://www.supergrubdisk.org/index.php?pid=5") ISO and burn it onto a CD and you can then boot the PC using it and recover GRUB which should allow you to boot Ubuntu again.

---

### Post by cariboo on 2008-06-03
We need a better description of the problem:

1: Is windows in the grub boot menu?
2: What is the output of sudo fdisk -l
3: what is the output of cat /boot/grub/devices.map
4: What is the output of cat /boot/grub/menu.lst

Questions 2,3,and 4 have to be entered in a terminal located in Applications-->Accessories-->terminal

note: for you windows guys a terminal is the same as cmd in windows.


Waiting for your reply

Jim

---

