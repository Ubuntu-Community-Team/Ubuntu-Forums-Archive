---
title: "Mounting Error"
date: 2007-10-11
forum: General Help
---

### Post by Ares203 on 2007-10-11
So I'm trying to mount one of the data harddrives that I have in my computer, but I'm having some troubles.  I'm using Ubuntu 7.04 (Fiesty).  The drive is formated in ntfs.

When I run  sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/hdd /media/data
in the terminal, I get the following error:

mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I think that it may be related to the fact the hdd does not show up in my fstab file.  But I know that hdd exists because if I go into the dev folder hdd is there.

I'm not sure if this indicates anything, but if I look in system log after running the previous command, this is there:  Oct 11 13:14:02 david-desktop kernel: [ 8173.248413] end_request: I/O error, dev hdd, sector 0

The output of fdisk -l is the following:
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6374    51197952    7  HPFS/NTFS
/dev/sda2            6375        9657    26370697+  83  Linux
/dev/sda3            9658        9964     2465977+   5  Extended
/dev/sda5            9658        9964     2465946   82  Linux swap / Solaris

All of these entries are from my one harddrive that has Vista on the NTFS partition and Fiesty on the ext3

I hope that is enough to diagnose something, but if there is more information needed then I'll try and provide it.  Thanks for any help you can give, cause I'm really starting to miss all my data on that drive.

---

### Post by dabl on 2007-10-11
Your mount command isn't quite right -- needs to be "mount point" then "device" -- you have those reversed.

However, if you will run the command ```
blkid
``` it will show you the UUID of the drive/partition in question, and then you can edit your /etc/fstab file and have it automatically mounted when you boot.  Here is what the fstab line needs to look like:

UUID=[COLOR="Magenta"]A8FC3435FC33FC5E[/COLOR] /media/data ntfs-3g user,atime,rw,nodev,nosuid 0 0

The actual UUID number would the one that you get from the blkid command.

Also you need to install the package ntfs-3g to be able to write to that NTFS-formatted partition.

```
sudo apt-get install ntfs-3g
```

Reboot your system after editing /etc/fstab and installing ntfs-3g, and you should have the drive mounted automatically.  :)

---

### Post by Ares203 on 2007-10-12
So I've partially solved the problem that I was having before, but now I've hit another brick wall.

I changed the hard-drive that I'm trying to mount to be secondary master (instead of secondary slave, which it was before).  But I'm still unable to mount it.

The drive does not appear in my fstab file, but it is in fdisk -l.  When I run the blkid command, the disk is not in there either, so I don't have the UUID.  Without the UUID, I don't know how I'm supposed to edit the fstab file. 

Is there any other way to find the UUID of the drive?

And I have installed the ntfs3g thing.

---

