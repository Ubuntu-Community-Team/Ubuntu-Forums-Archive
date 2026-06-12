---
title: "Can't change permissions on internal drive with automount or manual mount"
date: 2007-11-06
forum: General Help
---

### Post by illiterate_light on 2007-11-06
I have a fresh install of 7.10 and for some reason can't change permissions on anything on a secondary internal drive, on a fat32 partition.  Had no problems with this on 7.04.

Tried:

sudo mount -t vfat /dev/hdb5 /mount_location -o uid=1000,gid=100,umask=007

Also tried auto-mounting with this line in fstab:

/dev/hdb5       /mount_location    vfat    uid=1000,gid=100,umask=007 0 2

It mounts fine and I can read/execute from the drive, and I can also write to the drive, but I can't modify permissions, as root.  Can't change the owner or group of anything on the entire drive -- I get the error "You do not have the permissions necessary to change [owner or group]."

I've also noticed that the system seems to hang for a bit while trying to access this partition, if that sheds any light.  I have another ext3 partition on the same drive, and have no problems with it.

Anyone have any clues?  Any help is appreciated.

---

### Post by ohzopants on 2007-11-06
Found this:

In terms of the way rwx permissions work with FAT32 mounts:

The default permissions for a mounted FAT32 volume are rwx for root, but only rx for normal users.

In Linux, permission control works differently for FAT32 and NTFS filesystems than it does for native Linux filesystems (ext2, ext3, reiser, etc.):

1. The UNIX permissions of a directory onto which you mount a Windows filesystem can't be changed while the fileystem is mounted. Unmount the Windows partition; you should then be able to chmod the permissions of /mnt/Windows. You will need to set the appropriate Linux rwx permissions on the /mnt/fat folder and set the permissions for the FAT partition (as described below) in order to grant everyone write access.

2. Windows doesn't support UNIX-style permissions, and you can only apply permissions to the entire filesystem, not to individual Windows files/folders. This is done with the "umask" option of the mount command. In /etc/fstab, change the mount entry for your Windows partition to this:

/dev/hda6 /mnt/fat vfat users,defaults,umask=000 0 0

(the "users" option allows anyone to mount/unmount the drive and overrides the default , which is that only root is allowed to mount/unmount.)

- When issuing the mount command manually, the syntax is:

mount -t vfat -o umask=000 /dev/hda6 /mnt/fat


The value of the permission bits used with umask are the opposite of those used with the chmod command. For example, the following pairs are equivalent:

umask=000 and chmod 777
umask=022 and chmod 755

taken from: [http://www.daniweb.com/forums/thread22358.html](http://www.daniweb.com/forums/thread22358.html)

---

### Post by illiterate_light on 2007-11-07
Thanks for the detailed reply.  Unfortunately, I still can't change permissions.  Tried unmounting, then changing permissions on the mount directory while the drive was unmounted, and then manually mounting with your command, and I still get the same error when I try to change permissions of anything on the mounted drive.  I'm starting to wonder if it's a problem with the drive (or partition) itself, given that it now takes about 20 seconds to display the contents of the drive in nautilus, once it's mounted.

---

### Post by ohzopants on 2007-11-07
That's really weird.  Sorry, but I have no more ideas.

Who do the files belong to now?  Does this partition have to be fat32?

Good luck.

---

