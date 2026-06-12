---
title: "[SOLVED] fsck.ext3: Unable to resolve 'LABEL=external-backup'"
date: 2008-02-03
forum: General Help
---

### Post by goodfella on 2008-02-03
When I first set up my external drive I had no problem booting my computer.  However, the next day my computer failed to boot properly by giving me the following error and going into a maintenance shell:
> 
fsck.ext3: Unable to resolve 'LABEL=external-backup'
fsck died with exit status 8


The strange thing is once I exit the maintenance shell and log in, the external hard drive is mounted.  Another strange thing is after the 30 day period when a file system is checked, fsck has no problem locating the drive by its label.  Note that the file system checked is not my external hard drive.

Following is my fstab file:
> 
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
/dev/sdb5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb3
/dev/hdb3 /home           ext3    defaults        0       2
# /dev/sdb8
LABEL=school /home/nick/school ext3 defaults         0       2
# /dev/sda3
/dev/sda3 /media/backup   ext3    defaults        0       2
#/dev/sdc5 external hard drive
LABEL=external-backup /media/ext-backup ext3 defaults     0     3
# /dev/sda2
/dev/sda2 /media/media    ext3    defaults        0       2
# /dev/sdb1
/dev/sdb1 /media/win32    ntfs    defaults,nls=utf8,umask=007,gid=46 0       2
# /dev/sda1
/dev/sda1 /media/win64    ntfs    defaults,nls=utf8,umask=007,gid=46 0       2
# /dev/sda1 grub boot partition
/dev/sdb3 /media/boot     ext3    defaults
# /dev/hdb2
#/dev/hdb2 /media/ubuntu-6-01 ext3 ro,suid,dev,exec,auto,nouser,async 0 2
#/dev/sdb4 vmware virtual machines
/dev/sdb7 /media/vmware   ext3    defaults        0       2
# /dev/hdb4
/dev/hdb4 none            swap    sw              0       0
# /dev/sdb6
/dev/sdb6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


The output of the command e2label is as follows:
```

e2label /dev/sdc5
external-backup

```

Note /dev/sdc5 is the device for my external hard drive.  The external hard drive is a Maxtor OneTouch III.

The fsck number of the external drive was set to 3 so my other drives will be checked and mounted properly before the external drive.  If anybody can shed some light on this problem I would appreciate it as I have googled the problem and have been unsuccessful in finding a solution.

---

### Post by ryanVickers on 2008-02-03
Was your computer booted with the disk connected and turned on the first time, but not the second time?

---

### Post by goodfella on 2008-02-04
Yes it was.  But I turned it back on after I realized that it was not on after booting, and still every subsequent reboot has the same problem.

---

### Post by ryanVickers on 2008-02-04
oh, OK then; I can just see it causing a problem if it expects it to be always there, but if that was the case then subsequent reboots should work properly.

But they didn't, so... :confused:
Perhaps just the fact it has a non-default label... I really don't have a clue :rolleyes:
Maybe just look for a way to make it not bother with checking it to avoid the problem for now.

---

### Post by goodfella on 2008-02-04
I set the pass option in my fstab file to 0 before but when I do that the drive is not automatically mounted after my system boots.

---

### Post by ryanVickers on 2008-02-04
That would be good enough for me ;), but if you want to still make it work, I would just then have it mount when you logon (System > Preferences > Sessions, and add the command).

---

### Post by blissend on 2008-02-08
I have the same issue that I'm not able to resolve. Hopefully someone will be able to help.

Here is my fstab...
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
LABEL=home      /home           ext3    defaults,usrquota,grpquota      0      1
LABEL=backup    /backup         ext3    defaults        0       1
```

Here is fdisk -l
```
Disk /dev/hdc: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4662    37447483+  83  Linux
/dev/hdc2            4663        4864     1622565    5  Extended
/dev/hdc5            4663        4864     1622533+  82  Linux swap / Solaris

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux
```

Here is df -h...
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc1              36G  2.3G   32G   7% /
varrun                506M  128K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  132K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  487M   4% /lib/modules/2.6.15-51-386/volatile
/dev/sdb1             917G   54G  817G   7% /home
/dev/sda1             917G   16G  855G   2% /backup
```

Typing e2label /dev/sda1 & /dev/sdb1 gives me the correct labels. Changing the pass to 0 will not mount it. When I hit ctlr+d everything works fine on both drives.

An interesting thing of note is this wasn't a problem if I mounted using "/dev/sda1" and only one drive plugged in.

Any help would be appreciated.

---

### Post by dcstar on 2008-02-09
AFAIK external USB drives should not be in the fstab file as they cannot be loaded at boot up time as the USB drivers are not active yet (but the internal hardware storage drivers are).

A USB drive not in fstab will be mounted automatically - by its label - when the kernel gets around to that part of the boot sequence.

I do this with USB stick and USB hard drives and it works fine.

---

### Post by goodfella on 2008-02-09
Thanks dcstar, I was either looking for a solution or a good explanation of what is going on and you provided both.  However, I did something different then your method because my usb devices do not automatically mount when I insert them.  So what I did was create a udev rule for the external drive.  The rule is as follows:
> 
# These are the rules for mounting external backup drives

# this rule mounts the Maxtor OneTouch III usb external backup drive
KERNEL=="sd?5",SYSFS{serial}=="2CAC09PE",SYSFS{product}=="OneTouch III",SYSFS{manufacturer}=="Maxtor",SYMLINK+="ext-backup",ACTION=="add",RUN+="/bin/mount -t ext3 /dev/ext-backup /media/ext-backup"

Note: there should not be a space between the "o" and "d" in "product".

Now everything works just as I like it.  Thanks for your help.

---

### Post by Tyb on 2008-03-24
Another solution:  Thanks to this thread, I learned some about udev rules.  Reading the udev rules docs about the standard rules, I realized that the /dev/disk/by-label/ directory was exactly what I needed.  My reasoning was this: something is wrong with the ext3 processing of LABEL directives in the fstab.  So don't use them... Instead of this line:

    LABEL=Ext_Backup_250       /disks/ext_backup/250a     ext3    defaults        0       2

I use this line

    /dev/disk/by-label/Ext_Backup_250       /disks/ext_backup/250a     ext3    defaults        0       2

Now the system boots clearly every time.

By the way, an earlier comment in this thread talks about not putting external USB disks in the fstab at all and letting later stages of the boot process simply discover them.  On my system, the kernel will mount them automatically if I plug them in after boot, but not if they are connected at boot time.  This is great for sticks and other frequently removed/inserted media, but not for my main disks that have to be there all the time.

Thanks to all for your contributions to this thread.

---

