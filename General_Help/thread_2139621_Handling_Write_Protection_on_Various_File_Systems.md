---
title: "Handling Write Protection on Various File Systems"
date: 2013-04-27
forum: General Help
---

### Post by Iggy64 on 2013-04-27
I need help with a general concept.

I have recently converted from Windows to Ubuntu (LXDE and e17 desktops).  From my Windows days, I have several USB hard drives filled with music, photos, document backups, etc.  All these are NTFS file systems.  I also have dozens of USB thumb drives with similar content.  These are all (I believe) FAT32 formatted.

Most of the content of those external drives is highly valued, and I learned years ago to set it all as write protected (under Windows), so that I did not accidentally delete or modify files.  For example, I once had a zealous piece of software add bogus information to the tags in over 3000 music files.  I don't want that to happen again.  So I keep everything write protected.  When I want to modify a file, I temporarily and deliberately unprotect it, make the change,then reprotect it.  Under Windows, I could unprotect an entire folder, make changes to all the files within it, then reprotect the entire folder.  Simple.  I could also right click the folder and easily see its attributes.

So, now that I am running Ubuntu, it is unclear how I turn write protecting on and off on my NTFS and FAT32 drives.  I am learning how Linux lets me assign permissions to various users on my local ext4 file system.  But I am unable to picture how I protect the files on my old legacy NTFS and FAT32 USB drives, or even how I can easily observe their attributes.

Perhaps there is a great tutorial somewhere on this.  I have searched, but have come up empty so far.

Any guidance will be much appreciated.

---

### Post by dino99 on 2013-04-27
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://stackoverflow.com/questions/12639134/change-the-permission-of-file-directories-on-ubuntu-12-04](http://stackoverflow.com/questions/12639134/change-the-permission-of-file-directories-on-ubuntu-12-04)

---

### Post by Morbius1 on 2013-04-27
There's 2 things in your case that are getting in the way or your desire to throw a switch and change an ntfs / fat32 partition from read only to read / write:

[1] There are no Linux ownership and permission bits in a windows fileystem so chown and chmod commands won't work on them.

Instead a "view" of those filesystems is created which gives them the appearance that they do but they are immutable. Once set to a specific owner and with specific permissions they persist throughout the filesystem and cannot be changed unless you change the parameters of the mount.

[2] External USB drives will mount these partitions automatically with a default specific set of ownership / permission attributes.

For example, an external Fat32 usb partition will automatically mount with:

Owner = you
Folder permissions = read/write/execute
File permissions = read / write

---

### Post by SeijiSensei on 2013-04-27
One way to do this would be to define mount points for each device in /etc/fstab following the instructions given in [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions). You can specify "ro" in the list of options which forces the mount to be read-only.

You could also mount a device read-only from the command line with the "mount" command.  Usually if you plug in a USB device, it gets assigned the next available drive letter in the /dev/sd[a-z] scheme.  If you have one harddrive in the computer, it will be referred to as /dev/sda.  If you plug in an external device, it should be assigned /dev/sdb.  Each of the partitions on the device are named separately like /dev/sda1 or /dev/sdb3.

Suppose your computer has one internal hard drive.  When you plug in the device, it will be assigned /dev/sdb.  Let's also assume it has just one partition, /dev/sdb1.  

These days most everything is mounted under /media, so lets create a "mount point" for the device (really just an empty directory) called /media/Music.

```
sudo mkdir /media/Music
```

Now if you want to mount the device you plugged in to that location with read-only restrictions, you can use the command:

```
sudo mount -o ro /dev/sdb1 /media/Music
```

[s]Another possible trick would be to remove write-permissions from the mount point with
```
sudo chmod a-w /media/Music
```[/s]
Update:  There's a better approach for this method in the documentation I linked to above:
> Option 1 - for mounting read-only access. For example, this would be suitable for mounting your Windows C:\ partition if you need to access it. Modify the line below with your UUID and mountpoint:

```
UUID=519CB82E5888AD0F  /media/Data  ntfs  defaults,umask=222  0 0
```

A "umask" is a set of three "octal" (base-8) digits that are used to generate the default permissions on files and directories.  The umask is subtracted from the number 777 which represents full permissions for user, group, and others.  That results in permissions of 555, which is read and list/execute for everyone and no write privileges.

This is an alternative to using "ro" in the list of options.  I don't think one is intrinsically better than the other.

---

### Post by Iggy64 on 2013-04-27
Thanks to all for your kind replies.  I see now that, when I mount the external NTFS disk, Ubuntu automatically makes all the files Read/Writable for me, but inaccessible to anyone else.  I assume, then, that if I open a music file in a tagging program, for example, I could - either intentionally or unintentionally - change the metadata tags in that file, even though I had write protected it under Windows XP.  This implies that the Linux/Ubuntu permissions are stored in a different place in the file than are the Windows permissions.  That is, permissions under Linux are stored separately from permissions under Windows.  So there are two separate sets of permissions attributes stored in the NTFS file.  And a given file might be writable under Linux, but not under Windows.  I wonder if I am picturing this correctly.

---

### Post by Iggy64 on 2013-04-28
OK.  It seems like Windows stores its "write" attribute in a 32-bit attributes word in each file.  Linux, on the other hand, stores file permissions in the inode table, rather than in the file.  The filename links to the file's inode, where the permissions are stored.

So, if I hook up an NTFS-formatted USB hard disk to my Linux box, all the Windows write-protect attributes will be ignored by Linux.  I would be at risk of accidentally modifying or deleting the files that I had write protected under Windows.  So I need to change permissions within Linux, to protect those files when accessing them under Linux.

Now I wonder this: When I first mount the NTFS USB drive, where are the inodes for its files stored?  Is there one single inodes table in Linux?  If so, then when I unmount the NTFS USB drive, are all its files' inodes deleted?  And, if so, do I have to re-apply permissions every time I remount the drive?

---

### Post by SeijiSensei on 2013-04-29
> **Iggy64 said:**
> So, if I hook up an NTFS-formatted USB hard disk to my Linux box, all the Windows write-protect attributes will be ignored by Linux.  I would be at risk of accidentally modifying or deleting the files that I had write protected under Windows.  So I need to change permissions within Linux, to protect those files when accessing them under Linux.

No, just mount the device read-only as I described above.

---

### Post by Iggy64 on 2013-04-29
Thank you, SeijiSensei.  I need to think in terms of write protecting the entire drive, rather than individual folders.  That would serve me well, and would be quick and easy.  Sorry that I didn't comprehend your meaning the first time around.  Thanks for sticking with me.

---

