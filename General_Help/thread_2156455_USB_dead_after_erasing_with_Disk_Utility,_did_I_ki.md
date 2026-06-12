---
title: "USB dead after erasing with Disk Utility, did I kill it for good?"
date: 2013-06-21
forum: General Help
---

### Post by goodbye-windows(tm) on 2013-06-21
I tried to install 13.04 on a 64 GB usb stick. It had been working previously. But, during the install process it said it couldn't create any partitions. Tried a bunch of stuff, including reformatting and partitioning with Gparted-installs still failed.

I opened the disk utility program, and selected 'erase' with the record all data as zeros. After that, the punchbox didn't even recognize the drive when it was hot plugged. Disk Utility program can see it, but it just says 'USB Drive', without any info like size or any other data. 

Did I kill this thing for good, or is there anything I can do to restore it to proper operation????

TIA

Art

---

### Post by Bashing-om on 2013-06-21
[COLOR=#000000]goodbye-windows(tm); Howdy do;
[/COLOR]
As you "zeroed" out the drive, there is no partition table for a file system to exist on, nothing to find.
Write you a new partition table and format the device:
Try this tutorial...specific to hard drives, but applicable to usb devices as well.
I suggest the "command line partitioning" -> fdisk ->mkfs
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)[INDENT=2]
hope this works great and last long time

[/INDENT]

---

### Post by goodbye-windows(tm) on 2013-06-22
Thanks so much Bashing,

I went through the whole process and think I got everything correct. 

I learned a big bunch from the experience. I never did have to create a mounting point however, so not sure if I'm totally out of the woods. 

I wasn't sure about the format needed for a Linux only usb stick, so I formatted it to ext2.

I ended up using e2label to add a more descriptive label too.

I found the ownership of the unit was changed to 'root', so the chown command got me access to the drive.

SO, I can read/write to it, and it is now recognized by the computer when plugged in.

I'm a little worried about the creating a mounting point, but since the article was about hard drives, I assume that I don't have to specify a mounting point for the portable usb drive.

Again, thanks so much for the nudge in the right direction.

Art
-------------------

---

### Post by Bashing-om on 2013-06-22
[COLOR=#000000]goodbye-windows(tm); Hey...
We are all in this together, glad to be of some assistance.

Mount point: No need to make one for  removable media for general mounting purposes ... though one may. The  gvfs system takes care of it in an "auto mount" situation. However, the system has no way to know when you are done with the device and are ready to close it out for removal. You MUST inform the system ...thus the "umount" command; which will flush all operations from cache and finish up and close out all open files.

File system format: For general use in ubuntu only ...use ext4. Much more robust and lots of enhancements over ext2. ext2 does have some advantages in "special" circumstances ...now-a-days it is seldom required. 

See:
```
man mount
```very informative, take it in with small steps.[INDENT=2]
it is all a learning experience[/INDENT]

[/COLOR]

---

### Post by gordintoronto on 2013-06-22
Are you truly trying to install to the flash drive, not just create a "liveusb?" ext2 is good for a true installation, but fat32 is appropriate for a liveusb.

---

### Post by goodbye-windows(tm) on 2013-06-23
Hi Gordon,

When I first started the thread, I needed to know how to make the drive functional. Now that the drive works, I will ultimately use it to byte for byte copy using the dd command in order to clone a 32 GB SSD that has deleted files that MUST be recovered. So, it should be bootable with a complete copy of the ssd, but I will never boot from it.

Once I get my files recovered, the usb flash drive will go back to general use.

Regards,

Art

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]goodbye-windows(tm); Hey ,

Pleased that you are making progress.........
Recovering files: Have you looked into the utility "testdisk" ??
[/COLOR][INDENT=3][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

