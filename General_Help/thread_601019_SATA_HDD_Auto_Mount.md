---
title: "SATA HDD Auto Mount"
date: 2007-11-02
forum: General Help
---

### Post by sliPrix on 2007-11-02
I have searched around the forums and online elsewhere, but have found that I still don't understand making a HDD auto mount, and would greatly appreciate an explanation and solution to what I need to do.

I have a 40Gb HDD divided into to approximately 20Gb partitions, one holding ubuntu, and the other xp.  This HDD is an IDE controlled HDD.  I have a seperate SATA HDD that is 250Gbs, and the entire thing is partitioned into one large NTFS partition.  My question to you is how do I force this HDD (/dev/sdb) to automatically mount at /media/storage (I have already created the directory).  I do not know what I need to type into my fstab file, or where (what line) to enter in the information at.  I greatly appreciate your help!

When I issue the command ```
sudo fdisk -l
``` the output is as follows:
```
Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2473    19864341    7  HPFS/NTFS
/dev/hdb2            2474        4760    18370327+  83  Linux
/dev/hdb3            4761        4866      851445    5  Extended
/dev/hdb5            4761        4866      851413+  82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    c  W95 FAT32 (LBA)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

```

Disregard the 500Gb HDD, it's an external one, that is not going to be used often.
When I issue the command ```
df -h
``` the following results:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb2              18G  2.9G   14G  18% /
varrun                1.5G   88K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   84K  1.5G   1% /dev
devshm                1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G   14M  1.5G   1% /lib/modules/2.6.22-14-generic/volatile

```
My fstab file looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
# /dev/sda1     /media/storage  ntfs    defaults        0       0
UUID=ac46c543-3f66-45bd-8f02-3fb290ef3e5d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=6e35ce7c-db57-4a7f-8c25-67c162d15046 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by snkmad on 2007-11-02
Just found this on other thread, hope it helps you: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Or this, if the manual setup dont work for some reason: [http://ubuntuforums.org/showpost.php?p=3694162&postcount=2](http://ubuntuforums.org/showpost.php?p=3694162&postcount=2)

---

### Post by dcstar on 2007-11-02
> **sliPrix said:**
> I have searched around the forums and online elsewhere, but have found that I still don't understand making a HDD auto mount, and would greatly appreciate an explanation and solution to what I need to do.
.........]

[http://ubuntuforums.org/showpost.php?p=3694196&postcount=7](http://ubuntuforums.org/showpost.php?p=3694196&postcount=7)

---

### Post by sliPrix on 2007-11-02
> Just found this on other thread, hope it helps you: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Thanks, I'll try this now, I hope it works.

> 
Quote:
Originally Posted by sliPrix View Post
I have searched around the forums and online elsewhere, but have found that I still don't understand making a HDD auto mount, and would greatly appreciate an explanation and solution to what I need to do.
.........]
[http://ubuntuforums.org/showpost.php...96&postcount=7](http://ubuntuforums.org/showpost.php...96&postcount=7)

That thread was made while I was constructing mine.

---

### Post by geo909 on 2007-11-02
Hi, I had excactly the same question a couple of minutes
ago (look some threads up!)and thesolution was straightforward:

 Install the pysdm package, 
then use System-Administration-Storage Device Manager to set all of this up for you automagically.

 Mine works fine with this.

---

### Post by sliPrix on 2007-11-04
Thanks geo909 I tried the pysdm package, it worked flawlessly.  I now have my HDD auto mounting with no issues wahtsoever.  My only word of advice to other people who try this is dont forget to run it like:
```
sudo pysdm
``` 
You can run it as a normal user, however if you dont run it as sudo, you wont be able to change any setings.

---

