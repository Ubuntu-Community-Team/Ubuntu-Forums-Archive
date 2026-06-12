---
title: "[SOLVED] Warning : Unrecognized partition table for drive 80."
date: 2008-05-15
forum: General Help
---

### Post by TechKing on 2008-05-15
The Wubi installer freezes on reboot. I get the following message:

Warning : Unrecognized partition table for drive 80. Please rebuild it using a Microsoft compatible FDISK tool(err=1). Current C/H/S=16383/256/63
Press 'Esc' to enter the menu...

Whatever option I choose from the short menu after pressing Esc doesn't work. I get the Ubuntu logo with the moving meter bar for 20 seconds and then it goes to some text message.

I have WinXP media center SP3 with 250G HDD. The boot partition is a 224G NTFS partition and the rest is in a small partition in FAT32 format. There are no partition encryption, only a password set for each Windows user.

Any idea what the problem is?

---

### Post by tinybit on 2008-05-15
> 
Warning : Unrecognized partition table for drive 80. Please rebuild it using a Microsoft compatible FDISK tool(err=1). Current C/H/S=16383/256/63


This is only a warning. Generally it is not a serious problem.

err=1 means the partition table has an entry which has an invalid boot indicator. A valid boot indicator should be either 0x80 for bootable or 0x00 for non-bootable. Other values are invalid.

---

### Post by ago on 2008-05-16
at the prompt run 

cat /casper.log

and look for mount errors

---

### Post by TechKing on 2008-05-16
I typed cat /casper.log and it reports over 20 times:

/init: /init: 1: cannot open /dev/scd0: No medium found

and the last line is:

Unable to find a medium containing a live file system

---

### Post by ago on 2008-05-16
grep err /casper.log
grep mount /casper.log

---

### Post by drifter2502 on 2008-05-16
I get same message on Vista. I ignore it and Wubi boots OK. Is it OK to ignore this warning? No problems so far.

---

### Post by ago on 2008-05-16
> **drifter2502 said:**
> I get same message on Vista. I ignore it and Wubi boots OK. Is it OK to ignore this warning? No problems so far.

Yes it is ok in most cases

---

### Post by TechKing on 2008-05-16
It writes 3 times:

/scripts/casper-premount/20iso_scan: /scripts/casper-premount/20iso_scan: 33: cannot open /dev/scd0: No medium found


Then 3 times:

/scripts/casper-premount/30custom_installation: /scripts/casper-premount/30custom_installation: 91: cannot open /dev/scd0: No medium found

---

### Post by ago on 2008-05-17
Do you use a raid array?

---

### Post by TechKing on 2008-05-17
Solved: I used "Partition Table Doctor 3.5" and it solved my problem by fixing something mysterious in the partition table which was not considered a problem by Windows XP. The software gives no details. Before the fix, the computer could boot and start the Ubuntu installer but some kind of low level check of the MBR or partition table prevented the installation from continuing.

---

### Post by Stefano Diem Benatti on 2008-05-29
I got the same error with wubi installed on a tri boot
XP, Vista and kubuntu.
Even thought it is just a warning and doesn't do anything,
is there a way to remove it? ( just make the warning disappear? )
The wait 10 seconds thing on every boot kind of annoys me

---

### Post by tinybit on 2008-05-29
> **Stefano Diem Benatti said:**
> 
Even thought it is just a warning and doesn't do anything,
is there a way to remove it? ( just make the warning disappear? )
The wait 10 seconds thing on every boot kind of annoys me

You may have a try to fix your partition table with Partition Table Doctor as mentioned by TechKing:

> **TechKing said:**
> Solved: I used "Partition Table Doctor 3.5" and it solved my problem by fixing something mysterious in the partition table which was not considered a problem by Windows XP. The software gives no details. Before the fix, the computer could boot and start the Ubuntu installer but some kind of low level check of the MBR or partition table prevented the installation from continuing.

---

### Post by kat_ams on 2010-12-21
Is there an open-source way of solving this problem? Partition Doctor is no longer marketed and the new free version of EASYUS Partition Recovery you need a BartPE disk in order to run it.
The program will not run from wine (already tried)

I answered my own question.
The package **testdisk** in the Universe repositories works exactly the same as Partition Doctor, but it's FOSS and in the Ubuntu Repositories...

---

