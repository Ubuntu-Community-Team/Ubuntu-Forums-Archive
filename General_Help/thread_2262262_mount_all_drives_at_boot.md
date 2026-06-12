---
title: "mount all drives at boot"
date: 2015-01-23
forum: General Help
---

### Post by keith14 on 2015-01-23
Hi,
 want mount 3 additional drives on boot-up. They are usually not needed but sometimes are. This can happen from boot. Is there any reasons not to do this?
I have 4 partitions on one sata drive.
Thanks,
keith

---

### Post by Bashing-om on 2015-01-23
keith14; Hi !

Your system, do it the way you want to ( but any time a file system is mounted there is that risk of corrupting the files).
Mounting is a function of the file " /etc/fstasb " .
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) <- bodhi.zazen -Understanding fstab
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[INDENT][INDENT]make it so
[/INDENT][/INDENT]

---

### Post by keith14 on 2015-02-06
hi,
 ok i've checked into two methods to generate an auto mount script which will
mount desired partitions in the current OS at start-up.


one method: add entries to /etc/fstab and run: mount -a


preference:
sudo mkdir /media/keith/Win7; sudo mount /dev/sda5 /media/keith/Win7


The specific names and status of all drives is simple perl hash of udisks --dump
(lsusb, fdisk -l, lsblk, and blkid were nice but lacked info that udisks gave.
blkid was nearly all there but lacked whether the partition was mounted or not).


works, but had to change color file; ntfs dirs color got messed-up.
Got this direction on line also, change two lines in color file:
dircolors --print-database > ~/.dircolors
change:
STICKY_OTHER_WRITABLE 30;42 # dir that is sticky and other-writable (+t,o+w)
STICKY_OTHER_WRITABLE 01;34 # dir that is sticky and other-writable (+t,o+w)


OTHER_WRITABLE 34;42 # dir that is other-writable (o+w) and not sticky
OTHER_WRITABLE 01;34 # dir that is other-writable (o+w) and not sticky
thanks,
Keith

---

### Post by Bashing-om on 2015-02-06
keith14; Hey,

NTFS :
[http://ubuntuforums.org/showthread.php?t=2139423&page=2&p=12625060#post12625060](http://ubuntuforums.org/showthread.php?t=2139423&page=2&p=12625060#post12625060)

Re: About mounting and drives NTFS -- Morbius1; No one says it better.

[INDENT][INDENT]hope it helps
[/INDENT][/INDENT]

---

