---
title: "Partitions missing in grub"
date: 2024-11-05
forum: General Help
---

### Post by guan24 on 2024-11-05
Hi! 

I'm running into an issue after creating a partition and installing windows 11 to turn my Ubuntu laptop into a dual boot. 
The windows installation boots just fine, however I'm running into a problem when trying to boot my original Ubuntu installation. 

Instead of booting I'm redirected to the grub terminal where i can see my hard drive, but the partitions are missing. When I try to list the hard drive contents, i get an "unknown filesystem" error. 

To try and fix this, I booted from a live usb. When running fsdisk -l, I've been able to verify that the partitions are in fact still there.

I've also tried running boot-repair, However, boot-repair also doesn't show the option to repair my system, only to create an info summary, so i couldn't use this tool to repair my system

another clue I've found is the following error message when probing my hard drive.

Error: The primary GPT table is corrupt, but the backup appears OK, so that will be used.

Thanks a lot in advance for any help or info on fixing my system and making it bootable again!


EDIT: SOLVED! 


Solved the issue by running gdisk:

gdisk /dev/nvme0n1 
r - to enter repair options
b - to restore the backup
w - to write the changes

---

