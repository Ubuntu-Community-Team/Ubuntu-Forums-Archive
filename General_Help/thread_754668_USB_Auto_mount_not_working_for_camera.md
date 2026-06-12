---
title: "USB Auto mount not working for camera"
date: 2008-04-14
forum: General Help
---

### Post by over.tokyo on 2008-04-14
I have a cannon 400D camera which used to auto-mount a few updates earlier but then yesterday I noticed I am not able to auto mount my camera to copy images off it.  The only change would be the various system updates that were pushed to my laptop and i had installed. 
Before the updates. the camera used to show up as an volume nautilus. 
I am on kernel -  2.6.24-16-generic #1 SMP i686 GNU/Linux

The camera is being detected.  As can be seen here 
$ lsusb
Bus 007 Device 003: ID 04a9:3110 Canon, Inc. 
...

fdisk -l does not show the USB disk.  I am able to mount my MP3 player but not my camera. my mp3 player is auto-mounted fine. 

Also dmesg o/p tells me that it has detected the camera - 
....
[  219.936226] wlan0: RX WEP frame, decrypt failed
[  302.561207] usb 7-2: new high speed USB device using ehci_hcd and address 3
[  302.717801] usb 7-2: configuration #1 chosen from 1 choice
[  307.470298] wlan0: RX WEP frame, decrypt failed
....

These messages are  from the debug logs - 
Apr 13 22:48:37 dharsha-laptop NetworkManager: <debug> [1208152117.280374] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3110_noserial'). 
Apr 13 22:48:37 dharsha-laptop NetworkManager: <debug> [1208152117.362570] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3110_noserial_if0'). 

I am stuck at this point and have read the other forum messages around similar topics but haven't seen any that match my problem. 

Can someone help me diagnose this problem or suggest some solution ?? 

Thanks
Dhanvi

---

### Post by warp99 on 2008-04-14
You may have an old directory in your /media that was not removed cleanly and the camera could be using that. It would not auto-mount, but it would be waiting for you to click on the folder to mount it. The fix would be to remove the folder.

---

### Post by over.tokyo on 2008-04-14
Thanks for the reply. I thought it would be the same, but then I dont have any directory under /media related to my camera. The folders in /media are all already mounted volumes.  
Also on the other hand, if that were the case where an unclean unmount could causing this, wouldn't a restart fix that ? 

on another note - my fstab doesnt have any entry for usb volumes.

---

### Post by over.tokyo on 2008-04-14
Can someone help me in tacking this issue ? I really would love to continue to use ubuntu foir all my needs instead of booting into windows for something as simple as this.

Thanks for all your help.. :)

---

### Post by warp99 on 2008-04-14
> **over.tokyo said:**
> 
Also on the other hand, if that were the case where an unclean unmount could causing this, wouldn't a restart fix that ? 

If the permissions on the mount directory were incorrect from the udev mount point being set manually or the camera was mounted by a different user or an improper shutdown then the system would not remove the mount point in the future.

Can you manually mount the camera since the system does see the camera as connected?

---

### Post by over.tokyo on 2008-04-14
How do I manually mount the camera? 
I tried to see which block device it is being read as by running $fdisk -l but the output of fdisk doesnt show my camera memory as a volume.  Any other way I can mount my camera ?

---

### Post by warp99 on 2008-04-14
As long as the camera is umc, which appears to be your camera, then you can manually mount the camera like any other device. Here's how you do this:

Plug the camera in then run the command 'dmesg |tail'. It should show the camera being issued a device name (sdd, sdb, sdc, etc., etc.), then you can create a mount point for the camera based on this information. Example:

I plug in my usb drive, type 'dmesg |tail' and I get the following output:
```
dmesg |tail
[ 3173.423724] sd 4:0:0:0: [sdd] Mode Sense: 03 00 00 00
[ 3173.423726] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[ 3173.424865] sd 4:0:0:0: [sdd] 8015502 512-byte hardware sectors (4104 MB)
[ 3173.425125] sd 4:0:0:0: [sdd] Write Protect is off
[ 3173.425128] sd 4:0:0:0: [sdd] Mode Sense: 03 00 00 00
[ 3173.425129] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[ 3173.425156]  sdd: sdd1
[ 3173.425628] sd 4:0:0:0: [sdd] Attached SCSI removable disk
[ 3173.425657] sd 4:0:0:0: Attached scsi generic sg4 type 0
[ 3197.874465] usb 5-8: USB disconnect, address 6

```
I noticed that the system choose the device as sdd and the partition as sdd1, so I make a directory for my drive:
```
sudo mkdir /media/my_device
```
you only have to do this once, then mount the device:
```
sudo mount /dev/sdd1 /media/my_device
```
then the device is mounted so you can transfer the files back and forth using the file manager. When finished issue the following command:
```
sudo umount /dev/sdd1
```
and the device will be un-mounted.

---

### Post by over.tokyo on 2008-04-14
Thanks wrap99 for your help.. I did try what you have suggested before. But the problem is my dmesg logs do not list any device where my camera is mounted. 

The only entries in my log for my camera are - 
[ 302.561207] usb 7-2: new high speed USB device using ehci_hcd and address 3
[ 302.717801] usb 7-2: configuration #1 chosen from 1 choice

the only way I have right now to download snaps from my camera to my computer is using gphoto2 and command line. 

I still cannot figure out why ubuntu would refuse to mount my camera. :(

---

### Post by warp99 on 2008-04-15
I would put in a bug report at [launchpad.net]("https://launchpad.net/") since the camera did work prior to an update, so it seems like a regressive bug. I've been seeing other posts with the same problem recently. Camera works, then an update and the camera stops working.

---

### Post by over.tokyo on 2008-04-15
Thanks for the help and patience guys. I will register a bug there :)

---

