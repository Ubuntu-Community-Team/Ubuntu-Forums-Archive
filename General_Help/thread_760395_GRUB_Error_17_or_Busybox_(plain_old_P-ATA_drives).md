---
title: "GRUB Error 17 or Busybox (plain old P-ATA drives)"
date: 2008-04-20
forum: General Help
---

### Post by abalone on 2008-04-20
Just swapped out one drive for another and installed Ubuntu 7.10 on it (going back from 64 bit to 32 in the process). 

Everything's partitioned more or less as before:

hda: Primary Master, 80 GB Exelstor with Windows XP

hda1: Windows (NTFS)
hda2: Windows PProgram Files (NTFS)
hda5, or was it 6: file storage (FAT32)

hdb: Primary Slave, 400 GB Samsung with Ubuntu 7.10

hdb1: swap
hdb2: / (ext3) 
hdb3: file storage (NTFS)
hdb4: /home (ext3) 

The GRUB menu comes up, and I can boot Windows (I can even boot my old Ubuntu, except it doesn't work as it's now on another controller entirely - currently disabled so as to not interfere)** - but picking the first Ubuntu entry gives me Error 17 (can't mount selected partition). **

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=E2CC26F6CC26C49F ro quiet 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet



When I changed root (hd0,0) to root (hd1,1), I got a little farther - but:

Starting up...
Loading, please wait
kinit: name_to_dev_t(/dev/disk/by-uuid/ca5601f6-c887-42c5-a141-98616f536a10) = hdb1(3,65)
kinit: trying to resume from /dev/disk/by-uuid/ca5601f6-c887-42c5-a141-98616f536a10
No resume image found, doing normal boot...
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

I then get a "Busybox" shell that I don't know what to do with. 



I also on a whim changed that whole root=UUID=... string to root=UUID=/dev/hdb1:

Starting up...
Loading, please wait
kinit: name_to_dev_t(/dev/disk/by-uuid/ca5601f6-c887-42c5-a141-98616f536a10) = hdb1(3,65)
kinit: trying to resume from /dev/disk/by-uuid/ca5601f6-c887-42c5-a141-98616f536a10
No resume image found, doing normal boot...
**mount: Mounting /dev/hdb1 on /root failed: No such file or directory**
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

(Same as above, except for the additional line in boldface)



/boot/grub/device.map looks ok:

(hd0)	/dev/hda
(hd1)	/dev/hdb <-- new drive, looks correct to me, also detected in BIOS w/ everything AUTO
(hd2)	/dev/sda <-- the old, swapped-out Ubuntu drive on some Promise thing in IDE mode... now disabled in BIOS setup

I can poke around that new installed Ubuntu with the live CD, the drive seems ok so far. 

I'm a little confused as this isn't some weird new configuration - just the same old dual-booting-with-two-HDs I had been running for many years without ever digging into GRUB internals... 

*begs for help*



PS: One thing I noticed is that the UUIDs mentioned in menu.lst (E2CC26F6CC26C49F), in the "kinit: ..." lines I quoted (ca5601f6-c887-42c5-a141-98616f536a10), and (I think) in Nautilus' properties dialogue for the drive do not match up. I don't know if they have to, though, or if they even refer to the same things.

---

### Post by banewman on 2008-04-20
UUID's are how the system works out what to do on boot and mounting of different partitions.
When you changed hard drives you needed to change the UUID for root file system in fstab and menu.lst.

---

### Post by abalone on 2008-04-20
It was a fresh installation from the LIve CD to a blank HD... 

But I've changed the fstab entries to human-readable /dev/hda1 (etc.), and the root= options in menu.lst to what seemed to be the correct UUID. 

Still a kernel installation through synaptic adds the same old faulty entries, causing GRUB to attempt to boot Ubuntu from the Windows partition. 

There seems to be something else to fix somewhere...

---

