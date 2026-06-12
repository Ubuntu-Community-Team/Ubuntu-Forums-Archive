---
title: "How to access a Windows C: drive with Ubuntu LiveCD?"
date: 2014-04-22
forum: General Help
---

### Post by Vannyi on 2014-04-22
I've booted up my Windows XP laptop using an Ubuntu 12.04 live CD.  When I click on the folder icon in the Unity bar, I can browse the file system, but I can't see the Windows NTFS formatted drive.  How would I access it so that I can copy some files over to it?

BTW, just as an aside, I know that XP is no longer supported, but my employer has an extended support contract with Microsoft for another year of support.

Thank you

---

### Post by papibe on 2014-04-22
Hi Vannyi.

It should be available on the same folder icon window you opened. The disk should be listed under 'Devices' on the left column of the window.

Hope it helps. Let us know how it goes.
Regads.

---

### Post by Vannyi on 2014-04-22
Hi Papibe

I don't actually see "devices" when I click on the folder icon.

What I see is:

Computer (not clickable title in bold)
Home
Desktop
Documents
Downloads
Music
Pictures
Video
File System
Trash

Network (not clickable title in bold)
Upload on desktop (name of the share on my desktop PC)

---

### Post by papibe on 2014-04-22
Press F9. That should open a side bar where 'Devices' should be.

If that doesn't work. Press F10 so you can get access to the menus. Then select
```
Go -> Computer
```
There you should see the list of hard drives and partitions available. 

Let us know if that helped.
Regards.

---

### Post by Vannyi on 2014-04-22
Thanks for your response.

If I press F9, the sidebar that I listed above is toggled on and off, but the contents of it does not change.  Devices is not listed.

If I press F10, and then select Go=>computer, I see File System, but I do not see devices.

---

### Post by papibe on 2014-04-23
That is intriguing.

Could you open a terminal run this command, and then post back the results (you can copy/paste the text)?
```
sudo fdisk -l
```
Regards.

---

### Post by Vannyi on 2014-04-23
Here are the results of the command

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f4b52ee


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   406218751   203108352    7  HPFS/NTFS/exFAT
/dev/sda2       406218752   625139711   109460480    7  HPFS/NTFS/exFAT
```

---

### Post by papibe on 2014-04-23
There are 2 partitions on the disk. I think this one is the OS:
> **Vannyi said:**
> /dev/sda1   *        2048   406218751   203108352    7  HPFS/NTFS/exFAT
You may try mounting it manually like this:
```
sudo mount -t ntfs /dev/sda1 /mnt
```
Now you should be able to see your Windows disk under the /mnt directory (under Filesystem).

Let us know if that worked or not.
Regards.

---

### Post by Vannyi on 2014-04-23
I tried the command that you provided but received the below error

NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by papibe on 2014-04-23
There's another partition /dev/sda2, try with that too.

/dev/sda is the disk, /dev/sda1 and /dev/sda2 are partitions. You can't mount a disk, you mount partitions instead.

Let us know how it goes with /dev/sda2

Regards.

---

### Post by Vannyi on 2014-04-23
I hope I did this right, here is the command I ran

sudo mount -t ntfs /dev/sda2 /mnt

and here is the error message I received

Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by papibe on 2014-04-24
Does your machine boot correctly on XP? It looks that the filesystem is corrupted.

Could you try this?
```
sudo mount dev/sda1 /mnt
```
Regards.

---

