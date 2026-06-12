---
title: "[SOLVED] (fstab question) System is confused between 'sda' and 'sdb'"
date: 2008-07-06
forum: General Help
---

### Post by misterbk on 2008-07-06
Hello, 

Looking for some help with an fstab problem related to having two drives and adding one post-install:

**Problem:**
I have one PATA drive and one SATA drive, which is plugged into a PCI SATA controller card.  The PATA drive has linux on it, SATA is for storage.

PATA drive shows as 'sda' in fstab but 'sdb' in linux.
SATA drive shows as 'sda' in linux and I want it in fstab.  (which conflicts.)

What's weird is everything works.  I would expect the system not to boot if fstab points to the wrong device?  I'm guessing that the system is recognizing the other hard drive after parsing fstab, and knocking the boot drive down a letter, but that somehow it doesn't matter at that point.

The problem is how to get the SATA drive to auto-mount as /basement by putting it in fstab.  Also the configuration looks broken and I'm wondering if and how I should fix it.

**Contents of fstab:**
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=c22d8199-e281-4cd6-a89a-43c661362cdb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=0525945c-1023-4b03-8d1a-bf968815bdd1 /boot           ext2    relatime        0       2
# /dev/sda10
UUID=1b4c64e0-ef55-49f8-8a18-72a9c836b19a /home           ext3    relatime        0       2
# /dev/sda7
UUID=5454530a-150c-423e-a902-5d597255a05d /music          ext3    relatime        0       2
# /dev/sda5
UUID=cede8556-a6c0-48bd-9cd4-a850fc8d0b97 /tmp            ext2    relatime,noexec        0       2
# /dev/sda9
UUID=d8593f5b-1aee-42d3-af0f-b02909bfa778 /var/log        ext3    relatime,noexec        0       2
# /dev/sda8
UUID=68013980-f54e-4c5a-9b4b-dc6001ab385a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

**Output of df:**
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb6             19380676   2818904  15585024  16% /
varrun                  257788       128    257660   1% /var/run
varlock                 257788         0    257788   0% /var/lock
udev                    257788        72    257716   1% /dev
devshm                  257788         0    257788   0% /dev/shm
lrm                     257788     38684    219104  16% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb1                45130     11540     31182  28% /boot
/dev/sdb10             7761868    155416   7215272   3% /home
/dev/sdb7            168205816  69583900  90144820  44% /music
/dev/sdb5              1008672        32    954824   1% /tmp
/dev/sdb9               326649    306076      3708  99% /var/log
/dev/sda1            976576568 124659076 842149892  13% /media/the_basement

```


**Also probably relevant:**  I had difficulties during the Kubuntu install because of the drives.  If I had both plugged in during install, I got a Grub error "File Not Found" after install and the system wouldn't load.  I removed the SATA drive, reinstalled, and plugged it back in after booting up and shutting down once, and that got my system running.

I didn't try installing with both drives present and then modifying GRUB.  (because I am Grub-illiterate.)

Make sense to anyone?

---

### Post by kuja on 2008-07-06
The reason everything is working okay is because your fstab is referencing the UUID's instead of accessing them via /dev/sd?. The issue with things getting confused between BIOS and grub and Linux seems to be a relatively common problem. 

To add the other things to fstab, use the UUID of the partition and it should work fine. To get the UUID use the vol_id command. For example:

```
sudo vol_id --uuid /dev/sda1
```

---

### Post by misterbk on 2008-07-09
Wow thanks Kuja!

I noticed the UUID entries at the beginning after posting and got confused, they are entirely new to me after using several flavors of linux.  

Considering my old Debian system used to get hosed if I traded hard drives around much, I welcome them!

---

