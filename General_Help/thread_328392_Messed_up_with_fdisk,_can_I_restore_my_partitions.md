---
title: "Messed up with fdisk, can I restore my partitions?"
date: 2006-12-30
forum: General Help
---

### Post by barney_1 on 2006-12-30
Hi all,

I was using fdisk to redo a usb thumb drive on /dev/sdb.  I accidentally typed /dev/sda which is where my main SATA HDD is.  Long story short, I used to have sda1 through sda7, now only have sda1.

My system is still running, and I haven't rebooted, can I restore my partition settings?  I'm running edgy, here's the output of:

sudo fdisk -l
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux

```

Here's my fstab if that helps:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6 -- converted during upgrade to edgy
UUID=76b79d37-e36c-4ec6-908f-4cca4beca257 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda7 -- converted during upgrade to edgy
UUID=a35ab384-9b49-4736-9882-4eac9790103a none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=F2C085EDC085B7FD /mnt/Cdrive ntfs umask=0222 0 0
# /dev/sda2 -- converted during upgrade to edgy
UUID=F4C4882FC487F262 /mnt/Ddrive ntfs umask=0222 0 0
# /dev/sda3 -- converted during upgrade to edgy
UUID=07ac799d-9626-45af-9b4d-aafafe25ce5f /Flanders ext3 defaults 0 0
# /dev/sda5 -- converted during upgrade to edgy
/dev/sda5 /Lenny xfs defaults 0 0
//192.168.1.100/NAS1		/Milhouse smbfs	credentials=/root/.smbcredentials,rw,uid=mike	0	0
//192.168.1.100/NAS2		/Skinner smbfs	credentials=/root/.smbcredentials,rw,uid=mike	0	0

```

---

### Post by bernied on 2006-12-30
I'm sure this is doable - it is probably only the partition table that you have damaged. Is there anywhere that you might have saved (or posted to a forum) your old table? Or do you know the exact sizes of your previous partitions?

Have you had a look about your GUI utilities for disk management or something like it.

Also maybe the [df command](http://www.die.net/doc/linux/man/man1/df.1.html) might be able to help you.

Trouble is, to test that you fixed it involves a restart...

---

### Post by barney_1 on 2006-12-30
Thanks for the help with the df command.  I think that provides some good information for me.  I have an idea of how I had things set up.  Here is the output of the command:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6              9629880   6474348   2666356  71% /
varrun                  517452       160    517292   1% /var/run
varlock                 517452         4    517448   1% /var/lock
procbususb               10240       144     10096   2% /proc/bus/usb
udev                     10240       144     10096   2% /dev
devshm                  517452         0    517452   0% /dev/shm
/dev/sda1             10482380   7873844   2608536  76% /mnt/Cdrive
/dev/sda2             52428124  46660344   5767780  89% /mnt/Ddrive
/dev/sda3             82567220  46172936  32200116  59% /Flanders
/dev/sda5            155457308  44914752 110542556  29% /Lenny

```

I also found out about a program called gpart (different from gparted).  It guesses at your partition information.  I ran it once, it's initial scan identified all but one of my partitions, but the guess information at the bottom is not correct:

```
Begin scan...
Possible partition(Windows NT/W2K FS), size(10236mb), offset(0mb)
Possible partition(Windows NT/W2K FS), size(51199mb), offset(10236mb)
Possible extended partition at offset(143353mb)
   Possible partition(SGI XFS filesystem), size(151813mb), offset(143353mb)
   Possible partition(Linux ext2), size(9554mb), offset(295241mb)
   Possible partition(Linux swap), size(447mb), offset(304795mb)
End scan.

Checking partitions...
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
   Partition(Linux ext2 filesystem): logical 
   Partition(Linux ext2 filesystem): logical 
   Partition(Linux swap or Solaris/x86): logical 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 10236mb #s(20964760) s(63-20964822)
   chs:  (0/1/1)-(1023/254/63)d (0/1/1)-(1304/254/61)r

Primary partition(2)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 51199mb #s(104856248) s(20964825-125821072)
   chs:  (1023/254/63)-(1023/254/63)d (1305/0/1)-(7831/254/56)r

Primary partition(3)
   type: 015(0x0F)(Extended DOS, LBA)
   size: 161889mb #s(331549470) s(293587875-625137344)
   chs:  (1023/254/63)-(1023/254/63)d (18275/0/1)-(38912/254/63)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

```

the above listed guesses for Primary partitions 1 and 2 correspond correctly to /dev/sda1 and /dev/sda2.  The guess for Primary partition 3 is not correct though.  I'm running gparted with the -i option so that I can approve it's scan and hopefully that will help.

Does anyone else have some pointers on how I can rebuild my partition table?

---

### Post by barney_1 on 2006-12-30
I ran a program called testdisk and it seems to have restored my partitions.  I can mount them from the ubuntu live cd.  Unfortnately, I can't boot my computer.  I think this may be due to grub not being installed on the mbr.  Can someone point me in the right direction for resinstalling grub??

Thanks!

---

### Post by Sef on 2006-12-31
How to [Restore GRUB.]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by barney_1 on 2006-12-31
RESOLVED

Thanks everyone for the help.

I ended up restoring my partitions with a program called testdisk (available in the repositories, either universe or multiverse).  I detected all of my partitions quickly and accurately. 

Thank you Sef for you advice on restoring grub.  I actually did it a different way that I think is a better option.  Anyone interested check out post #5 from this thread:
[http://ubuntuforums.org/showthread.php?t=297548]("http://ubuntuforums.org/showthread.php?t=297548")

---

