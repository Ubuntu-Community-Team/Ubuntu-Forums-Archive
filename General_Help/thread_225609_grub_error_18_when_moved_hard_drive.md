---
title: "grub error 18 when moved hard drive"
date: 2006-07-30
forum: General Help
---

### Post by dccool879 on 2006-07-30
I put my hard drive in another computer because the power supply failed on the other, and during boot i get

GRUB loading stage 1.5
grub loading, please wait...
error 18

what gives? i need help asap because this is for a (semi) popular server with many hits every day thanks!!

---

### Post by dccool879 on 2006-07-30
OK, i looked through the grub manual, and i'm getting
18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

It is an old computer, and this is a 20 gig hd, but it used to be in this machine in the first place! however!! i think it may have been partitioned to be below 8 gigs. Now, it is not that way. Is there  a way to shrink the partition to less than 8 gigs without destroying the data? i just tried to change it from lba to normal and it does nothing [http://ubuntuforums.org/showthread.php?t=11764](http://ubuntuforums.org/showthread.php?t=11764)

i also have a 1 gig hd, could i write /boot to that?

---

