---
title: "Question with accessing other partition of Hard Drive"
date: 2007-01-28
forum: General Help
---

### Post by Mr. DVD on 2007-01-28
I have three major partitions on my hard drive and I can access two of them while using Ubuntu. How can I access the third? It doesn't appear while I'm using Ubuntu. Also, is it possible to uninstall Ubuntu? Last time I tried that I had to go through this long process that just eventually led to reinstalling it.

---

### Post by Goober on 2007-01-28
What format is the 3rd partition in?  If it is NTFS (Windows), then you will likely need to manually mount it.  If it is ext3 (Linux native), then it should automount, depending on your settings.

If you need a good simple partitioning program, try gparted.  It should be available through the Add/Remove programs.

You could always reformat your Linux Hard drive to get rid of Linux.  I am not sure how you otherwise uninstall an Operating System.  They aren't really meant to uninstall ...

---

### Post by taurus on 2007-01-28
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Mr. DVD on 2007-01-28
Hmm, that link doesn't quite work. Is it possible for me to just change the format of the NTFS drive to ext3 and allow it to be read on Linux? Would it still be accessible by Windows?

---

### Post by taurus on 2007-01-28
If you don't have anything on that drive, you can format it to ext3 and Windows can read and write to it with [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by Goober on 2007-01-28
No, you can't change the format of the NTFS drive.  The only way is to reformat the drive, which will DELETE all of the info on that, and format ir to ext3.  

What you want to do is to mount the drive onto Linux, where you can access it.  fdisk -l in a Terminal will tell you if Linux recognizes the partition.  You can try and mount it directly, 

sudo mount /dev/hdaX (The X is whatever partition number it is, from fdisk -l)

That will mount it to your desktop.  If that doesn't work, then you need to make a temperory folder somewhere, Mount the partition to there, and then use Nautilus to access it.  

sudo mkdir /tmp/windows
sudo mount /dev/hdaX /tmp/windows (Again, X is the partition number)
gksudo nautilus

The last line opens Nautilus, which allows you to view your files in root mode.  You will likely find that you can't access them, in that case, you need to do as follows to change the permission:

1 - Right-click on the File
2 - Click Properties
3 - Click Permission
4 - Change the Owner and Group to your Name, and the options under that to as you want, likely Read and Write, etc.

Hope that helps.

---

### Post by Mr. DVD on 2007-01-28
I seem to do pretty well with that last method, up until I have to use nautilus. The mounted Windows partition is read-only, what do I do now?

---

### Post by taurus on 2007-01-28
How did you mount the ntfs partition anyway?

This guide will walk you through adding an entry in /etc/fstab so it will be mounted automatically each time you boot Ubuntu.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Mr. DVD on 2007-01-28
I just followed these steps:
"sudo mkdir /tmp/windows
sudo mount /dev/hdaX /tmp/windows (Again, X is the partition number)
gksudo nautilus"

---

### Post by taurus on 2007-01-28
But you have to replace the /dev/hdaX with the actual partition of your harddrive.

What are the outputs of these two commands from a terminal?

```
sudo fdisk -l
df -h
```

---

### Post by Mr. DVD on 2007-01-28
I get these two: For the first command.
```
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte secto
```

For the latter:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              44G  2.0G   40G   5% /
varrun                221M   84K  221M   1% /var/run
varlock               221M     0  221M   0% /var/lock
procbususb             10M  152K  9.9M   2% /proc/bus/usb
udev                   10M  152K  9.9M   2% /dev
devshm                221M     0  221M   0% /dev/shm
lrm                   221M   18M  203M   8% /lib/modules/2.6.17-10-generic/volatile
/dev/hdc              700M  700M     0 100% /media/cdrom1
/dev/hda1             5.6G  3.4G  2.2G  61% /media/hda1
/dev/hda1              98G   45G   54G  46% /tmp/windows
/dev/hda2              98G   45G   54G  46% /tmp/windows

```

---

### Post by taurus on 2007-01-28
That should be lower case letter l as in larry.

```
sudo fdisk -l
```

---

### Post by Mr. DVD on 2007-01-28
Then I get this: 
```

Disk /dev/hda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         769     5813608+   b  W95 FAT32
/dev/hda2   *         770       14314   102400200    7  HPFS/NTFS
/dev/hda3           14315       20499    46758600   83  Linux
/dev/hda4           20500       20673     1315440    f  W95 Ext'd (LBA)
/dev/hda5           20500       20673     1315408+  82  Linux swap / Solaris

```

---

### Post by Goober on 2007-01-28
> **Mr. DVD said:**
> I seem to do pretty well with that last method, up until I have to use nautilus. The mounted Windows partition is read-only, what do I do now?

Were you able to use Nautilus to find your partition?  It should be under /tmp/windows (/tmp will be under Filesystem, if that helps).  After you find where the partition is mounted, and can see all of your files, you should be able to right-click on them, and change the permissions so you can read and write them, and thus access your files.  

I know that my method was kinda complicated, but it worked for me.  I know there must be a less complicated method out there somewhere.

---

### Post by taurus on 2007-01-28
Okay, edit your /etc/fstab with

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```

/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0
/dev/hda2   /media/hda2   ntfs   nls=utf8,umask=0222   0   0
```
Save the changes.  Now, create a new mount point for /dev/hda2 (since you already have one for /dev/hda1).

```
sudo mkdir /media/hda2
```
Reboot.  

Now, your fat32, /dev/hda1, will be automatically mounted to /media/hda1 with read/write permissions for everybody while your ntfs, /dev/hda2, will be mounted to /media/hda2 with read permission only.

---

### Post by Mr. DVD on 2007-01-29
Okay, it works now. Thanks to everyone that helped out! It'd be nice if I could write to it as well, but I guess NTFS can't be written to by Linux?

---

### Post by taurus on 2007-01-29
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

