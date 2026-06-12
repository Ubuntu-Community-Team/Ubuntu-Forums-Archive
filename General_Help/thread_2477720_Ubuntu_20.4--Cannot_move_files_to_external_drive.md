---
title: "Ubuntu 20.4--Cannot move files to external drive"
date: 2022-08-04
forum: General Help
---

### Post by stbickerton on 2022-08-04
I am running Ubuntu 20.4.  I am trying to copy files to an external hard drive, but Ubunto will not allow me to do it.  I have tried an external hard drive, a flash drive, and an SD card but all to no avail.  I hope someone on this forum can help.  Thank you.

---

### Post by Impavidus on 2022-08-04
So, what error message do you get? Permission denied? Mounted read-only? What filessytem is on the external drive? NTFS, exfat, fat32, ext4? Did you simply plug it in and wait for the filemanager popping up, showing it was mounted?

In most cases Linux gives a helpful error message. Helpful to experts, anyway.

---

### Post by ajgreeny on 2022-08-04
How is the external drive formatted?
If you formatted it using your current Ubuntu installation and as the Ubuntu default, it will be ext4 and will be owned by root meaning you can not write to it as user.

With the disk attached and mounted show us the output of ```
ls -la /media/$USER
``` which will show us the name of the mountpoint of the disk and who owns that mountpoint.
You can easily change ownership of that mountpoint if necessary once we know what it is and then you should be able to write to it easily.

---

### Post by stbickerton on 2022-08-05
I can't even format the flash drives!  As for the flash drives, they are formatted FAT32. When I try to drag any file (document, pdf, music, photo, etc), it will not copy onto the drive's folder, instead, it just slides back to its original place.  I tried to copy and paste, but when I go to paste the file on the drive it will not show the option.

---

### Post by stbickerton on 2022-08-05
> **ajgreeny said:**
> How is the external drive formatted?
If you formatted it using your current Ubuntu installation and as the Ubuntu default, it will be ext4 and will be owned by root meaning you can not write to it as user.

With the disk attached and mounted show us the output of ```
ls -la /media/$USER
``` which will show us the name of the mountpoint of the disk and who owns that mountpoint.
You can easily change ownership of that mountpoint if necessary once we know what it is and then you should be able to write to it easily.


It shows the following when I inputted that command in Terminal:

drwxr-x---+ 2 root root 4096 Aug 4 12:59
drwxr-xr-x  3 root root 4096 Jul 2  2020

---

### Post by ajgreeny on 2022-08-05
> **stbickerton said:**
> It shows the following when I inputted that command in Terminal:

drwxr-x---+ 2 root root 4096 Aug 4 12:59
drwxr-xr-x  3 root root 4096 Jul 2  2020
Was the usb disk attached when you ran that command?

---

### Post by TheFu on 2022-08-05
> **stbickerton said:**
> It shows the following when I inputted that command in Terminal:

drwxr-x---+ 2 root root 4096 Aug 4 12:59
drwxr-xr-x  3 root root 4096 Jul 2  2020

Unfortunately, this isn't sufficient for us to know much.  We need to see the parent directory permission and name/location.  It also appears that someone set some ACLs, so we need to see those.  The getfacl command can show those for 1 object.

But it appears that the storage is mounted by root with permissions for only root to do stuff on it.  That seldom is what you really want.
FAT32 is the last file system anyone should choose today.  Depending on the Ubuntu version, full support for it might not be included.  Non-native Linux file systems do not support the chmod or chown commands, so we have to trick the OS into allowing a user to have access.  This is controlled by mount options where we specify the userid who will be the owner.

With a little more information, we can show you how to make this stuff happen automatically with all the speed possible. Really, it should work automatically, just slowly, for most situations.  There's a system called gvfs which is supposed to make the file manager intelligently mount external storage. Alas, it is crap and has always been crap to my knowledge. Other opinions exist, of course.

I'm willing to take some wild guesses with the information missing. Perhaps you'll risk it?
1. "eject" the storage.  Don't pull it out from the USB slot.
2. sudo mkdir /media/junk
3. sudo mount -t auto -o uid=$USER /dev/sdb1 /media/junk

# When you are done, run
4. sudo umount  /media/junk 

I've made 2 assumptions.  
a) that you want to mount the partition/file system to  /media/junk.  Change as you like.
b) that  /dev/sdb1  is the device file which points at the fat32 file system.  This option can be replace with the UUID= or LABEL= instead and work.  I'd strongly encourage that a partition LABEL be used. **gparted** can be used to set the partition LABEL. There are other ways.  Setting the LABEL is a 1-time thing.  It is typically done when formatting the file system on storage.

Give those steps a shot.

If you want a better, nearly universal file system for flash storage, use exFAT.  the options I use with exFAT are:
-o dirsync,nodev,windows_names,nosuid,noatime,async,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002
You can look those up, if interested.

For Linux only microSD or USB flash storage (not SSD or HDD), the f2fs file system is even better. However, most other OSes don't support it.  OTOH, it supports normal Unix permissios and owners, so chown, chgrp and chmod all work.  The downside for FAT32, exFAT and f2fs is that they are not journaled, so corrupted files are much more common.  Journaled file systems cause many more writes, which is bad for flash storage lifetime.  NTFS, ext3/4, jfs, xfs, are all journaled file systems.  Always use a journaled file system on SSDs and HDDs.

---

### Post by mIk3_08 on 2022-08-06
> **stbickerton said:**
> I am running Ubuntu 20.4.  I am trying to  copy files to an external hard drive, but Ubunto will not allow me to do  it.  I have tried an external hard drive, a flash drive, and an SD card  but all to no avail.  I hope someone on this forum can help.  Thank  you.
Maybe you can just do the following command below:
```
mv '/home/username/Documents/Filename.jpeg' '/media/username/Medianame/DestinationFolder'
```
Regards and cheers

---

### Post by TheFu on 2022-08-06
> **mIk3_08 said:**
> Maybe you can just do the following command below:
```
mv '/home/username/Documents/Filename.jpeg' '/media/username/Medianame/DestinationFolder'
```
Regards and cheers

That won't work. The permissions don't allow it.

---

### Post by ajgreeny on 2022-08-06
If your USB disk was attached where was it mounted?

Obviously not in the normal place, ie,*** /media/username/USBname*** so perhaps it was not mounted anywhere.

---

### Post by Morbius1 on 2022-08-07
> **ajgreeny said:**
> If your USB disk was attached where was it mounted?

Obviously not in the normal place, ie,*** /media/username/USBname*** so perhaps it was not mounted anywhere.

Which might explain this:
> **stbickerton said:**
> I can't even format the flash drives!

---

### Post by ajgreeny on 2022-08-07
Yes, it might explain many things though not why you can not format it as a disk must be unmounted to be formatted, though it might explain this if the disk is mounted in an unexpected place, though why and where is another question that we need to try to answer.

So plug in the USB disk then run command ```
sudo blkid -c /dev/null
``` and copy the output back here using **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

You could also run command ```
mount
``` and again copy back here the output in code tags.

If we get no useful info from this I begin to wonder if your USB disk is dead as it appears not to behave as it should do.

---

