---
title: "Grub Problems."
date: 2007-10-25
forum: General Help
---

### Post by Havek on 2007-10-25
I recently had to install windows xp, because vista does not support watching tv if you don't have ultimate.  Before i did this i had Windows Vista and linux installed using GRUB, everything worked fine.  Now since i installed Windows xp i had to reinstall GRUB but have come into some problems.  Linux boots up ok, and windows xp does, but my when i choose the windows vista option it says it can't be found.  Now i know its there cuase in XP i can get to all my files in Vista, just grub is pointing the the wrong section or something.  Whats the code to preform find out the (hd0,0) ?  If i know this i can change the menu.lst in GRUB.

---

### Post by Havek on 2007-10-25
All i need i think is the code to see (hd0,0) for example.

---

### Post by Havek on 2007-10-26
This is what i get when i type in fdisk -1
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17800   142974432+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           17801       18182     3068415    f  W95 Ext'd (LBA)
/dev/sda3           18183       19457    10241437+  fd  Linux raid autodetect
/dev/sda5           17801       18182     3068383+   7  HPFS/NTFS

```

So i can see that the partition Vista is on is sda1 so what do i do next to learn what (hd..) it is?  Any help would be nice i would like to be able to get on to my Vista.

---

### Post by Maestro23 on 2007-10-26
What's your menu.lst look like? Run the command and copy/paste here.

> cat /boot/grub/menu.lst (lower case L)

---

### Post by Havek on 2007-10-26
> **Maestro23 said:**
> What's your menu.lst look like? Run the command and copy/paste here.

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/md0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/md0 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Windows operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

(hd0,1) takes me no where telling me " Invalid device requested".

---

### Post by fjgaude on 2007-10-26
If I know anything, which is not much, the Vista drive should be (hd1,0) in menu.lst or else it is not on sdb1. You do have two drives, eh?

---

### Post by mikewhatever on 2007-10-26
> **fjgaude said:**
> If I know anything, which is not much, the Vista drive should be (hd1,0) in menu.lst or else it is not on sdb1. You do have two drives, eh?

Not according to his fdisk. There is not sdb.

Havek, do you know where is Vista installed? There are two NTFS partitions, sda1 and sda5. Is it possible that Vista is on the second one? When installing XP, have you created a separate partition for it?

---

### Post by Havek on 2007-10-26
> **fjgaude said:**
> If I know anything, which is not much, the Vista drive should be (hd1,0) in menu.lst or else it is not on sdb1. You do have two drives, eh?

Yea i know i have 2 drives, but they are in RAID 1.  But i did not see that sdb1 hmm maybe  i should change that to a. lets see what this will do.

---

### Post by Havek on 2007-10-26
> **mikewhatever said:**
> Not according to his fdisk. There is not sdb.

Havek, do you know where is Vista installed? There are two NTFS partitions, sda1 and sda5. Is it possible that Vista is on the second one? When installing XP, have you created a separate partition for it?

There are 2 drives and Vista is on both since its RAID 1.

---

### Post by Havek on 2007-10-26
Ok changing sdb1 to sda1 did not work, and changing it to (hd1,0) did now work either giving the  message that it did not  exist.  I am thinking about putting in my vista disk and trying to do a repair, see if it can just write over grub and then i can come in and fix the windows one to detect my linux.

---

### Post by caen1944 on 2007-10-26
Hi,

I have my windows on a raid system, and because of that grub always screws up the drive and partition numbering when it gets installed. Seems that the drives seem different from the installer than they do from grub itself.

In my case it is trivial to fix though:

I found some very helpful stuff on this site:
[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)

Best of all you can type find /vmlinuz from the grub prompt and it will tell you what device to boot from. Then you can edit the grub boot command in the grub system when you start up. 

Anyway it worked for me. 

Good luck

---

