---
title: "from xfs to vfat"
date: 2007-04-08
forum: General Help
---

### Post by kanha on 2007-04-08
I want to change one of my partition to vfat which is currently xfs.(for sharing with windows)
how to do that? 
please help.I do not want to loose my data on that drive.

---

### Post by krussell on 2007-04-08
Hello :-)
No way to direct conversion. First you have to back up the data, then open console.
type fdisk /dev/hda (supposing your hard disk is primary master)
type "m" it'll show a list of command, see what command you have to use for changing the file system type (l or t ?)
then type "p" press enter > it'll show all the partitions in the disk
then type "l/t" > choose a partition number (the one you want to change) then select vfat code (b52) i think (sorry i am in front of a Windowz machine). then type "w" > it will make change to the disk. then quit fdisk with "q".
Now boot in windows, your partition that you changed the type (from xfs to vfat) will be visible in My Computer. Right click it and Format.

Again the commands (in console):
fdisk /dev/hda
  p
  l/t (please type 'm' for the correct command)
  w
  q

BE CAREFUL, if you're not sure what you're doing, please read some help files on fdisk, incorrect command inn fdisk may destro the partitions (and the data in it).

---

