---
title: "Permission Problems"
date: 2005-10-18
forum: General Help
---

### Post by k_smolka on 2005-10-18
Hi guys a newbie to ubuntu

I have managed to mount 2 different drives one a fat32 partition on my hard drive and the other an external hard drive.

But i am having problem writing to the drives.

I have tried both chmod and chown but they do not work. I simply get an error saying i do not have permission.

Below is a copy of my fstab file, any help would be most appreciated

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda1        /mnt/usb        auto         defaults     0 0
/dev/hda6 	/mnt/sharedHD 	vfat 		defaults 0 0


thanks again

Karl

---

### Post by Emerzen on 2005-10-18
I think the line should look like this:

/dev/sda1 /mnt/usb/ -t vfat -o iocharset=utf8,umask=000

and

/dev/hda6 /mnt/sharedHD/ -t vfat -o iocharset=utf8,umask=000

remember that you can only write file up to 4GB to FAT32 partitions.  Also, these lines are adapted from this guide:

[www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by seldenthuis on 2005-10-18
> 
I think the line should look like this:

/dev/sda1 /mnt/usb/ -t vfat -o iocharset=utf8,umask=000


You dont have to change the filesystem to vfat, auto works just fine.

The important thing is to change 'defaults' to 'umask=000'. That will give everybody read and write permission to the partition:

/dev/sda1 /mnt/usb auto umask=000 0 0
/dev/hda6 /mnt/sharedHD vfat umask=000 0 0

---

### Post by Nech on 2005-10-18
I have a problem the permissions too

In my fstab:
/dev/hdb1       /media/d        vfat gid=100,umask=0007,fmask=0117,utf8 0      0
/dev/hda1       /media/c        ntfs auto,ro,exec,users,dmask=000,fmask=111,nls=utf8  0       0

In vfat I not have permission write
In ntfs I not have permission read

---

### Post by seldenthuis on 2005-10-18
> 
In my fstab:
/dev/hdb1 /media/d vfat gid=100,umask=0007,fmask=0117,utf8 0 0
/dev/hda1 /media/c ntfs auto,ro,exec,users,dmask=000,fmask=111,nls=utf8 0 0


I'm not really sure what you're trying to do with all the umask,dmask and fmask options, but if you simply want to enable read permissions for everyone on the ntfs-partition and read+write permissions on the vfat partition you just have to change those lines to:

/dev/hdb1 /media/d vfat umask=000,utf8 0 0
/dev/hda1 /media/c ntfs umask=0222,nls=utf8 0 0

---

### Post by Nech on 2005-10-19
Thank you very much.  Now it works well :)

---

