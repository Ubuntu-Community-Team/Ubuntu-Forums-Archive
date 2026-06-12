---
title: "Need help changing permissions for an external."
date: 2008-06-20
forum: General Help
---

### Post by jawinterton on 2008-06-20
I have an external HD that I copied data to from a Mac using dd_rescue.  It won't let me copy data the regular way now though.  It gives me an error telling me I don't have permission to do that. Can somebody please tell me how to get permission?  

I have tried to change the permissions by right clicking on the folders but it won't let me.  It just gives me an error telling me I shouldn't change the permissions.  

Sudo command from the command prompt doesn't seem to be of any help around the permissions either.  

I don't know what group 99 is all about.  When I go to Group Settings on my computer it doesn't have a group "99" listed.  

Any help would be much appreciated.

---

### Post by geirha on 2008-06-20
Try running nautilus as root, and see if it'll let you change ownership to your user and group. You can run nautilus as root by hitting Alt+F2 to get the run dialog, then run ```
gksu nautilus
``` and browse your way to those files.

In case that doesn't work, you'll need to provide some more info. On what kind of filesystem are the files you are trying to change ownership/permissions for?

---

### Post by jawinterton on 2008-06-20
Good idea, but when I did that I got this error when trying to change anything in the permissions window of the folders on the drive.

---

### Post by geirha on 2008-06-20
Could you run the following commands in a terminal, replacing **path** with the path to the directory you are trying to change ownership/permissions in:
```

sudo fdisk -l
sudo df **path**

```
It should show what filesystem we're talking about.

---

### Post by jawinterton on 2008-06-20
Okay, this is what it gave me:
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dbe0943

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         163     1309266   82  Linux swap / Solaris
/dev/sda2   *        1531        9729    65858467+   7  HPFS/NTFS
/dev/sda3             164        1530    10980427+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e43150e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488386552+  af  Unknown

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488386583+  ee  EFI GPT


Then, I ran the other command and it game me this:

> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            488386552 255699232 232687320  53% /media/Vault


---

### Post by jawinterton on 2008-06-20
BTW.... GParted shows it as an HFS+ partition.

---

### Post by robklg on 2008-06-20
Hi,

From the information you give...

The group 99 is obviously a group on your Mac. The ownership/group information has been preserved on your external drive -- Good thing!

However, this is not the problem.

The reason you get those errors is because the device is mounted read-only... as the error message says.

Please show us the output of the 'mount' command.

It will say /dev/sdb1 is mounted 'ro' (read-only).

You could try this:

sudo mount -oremount,rw /media/Vault

And try the 'mount' command again.

But I'm also curious what filesystem that is...

---

### Post by geirha on 2008-06-20
I have no experience with the HFS+, but according to google, it seems you need the package [hfsprogs](apt:hfsprogs) in order to mount it in read-write mode. Do you have that package installed?

---

### Post by jawinterton on 2008-06-20
I unmounted and tried to mount the device but there wasn't a folder.  After creating the folder in /media I mounted it successfully.  I didn't get a message that it was moutned 'ro'.  I ran the other command you gave me and it still gives me no messages afterwards.

HFS+ is a filesystem for Mac.

---

### Post by jawinterton on 2008-06-20
no, thank you!  :)   I'll try that.

---

### Post by jawinterton on 2008-06-20
> **geirha said:**
> I have no experience with the HFS+, but according to google, it seems you need the package [hfsprogs](apt:hfsprogs) in order to mount it in read-write mode. Do you have that package installed?

I have the package installed now, but I don't have any read-write support after trying to mount it.  

I ran fsck on it (since hfsprogs should enable me to do that) and I get this error:
> fsck 1.40.8 (13-Mar-2008)
** /dev/sdb1
   Invalid Volume Header
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
   Invalid node structure
(4, 32)
** Volume check failed.


Any idea??

---

### Post by geirha on 2008-06-20
Well, sounds like there's something wrong with the filesystem. Are you able to connect it to a Mac somehow? Apple's tools should be better suited to fix errors with Apple's filesystem.

---

### Post by jawinterton on 2008-06-20
Yes, unfortunately Apple's Disk Utility gives me the same information.   I really need to find some way to get the data to another drive to be read on the mac.  It's odd to me that the drive mounts and I can see some directories and files but can't access or copy anything.

---

### Post by geirha on 2008-06-20
You're not even able to copy it as root either (through "gksu nautilus")?

---

### Post by jawinterton on 2008-06-20
Nope, that's when I get permission errors.

---

### Post by jawinterton on 2008-06-20
Here at work I connected the drive up to our Mac G5 and I ran a data recovery scan with Data Rescue II (commercial software).   The quick scan came up with the files so I should be able to recover everything by running a thorough scan.  The sucky part is that I couldn't do this in Linux.  dd-rescue seems to be nice for making a quick duplicate of a disk having problems and near death, but not very good for making a duplicate to actually use (at least not for hfs+ partitions and w/o scanning with data recovery software afterwards).  Thanks for your help!

Still not a Linux hater though.  :)

---

