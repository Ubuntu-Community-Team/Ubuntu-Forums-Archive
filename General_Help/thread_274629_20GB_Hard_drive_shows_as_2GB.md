---
title: "20GB Hard drive shows as 2GB"
date: 2006-10-10
forum: General Help
---

### Post by david.holland on 2006-10-10
When I try to partition a 2nd hdd (hdb) it only shows as 2GB.  However when formatted to FAT32 in winXP it is definitely a 20GB hdd.  I have checked the heads, cylinder and track info in the bios and is looks like this:
9579/255/63 which gives 20010MB

But when I view this info in fdisk as su it shows only as:
4096/16/63 which gives 2111MB
I have tried to change this to 9579/255/63 and write the info to the drive but it does not 'stick' and reverts back to 4096/16/63 immediately after and also after a reboot too.

I try to format the harddrive and create partitions but Ubuntu 6.06LTS only shows the hdd (hdb) as 2111MB in size. 
I have replicated this on Mandriva 2006 too!

My system looks like this:
AMD- Duron(909Mhz) / 384MB RAM / 
1 x hda (hda1=~9.5GB (winXP) / hda2=~30GB (Mandriva2006) / swap=~500MB
1 x hdb (20GB hdd only showing as 2GB?? tying to install Ubuntu on this one)

---

### Post by ajgreeny on 2006-10-10
Have you tried the system with gparted, available on the ubuntu live CD I think, or even better as it's own live, bootable CD.  This should letyou see if there really is 20 GB free on the disk, or if something else is blocking it for some reason, though I can't imagine what.

Also have a look in Windows.  Right click on "My computer", go to "Manage", "Disk management" and see what partitions are shown there.  If there are some strange ones showing on the disk and you want the whole disk for ubuntu, you can just delete them in that window and try installing ubuntu again.

---

### Post by david.holland on 2006-10-10
thanks for ur reply ajgreeny, what I need to point out though is that the harddrive is not partitioned.  When viewed in gParted is shows as a *device * [not a partition] with 2111MB in size with no allocated partitions on this.  If I try to partition the device with gParted it only lets me manipulate 2111MB (this total size it detects).

Hmm??

---

### Post by cd-r80 on 2006-10-10
Deleting partitions with Linux fdisk helped me once. Then I created Partitions again with DiskDrake (Old Mandrake CD). With Gparted I have got problems.

---

### Post by Kateikyoushi on 2006-10-10
Is the drive correctly configured in bios ?

---

### Post by david.holland on 2006-10-10
In the bios, I have let the bios auto detect the drive details and also user defined the drive details too.  How do I correctly configur the drive in the bios?

---

