---
title: "moving windows partition"
date: 2006-12-08
forum: General Help
---

### Post by richardhp on 2006-12-08
I have read a little bit about this and I am well aware that it can go wrong, but I was wondering how to move a windows partition from one disk to another. 

I want to do this as I have a new hard disk drive that i want to put everything on. I have successfully put Edgy onto the first partition and want my existing windows partition which is on another disk to be put onto the same disk as edgy then have it set up to dual boot.

I started out by using some disk imaging software to make a backup of my existing windows partition, which is 13GB. I then "restored" it to my new 35GB partition which i think may be the cause of some of my problems since they are of two different sizes. 

When I boot into the new partition from GRUB using this from the Menu.lst entry:


title		Windows XP Image
root		(hd0,2)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


it comes up and says "Cannot boot, hal.dll corrupted" which i know is something to do with Hardware Abstraction Layer and I found some possible solutions to this ie formatting the harddisk and re-installing windows which I am reluctant to do as i have programs installed on the partition i want to keep but no longer have the disks for.

I also found that one of the problems may be to do with the Boot.Ini file which looks like this:


[boot loader]
timeout = 30
default = multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS = "Microsoft Windows XP Professional" /noexecute=optin /fastdetect


I don't really know much about the subject but I have done my best to put as much information here as I can, please ask for more if you think it will help.

---

