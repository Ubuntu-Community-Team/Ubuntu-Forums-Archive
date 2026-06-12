---
title: "Copying files from an unbootable WinXP drive"
date: 2007-02-17
forum: General Help
---

### Post by Theophylact on 2007-02-17
I have a new 250 GB USB external hard drive, and I need to copy files from a WinXP boot disk that won't boot. I can, however, boot into Ubuntu Live 5.1 from a CD-ROM.

I decided temporarily not to convert the external drive to NTFS. It's still FAT32; Ubuntu recognizes it, and can see the three files that are there. And Ubuntu recognizes (in disk manager) that there are two hard drives, a Maxtor 200 ( the WinXP boot drive) and a Seagate 250 (currently empty but formatted).

Now, how do I get them to display their contents? The only disks displayed on the desktop are the CD-ROM and the external "MyBook" hard drive. What I want to do, of course, is to copy my vital files from the Maxtor to both the Seagate and the external before I do a repair installation of WinXP.

It's true that the boot drive is NTFS, but Ubuntu should be able to read the files even if it can't write them, and I've left the external HDD in FAT32. I'm a Linux noob and I really could use a bit of help.

---

### Post by xopher on 2007-02-18
> **Theophylact said:**
> I have a new 250 GB USB external hard drive, and I need to copy files from a WinXP boot disk that won't boot. I can, however, boot into Ubuntu Live 5.1 from a CD-ROM.

I decided temporarily not to convert the external drive to NTFS. It's still FAT32; Ubuntu recognizes it, and can see the three files that are there. And Ubuntu recognizes (in disk manager) that there are two hard drives, a Maxtor 200 ( the WinXP boot drive) and a Seagate 250 (currently empty but formatted).

Now, how do I get them to display their contents? The only disks displayed on the desktop are the CD-ROM and the external "MyBook" hard drive. What I want to do, of course, is to copy my vital files from the Maxtor to both the Seagate and the external before I do a repair installation of WinXP.

It's true that the boot drive is NTFS, but Ubuntu should be able to read the files even if it can't write them, and I've left the external HDD in FAT32. I'm a Linux noob and I really could use a bit of help.

It's possible, and, not that hard to do either.

The filesystem should even be automagically detected.

So, first of all, do a ```
sudo fdisk -l
```

This show's you all the partitions available for use. You should be able to locate the NTFS one in the list. Now, let's say it was called /dev/hda2 (change this to the correct one..)

Create a folder to mount it to in /media: ```
sudo mkdir /media/hda2
```

Mount the partition into that folder: ```
sudo mount /dev/hda2 /media/hda2
```

Now the partition should even be visible on your Desktop, if not, you can still browse it in /media/hda2

Hope this helps.

---

### Post by steveandarchie on 2007-02-18
Hello,

I have a similar problem. I have installed edgy intending to dual boot with winXP but XP will not boot. That's no big problem as I'll eventually take it off but before that I need to burn some data from the XP partition. 

My other installation of Ubuntu mounts the windows partitions automatically  at start up but this one doesn't and a look at 'Computer' in 'Places' doesn't show the partition - only the CDROM and filesystem. Gnome Commander doesn't seem to see it either but a live boot with slax/kanotix/puppy all reveal the missing XP partition - the problem being (apart from Puppy) that I need the CD to burn the data.

I tried the above but no joy. Any ideas?

Many thanks

---

### Post by steveandarchie on 2007-02-18
Here's the fstab file

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=d72418b9-dfad-465a-9bbc-c36b46c6cf7b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=5b123f72-4a21-4649-823e-e63ac0f7674e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Which shows that only the ubuntu partitions are mounting. I am really spooked about changing this and I have no idea what UUID figures are - can anybody help?

Many thanks

---

### Post by Theophylact on 2007-02-18
> **xopher said:**
> It's possible, and, not that hard to do either.

The filesystem should even be automagically detected.

So, first of all, do a ```
sudo fdisk -l
```

This show's you all the partitions available for use. You should be able to locate the NTFS one in the list. Now, let's say it was called /dev/hda2 (change this to the correct one..)

Create a folder to mount it to in /media: ```
sudo mkdir /media/hda2
```

Mount the partition into that folder: ```
sudo mount /dev/hda2 /media/hda2
```

Now the partition should even be visible on your Desktop, if not, you can still browse it in /media/hda2

Hope this helps.I've gone and done that (after some confusion about how to mount an NTFS partition). What I now have is an error message telling me that I don't have the permissions necessary to view the contents of hda1.

What next?

---

