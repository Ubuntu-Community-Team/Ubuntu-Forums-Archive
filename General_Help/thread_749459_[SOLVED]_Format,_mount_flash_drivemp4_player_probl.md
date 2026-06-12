---
title: "[SOLVED] Format, mount flash drive/mp4 player problem"
date: 2008-04-08
forum: General Help
---

### Post by SPr on 2008-04-08
This concerns a 2GB flash drive mp4 player.

I wanted to reformat my mp4 player so I used gparted to delete the old partition and create a new primary FAT16 partition.

The problem:

If I reformat the player, unplug the USB cable, plug it back in, allow it to auto-mount and copy music to it, unmount it and turn it on the mp4 player doesn't recognise that there is any music on there. It gives the simple response "No Files!".

If I reformat the player, unplug the USB cable, turn it on and use the built-in microphone to record something it will save the recording and play it back. (The player has the capability to take memos). If I then plug it into the PC it wont mount. 
```

         :~$ sudo mount -t vfat /dev/sdb1 /media/mp/
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
dmesg|tail gives:
```

[ 2393.371390] sd 10:0:0:0: [sdb] 3986353 512-byte hardware sectors (2041 MB)
[ 2393.372018] sd 10:0:0:0: [sdb] Write Protect is off
[ 2393.372024] sd 10:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[ 2393.372027] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 2393.372032]  sdb: sdb1
[ 2393.431353] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[ 2393.431410] sd 10:0:0:0: Attached scsi generic sg0 type 0
[ 2412.188315] FAT: bogus logical sector size 767
[ 2412.188321] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 2854.946222] usb 5-3: USB disconnect, address 11

```
lsusb gives:
```

Bus 005 Device 014: ID 10d6:1101 Actions Semiconductor Co., Ltd 

```
(Edited out the blank lines).

I hope I've explained the problem well enough. I've searched but not found anything to fix this. Thanks in advance. (Please ask if more info is needed.)

---

### Post by ibutho on 2008-04-08
Try formatting your mp4 player as follows
```
sudo mkfs.vfat /dev/sda
```
Change /dev/sda to the device name of your mp4 player. You can get the device name by running dmesg after plugging in the device.

---

### Post by SPr on 2008-04-09
> **ibutho said:**
> Try formatting your mp4 player as follows
```
sudo mkfs.vfat /dev/sda
```
Change /dev/sda to the device name of your mp4 player. You can get the device name by running dmesg after plugging in the device.

Thanks for the reply.

I tried that and received this error "mkfs.vfat: Will not try to make filesystem on full-disk device '/dev/sda' (use -I if wanted)". I assume that it can see the memo recordings I made earlier.

sudo mkfs.vfat -I /dev/sda worked! :D Thank you for solving it for me.

TBH I had used mkfs.vfat to format it with no success but I was using different switches to try and force mkfs into doing what I wanted.

---

### Post by SPr on 2008-04-09
Dupe post. This forum is sloooooooooooooow

---

