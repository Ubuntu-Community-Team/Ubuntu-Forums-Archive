---
title: "File systems"
date: 2008-04-28
forum: General Help
---

### Post by omrsafetyo on 2008-04-28
My wife got me a portable HD for xmas.  As soon as I plugged it in, I found it was NTFS, and had to reformat it to FAT32, so I could use it with Ubuntu at home.

At work I use Windows, and like to be able to access my files on my work laptop - not to mention, I just took a SQL Server 2005 certification course, and wanted to copy the virtual machine files to my HD so I could practice before taking the exam.

When trying to copy with of the HD image files, I kept running into "Not enough resources/disk space" errors.  I didn;t think too much of it at first, but it hit me today that FAT32 is limited to 4GB. 

What FS can I use on both windows and linux, and have unlimited filesizes?

I think I used gparted, and it didn't have a "format to vfat" option.  Will vfat work?

---

### Post by retrow on 2008-04-28
If you have a dual boot machine, you can log in to Windows and format it as NTFS. Ubuntu should be able to read/write NTFS file system.

---

### Post by bodhi.zazen on 2008-04-28
Ubuntu will use NTFS so that is your best bet. If you need read - write access from Ubuntu , use ntfs-3g.

---

### Post by omrsafetyo on 2008-04-29
So format to NTFS, and mount as ntfs-3g?

Thanks for the help!

---

### Post by bodhi.zazen on 2008-04-29
> **omrsafetyo said:**
> So format to NTFS, and mount as ntfs-3g?

Thanks for the help!

yes, do you know how to do that ?

mount -t ntfs-3g .....

or a fstab entry 

UUID=xxx.yyy.zzz /media/disk ntfs-3g ....

If you need help : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by omrsafetyo on 2008-04-29
Yes, I'll have to modify my fstab entry.  Currently it mounts it as FAT32 when I plug my USB drive in.  I should just have to install the driver (not sure if I have it), and then change the fstab.

Thanks for all your help.  I'll report my success when I get home.

EDIT:
What does the UUID portion do?  I don't have that in my current fstab entries that I have made myself.  I have one ntfs drive that is from a windows install that I use for media, and then I have this USB device... I have seen the UUID in the other entries, but don't know what it is.

---

### Post by bodhi.zazen on 2008-04-29
[http://liquidat.wordpress.com/2007/10/15/short-tip-get-uuid-of-hard-disks/](http://liquidat.wordpress.com/2007/10/15/short-tip-get-uuid-of-hard-disks/)

---

### Post by omrsafetyo on 2008-04-29
So what is wrong with this entry:
UUID=D052CDAD52CD991C   /media/Maxtor ntfs-3g   rw,noauto,users,gid=omrsafetyo,uid=omrsafetyo,umask=000         0       0

I'm getting a read-only filesystem, that isn't mounting at /media/Maxtor - its mounting at /media/usbdisk

---

