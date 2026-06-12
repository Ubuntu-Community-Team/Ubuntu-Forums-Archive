---
title: "[SOLVED] help with grub entry"
date: 2008-05-21
forum: General Help
---

### Post by Raccoon1400 on 2008-05-21
I just installed hardy to an old box with 3 other linux OSs already on it. I opted out of bootloader installation, and don't know what the grub entry should be(using grub menu from other ubuntu install on this machine). Hardy is on hda6. kernel 2.6.24-16-generic.

---

### Post by Patb on 2008-05-22
> I opted out of bootloader installation
Raccoon, I think you are going to have to install grub, so that there are grub stage1 and stage2 files on your new installation's partition.  For specifics, see Catlett's post which also covers installing grub: "How to restore Grub from a live Ubuntu cd": [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) 

You can also start manually by typing in the relevant commands at the grub menu (see the on-screen help).  You would probably need commands something like:
```
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic
initrd /boot/initrd.img-2.6.24-16-generic
boot
```
But if there are no stage1 or stage2 files on the hda6 partition, this will not work.  

For reference, see also Herman's: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm).  It must be good, Herman's an Aussie.  

Cheers, Pat.

---

### Post by angry_johnnie on 2008-05-22
something like this, maybe?

```
title		Ubuntu, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e02ad13c-f7b1-43b6-956c-df27b5312f36 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault
```

I think you can change **root=UUID=e02ad13c-f7b1-43b6-956c-df27b5312f36** (in **kernel**) --that is **my** UUID thing, and yours would be different-- to (hd0,5), or maybe hda6.

Hope that helps. :-)

---

### Post by Raccoon1400 on 2008-05-22
The part that makes it complicated is the log string of numbers that tell it the root partition after the kernel path. Why isn't it something like root=hda6 like with non debian distros?

---

### Post by angry_johnnie on 2008-05-22
Enter this in a terminal, to determine the volume's UUID

```
sudo /sbin/vol_id -u /dev/hda6
```

and see if that does it. :-)

Edit:  I just changed that to hda :p sorry 'bout that...

---

### Post by danwood76 on 2008-05-22
You dont have to use the UUID.
Just use root=hda6 as you would normally.

---

### Post by didac on 2008-05-22
> Re: help with grub entry
You dont have to use the UUID.
Just use root=hda6 as you would normally.

In Ubuntu you'll have to put root=/dev/sda6

Notice it's sda, not hda.

---

### Post by danwood76 on 2008-05-22
sda or hda is dependant on whether the drive is scsi (sata) or pata.
sda for sata drives, hda for pata.
(This is still true isnt it?)

So it could still be hda.

---

### Post by cdtech on 2008-05-22
1st Hard Drive

Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hda1 ----(hd0,0)----- /dev/sda1-------(hd0,0)
/dev/hda2 ----(hd0,1)----- /dev/sda2-------(hd0,1)

So:
root (hd0,6)
kernel	/boot/vmlinuz-2.6.24-16-generic root=/dev/hda6

sudo fdisk -l: will tell you sda hda
blkid: will give you the block id (UUID)

> Hardy is on hda6. kernel 2.6.24-16-generic.
How did you find this out?

---

### Post by Raccoon1400 on 2008-05-22
```
title	Ubuntu Hardy Heron
root	(hd0, 5)
kernel 	/boot/vmlinuz-2.6.24-16-generic root=UUID=ab8037ec-2bf2-419c-8b51-725b4b5e44a2 ro quiet
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
```

No matter what I try, I get an error saying "unrecognized device string".
I replaced the uuid, I replaced it with /dev/hda6, /dev/sda6, it tried setting root to (hd0, 5) and (hd0, 6)
```

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1263    10145016   83  Linux
/dev/hda2            1397        2491     8795587+   5  Extended
/dev/hda3            1264        1396     1068322+  83  Linux
/dev/hda5            2388        2491      835348+  82  Linux swap / Solaris
/dev/hda6            1397        2387     7960144+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2354    18908473+  83  Linux
/dev/hdb2            4864        4998     1084387+  82  Linux swap / Solaris
/dev/hdb3            2355        4863    20153542+   5  Extended
/dev/hdb5            2355        4863    20153511   83  Linux

Partition table entries are not in disk order
duncan@duncan-desktop:~$ 

```

```
root@duncan-desktop:/home/duncan# mount -t ext3 /dev/hda6 /media/disk0
root@duncan-desktop:/home/duncan# cd /media/disk0/boot
root@duncan-desktop:/media/disk0/boot# dir
abi-2.6.24-16-generic             memtest86+.bin
config-2.6.24-16-generic          System.map-2.6.24-16-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak
root@duncan-desktop:/media/disk0/boot# 
```

---

### Post by Raccoon1400 on 2008-05-22
fixed it.
I used
(hd0, 5)
instead of
(hd0,5)
Thanks for the help.

---

