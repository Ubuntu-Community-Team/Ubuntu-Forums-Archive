---
title: "Data recovery in a deleted encrypted lvm"
date: 2016-02-13
forum: General Help
---

### Post by Ufars on 2016-02-13
Hi,
I have searched a lot in the forum and on the internet without success.

I have just deleted my lvm partition on my ubuntu laptop.
I need to recover this partition because I have some file here. (I have one backup, but for some reason I can't use it).

The boot partition is save, no problem so probably in the grub file there are some information about the lvm?

I have some experience in data recovery. Is testdisk enough for recover this lvm?

Thanks for any help.

---

### Post by TheFu on 2016-02-13
Luke,  I think the backups are your only hope.

And welcome to the forums.

In another post in these forums recently (last 6 weeks), I posted the commands used to mount encrypted storage previously used on 1 machine to another thru a USB3 interface.  This was an encrypted partition, with LVM inside it and the partition table was intact.  That appears to be the main issue with this problem - you need to put the partition table back the way it was to have any hope.  Seems you may already know those commands, so don't know how useful it it.  'cryptsetup' is one part (*and a good search term*).

Was the partition metadata part of the backups?  If not, perhaps adding it would be good for future needs.  It just requires a **sudo parted -ml > partition.table.bak** cmd.  BTW, I need to do this here on all the systems too.  An ounce of prevention ... I store stuff like this in /root/backup along with daily updated from crontabs, installed pkg lists and lshw output. Adding the current partition tables is definitely something missing here especially since they are so small and easy to make just before every backup happens.

---

### Post by Herman on 2016-02-13
Would this link be any help to you?  -   [Rescue an encrypted LUKS LVM volume]("http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html") - Ubuntu geek

---

