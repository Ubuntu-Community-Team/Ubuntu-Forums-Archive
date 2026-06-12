---
title: "Hardy on new partition not bootable"
date: 2008-06-26
forum: General Help
---

### Post by blazini on 2008-06-26
Previously I installed Fiesty (upgraded to gutsy) on a 500gb hdd but did not make /home a seperate partition. Since I can't back up all those filesand move /home to a new partition for a clean hardy install, I shrunk the unpartitioned hdd to allow space for a Hardy partition. I installed hardy on this new partition, but grub does not see it.

the "sudo fdisk -l" command sees it but shows it as not bootable. What do I need to do in order to make it bootable?
```
$ sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x437f1efa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       14945    68846557+   f  W95 Ext'd (LBA)
/dev/sda5            6375        9561    25599546    b  W95 FAT32
/dev/sda6            9562       12748    25599546    b  W95 FAT32
/dev/sda7           12749       14945    17647371    b  W95 FAT32

Disk /dev/sdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd1c9c4bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000195e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        3022       60427   461113695   83  Linux
/dev/sdc2           60428       60801     3004155    5  Extended
/dev/sdc3               1        3021    24266151   83  Linux
/dev/sdc5           60428       60801     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order
jmoney@jmoney-desktop:~$ cat /boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/sda
jmoney@jmoney-desktop:~$ grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. 


```There are 3 hdds in this computer, sdc is the one with both fiesty and the new hardy partition. sdc3 is the partition with the hardy install and sdc1 is the old Gutsy install. I just need to know how to make sdc3 bootable and if necessary, sdc1 unbootable.

---

### Post by blazini on 2008-06-27
I've tried several things now. I added an entry for the hardy partition in fstab (of the gutsy partition that does boot) and added a boot flag for it. Now I can see it in grub, but when I choose it I gat an error something like "partition not found".

I guess the problem is that the grub that loads is off the Gutsy partition, how do I get the system to load the grub that's on the Hardy partition?. I'm guessing that's the way to do it. I don't really care whether the gutsy partition is bootable anymore or not. I just want to boot the hardy partition and use the /home directory from gutsy, since all my data is there and there's no reasonable way to move it.

---

### Post by casperlingus on 2008-06-27
In your case, run the following command to make it bootable:

```
sudo fdisk /dev/sdc
```

This will bring up an interactive shell, you can type 'm' for a list of commands.  Type 'p' first to list the partitions.  Then 'a' is used to toggle a partition bootable. It'll ask you for a partition number.  Count them down from the list you just printed.  Once you are done, type 'w' to write the changes.

As for the second part of the problem:

I've had a similar problem before with booting.  My suggestion is that when grub pops up and asks you where to boot, select the hardy option, but **don't** hit <enter>.  Instead, type 'e' for edit, and it will pop up with the boot string for editing (this is the string as it is in /boot/grub/menu.lst).  The first thing in the boot string should look something like:

```
root=(hd0,2)
```

This is saying to boot off the first harddrive, third partition (zero-indexed).  On multiple occasions I've had the problem that the installation did not read the HDD order correctly, so these get out of order.  I've found, when I have this problem, that /boot/grub/device.map does not necessarily list the correct device mapping (perhaps that's the problem?)

The moral of the story is to hit 'e' and change the boot string to "(hd1,2)".  Hit enter and then type 'b' for boot.  It will attempt to boot from that new boot string.  If that doesn't work, try (hd2,2) or (hd0,2) or whatever you haven't tried.   The last number should already be correct, as the partitions are not going to be out of order, just the HDD list.

If this works, the first thing you should do when it boots is edit /boot/grub/menu.lst and change all the (hd0,2) entries to (hd2,2) entries, or whatever it was that you changed.  Otherwise, you'll have to keep editing that boot string every time you boot.

I hope this works.  This procedure has fixed most of my booting related problems.

-Casper

---

### Post by plucky on 2008-06-27
> I added an entry for the hardy partition in fstab


Can you access the Hardy menu.lst file?

If so you can copy the entry to boot Hardy from that file into the Gutsy menu.lst file.What I don't understand is why the Grub wasn't rewritten to the MBR to boot Hardy?

Can you post the output of ```
sudo blkid
``` and ```
cat /boot/grub/menu.lst
```

Good Luck

---

### Post by blazini on 2008-06-28
casperlingus.....

I already set the boot flag as you mentioned in the first step. The second step is exactly what I needed to do. Thanks for the tip about the hdds being out of order, It took some playing around to get the correct hdd's. When I was edidting menu.lst I thought it was odd that  grub doesn't know exactly  how to assign the correct hdd. I'm sure there's a reason for that tho.

I just have to figure out how to get these other hdd's mounted now

Thanks

---

