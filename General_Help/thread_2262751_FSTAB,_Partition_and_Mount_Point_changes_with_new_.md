---
title: "FSTAB, Partition and Mount Point changes with new SATA Controller Ubuntu 14.10"
date: 2015-01-27
forum: General Help
---

### Post by shag00 on 2015-01-27
I have a Gigabyte Z87X-UD5H motherboard with 2 built-in SATA controllers, I have 10 disks attached and all was well until I purchased a new 4 port SATA expansion card, a Syba FG-EST18A (no raid or BIOS).

In my FSTAB my drives are numbered SDB through SDJ  (see attachment), the boot drive uses UUID allocated by the system - giving 1 boot/system drive and 9 data drives = total 10 drives. All the data drives have 1 partition, being SDB1 through SDJ1. Format is ext4.

After installing the SATA expander card, which appears to be working fine, I am at a complete loss to understand what and how changes to the file system have occurred and more importantly how to proceed without losing the data on a number of drives.

I have made no changes to anything or installed/deleted any software other than physically mount the SATA card and connect 1 brand new disk (unformatted) and the outcome has me completely baffled and this is what has happened:

FSTAB
The new drive is named SDG - that comes about because the new controller is detected at boot before the 2nd built-in controller which I understand, what I do not understand is the follow-on changes: so all my drives have been moved forward 1 alphabet (the old SDG is now SDH) and the old SDJ is now SDK and the partition has likewise changed from SDJ1 to SDK1 even though there is no SDK1 in my FSTAB, however it is mounted and usable and in "Files" the correct partition is shown/used.

MOUNTPOINTS
In addition the mount points have been changed though I have added none and FSTAB has not changed. Now, running "lsblk" (see attachment) in the terminal shows that a new mount point has been created - /media/scott/disk91.

PARTITIONS
Gparted shows SDK1 (The old SDJ1) as having a label "Disk9" which I think is what is showing in "Files".

QUESTIONS
1/ How is a partition not listed in FSTAB being mounted?
2/ How are new mountpoints being created?
3/ If I partition the new disk (now SDG) with SDG1 is that data on the old SDG1 (now SDH1) destroyed or corrupted?

Thanks

---

### Post by TheFu on 2015-01-27
Didn't look at the images. 

Adding a new controller can change the order of the SATA devices. This is why using labels or UUIDs for mounting is better. 

Can't say anything about the interaction between different controllers, but that could be a problem - especially with lower-end vendors.

Modern Linux have gvfs, which is used for mounting dynamic volumes - normally flash drives or USB attached disks. It doesn't modify the fstab. It also puts them under /media on the current ubuntu, but previously put these dynamic mounts under /var.

---

### Post by shag00 on 2015-01-27
Thanks for your reply although it doesn't really help me, I said in my initial post that I understand why the order of SATA drives changes, that being at boot, the controllers are discovered by an (unknown to me) method and then each attached drive is discovered sequentially sata 0, sata1 etc.

Not sure why you mentioned gvfs, which I am not familiar with so I found this wiki definition:
[FONT=comic sans ms][SIZE=1]**GVFS** is the [virtual filesystem]("http://en.wikipedia.org/wiki/Virtual_filesystem") for the [GNOME desktop]("http://en.wikipedia.org/wiki/GNOME_desktop"), which allows users easy access to remote data via [SFTP]("http://en.wikipedia.org/wiki/SSH_file_transfer_protocol"), [FTP]("http://en.wikipedia.org/wiki/File_Transfer_Protocol"), [WebDAV]("http://en.wikipedia.org/wiki/WebDAV"), [SMB]("http://en.wikipedia.org/wiki/Server_Message_Block"), and local data via [Udev]("http://en.wikipedia.org/wiki/Udev") integration, [OBEX]("http://en.wikipedia.org/wiki/OBject_EXchange"), [MTP]("http://en.wikipedia.org/wiki/Media_Transfer_Protocol") and others.[SUP][[1]]("http://en.wikipedia.org/wiki/GVFS#cite_note-1")[/SUP][/SIZE][/FONT]

GVFS may be  modifying the /dev folder with the inclusion of the new device as SDG and adding SDH but is it also mounting the SDH1 partition and creating a new mount point?

I am still looking for answers to:
1/ How is a partition not listed in FSTAB being mounted?
2/ How are new mountpoints being created?
3/ If I partition the new disk (now SDG) with SDG1 is that data on the old SDG1 (now SDH1) destroyed or corrupted?

---

### Post by TheFu on 2015-01-27
If it isn't in the fstab, there are 2 ways that I know it could get mounted.
* gvfs
* automouter

That is why I mentioned gfvs. It is automatic. This is the most likely reason any partition is mounted, when not in the fstab.

Automounter using autofs is not automatic, until you modify a few config files. You would have set that up.

---

### Post by ajgreeny on 2015-01-27
> **shag00 said:**
> Thanks for your reply although it doesn't really help me, I said in my initial post that I understand why the order of SATA drives changes, that being at boot, the controllers are discovered by an (unknown to me) method and then each attached drive is discovered sequentially sata 0, sata1 etc.
Which is precisely why you should always use UUIDs or labels in fstab.

You cn discover all the UUIDs of all partitions with command ```
sudo blkid -c /dev/null
```and I suggest you do as TheFu said and edit fstab, replacing all those /dev/sdx# nomenclatures with the appropriate UUID; they will never change unless you specifically change them manually of format the partition.

---

### Post by bab1 on 2015-01-27
> **shag00 said:**
> ...

GVFS may be  modifying the /dev folder with the inclusion of the new device as SDG and adding SDH but is it also mounting the SDH1 partition and creating a new mount point?

My understanding is that the kernel enumerates (discovers) the devices and adds the the description to the /dev directory.  UDEV sets the rules for mounting the partitions of discovered devices.  A device always has a partition, even if it spans the entire device (i.e sda1 or sdb1).  File systems on partitions are what is mounted.  Not the device itself or the partition itself.
> 

I am still looking for answers to:
1/ How is a partition not listed in FSTAB being mounted?
Using udev rules via gvfs> 
2/ How are new mountpoints being created?
Dynamically via gvfs using udev rules> 
3/ If I partition the new disk (now SDG) with SDG1 is that data on the old SDG1 (now SDH1) destroyed or corrupted?
If you repartition any device your data is at risk.  Note that you do not rename device names.  Only the kernel does that.

---

### Post by shag00 on 2015-01-27
Thank you for replies gentlemen, now I know the reason for what is happening I can continue with confidence. Am attempting to mark this thread as answered.

---

