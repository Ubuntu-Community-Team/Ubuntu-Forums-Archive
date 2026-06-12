---
title: "CD just spins, can't access"
date: 2008-03-28
forum: General Help
---

### Post by G_Stewart on 2008-03-28
:confused:
Nothing changed (that I know) but, all of a sudden if I insert a CD it just spins. It won't open a new window, I can't access through K3B, the light on the CD rom simply blinks fast.

Help....

---

### Post by ibuclaw on 2008-03-28
What types of CDs/DVDs have you tried?

Does it work with another OS?

Have you done anything potentially damaging such as over-burning to CD-RWs in the past?

Also, how do you handle the opening/closing of the CD Drive?

Giving the output of these commands would help as well.
Find the line "**/dev/scd0**" in this file:
```
 nano /etc/fstab 
```

And Copy&Paste the output of:
```
 lsscsi 
```

Regards

---

### Post by G_Stewart on 2008-03-28
Tried several CD's on several computers, worked fine.
No damage
I use both the eject button and right-click eject.

fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5874bf9c-eb75-4255-8d91-e4ab94714ed5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4f2e54d6-c42c-4be3-af68-9185e5c59975 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /storage        ext3    defaults                0       0
/dev/sdc1       /media/usbdrive vfat defaults,user      0       0

Can't use lsscsi, tried to download it and got this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
guy@guy-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
guy@guy-desktop:~$ sudo dpkg --configure -a
Setting up bricolage-db (1.8.9-2ubuntu1) ...
invoke-rc.d: unknown initscript, /etc/init.d/postgresql-7.4 not found.
dpkg: error processing bricolage-db (--configure):
 subprocess post-installation script returned error exit status 100
Setting up libc6 (2.6.1-1ubuntu10) ...

dpkg: dependency problems prevent configuration of bricolage:
 bricolage depends on bricolage-db (>= 1.8.3-6); however:
  Package bricolage-db is not configured yet.
dpkg: error processing bricolage (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 bricolage-db
 bricolage

---

### Post by ibuclaw on 2008-03-28
Do you have trouble for both CD Disc Drives?

My fstab current fstab entries looks like this:
In bold are the differences between yours and mine.
```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto**,exec,utf8** 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto**,exec,utf8** 0       0

```

and as for your apt-get error
Is there a reason why you need bricolage?
Perhaps trying:
```
 apt-get auto-remove 
```
If it allows you...

Else, it's not, some claims that removing all info on the broken package in the /var/lib/dpkg folder helps fix this.
[Read here]("http://ubuntuforums.org/showthread.php?t=462135")

---

### Post by Bllasae on 2008-03-29
Restart the computer. This happens infrequently on all operating systems.

---

