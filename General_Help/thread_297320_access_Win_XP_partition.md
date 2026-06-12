---
title: "access Win XP partition"
date: 2006-11-10
forum: General Help
---

### Post by brad1138 on 2006-11-10
Sort of, I have a crashed XP machine, I am trying to save a bunch of Pictures.  I booted with the Ubuntu 6.10 cd. How can I access the "C:" drive from Ubuntu.

Thanks,
Brad

---

### Post by goodfella on 2006-11-11
you need to figure out what drive/partition your windows C:\ is on.  If you only have one disk then it is probably in the hda1 partition.  If you can get into a linux shell and type:

sudo fdisk -l

this will give a list of your drives and their partitions which will help other people solve your problem so make sure to post it to the forum.

---

### Post by brad1138 on 2006-11-11
Thanks, It is where I thought it was also dev/hda1. If this is going to be too complicated it will be easier to just pull the drive and put it in one of my other XP machines and get the files that way. Just thought this might be a somewhat easy way w/o having to pull comp apart.

Brad

---

### Post by goodfella on 2006-11-11
Sorry for the long delay but I had to go to work after I posted my reply.  If you want to just pull the drive out and put it in another computer that should work but it is no fun and you won't learn anything new about linux.  Where do you plan on copying the files to when you can get access to the windows partition?

---

### Post by brad1138 on 2006-11-12
*If you want to just pull the drive out and put it in another computer that should work but it is no fun and you won't learn anything new about linux.*

Ya I know, OK I'll keep going with Ubuntu.

*Where do you plan on copying the files to when you can get access to the windows partition?*

Another computer on my LAN.

---

### Post by goodfella on 2006-11-12
The usual way to access a windows partition is to mount it and then do what you need with it.  However, I don't know how the live cd's work and how from the live cd to access a drive on your lan.  Another thing is you need a mount point for the windows partition.  This is usualy /media/hda1 if your windows partition is hda1 like you mentioned earlier.  To get around the lan problem maybe you could use a usb drive which you should be able to mount from a live cd.  

To mount to your windows partition get into a terminal and type the following command if your windows filesystem is ntfs:

     ```
sudo mount -t ntfs /dev/hda1 /media/hda1
```

if the windows file system is fat32 then use this command:

     ```
sudo mount -t vfat /dev/hda1 /media/hda1
```

the 'sudo' command will ask you for a root password.  Hopefully you have one with the live cd.  Also the /media/hda1 folder must exist for this command work.  The /media/hda1 folder will be equivalent to C:\.  So if you had a folder called 'test' in the C:\ directory on windows, the way to access it in ubuntu would be to type in a terminal:

```
cd /media/hda1/test
```

Make sure that the files system the usb uses is fat32.  To mount the drive for read/write access use the following command:
     
     ```
sudo mount -t vfat -o iocharset=utf8,umask=000 /dev/sda1 /media/sda1 
``` 

Accessing the usb drive folders is the same as for the windows partition.  Also as before, the /media/sda1 folder must exist in order for the command to work.  With both the drives mounted you can use the cp command from the terminal to copy everything you need.

Hopefully this was helpfull.

---

### Post by brad1138 on 2006-11-12
*sudo mount -t ntfs /dev/hda1 /media/hda1*

when I tried that it says "hda1 does not exist". I tried creating it in Nautilus but the create folder options was grayed out. I tried mounting it to  just media which kind of worked (didn't give error anyway) but I couldn't access anything. Said either I didn't have permission or couldn't access it. I think it's a limitation of running it off cd. I was able to access network drives though.

---

### Post by goodfella on 2006-11-12
Type the following commands in the terminal to see what the permissions are for the /media folder and post the output to the forum:

```
cd /
```
```
ls -l media
```

---

### Post by Padraig Notlad on 2006-11-20
I'm having pretty much the same problem.  Can you help?  Here is what I get when I do what you said.  I want to see "disks-conf-sdb"  I believe that is the NTFS drives I want to see.

total 60
dr-x------ 1 root    root  8192 2006-11-19 17:56 disks-conf-sda1
dr-x------ 1 root    root  8192 2006-11-19 17:56 disks-conf-sdb1
drwx------ 3 padraig admin 4096 2006-11-20 21:56 gconfd-padraig
drwx------ 3 root    root  4096 2006-11-20 22:42 gconfd-root
drwx------ 2 padraig admin 4096 2006-11-20 21:56 keyring-3cJW50
drwx------ 2 padraig admin 4096 2006-11-20 22:42 libgksu1.2-LzVjn8
srwxr-xr-x 1 padraig admin    0 2006-11-20 21:56 mapping-padraig
drwx------ 2 padraig admin 4096 2006-11-20 22:45 orbit-padraig
drwx------ 2 root    root  4096 2006-11-20 22:42 orbit-root
drwx------ 2 padraig admin 4096 2006-11-20 21:56 ssh-kxhTMs4942
-rw-r--r-- 1 padraig admin 1077 2006-11-20 22:17 tmpBuR3If
-rw-r--r-- 1 padraig admin  653 2006-11-20 22:17 tmpLDBqDt
-rw-r--r-- 1 padraig admin  533 2006-11-20 22:17 tmpyJfLPl
srwxr-xr-x 1 padraig admin    0 2006-11-20 22:38 totem.padraig.2600143949
drwx------ 2 padraig admin 4096 2006-11-20 21:56 virtual-padraig.9WM6ur

---

### Post by ububaba on 2006-11-21
> **goodfella said:**
> The usual way to access a windows partition is to mount it and then do what you need with it.  

To mount to your windows partition get into a terminal and type the following command if your windows filesystem is ntfs:

     ```
sudo mount -t ntfs /dev/hda1 /media/hda1
```




I followed your instructions. I have two SATA disks for XP as you can see but
somehow I get this result.

> 
Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       23944   192330148+  83  Linux
/dev/hdb2           23945       24321     3028252+   5  Extended
/dev/hdb5           23945       24321     3028221   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        1278    10257502+   f  W95 Ext'd (LBA)
/dev/sda2   *        1279        5745    35881177+   7  HPFS/NTFS
/dev/sda3            5746        6006     2096482+   7  HPFS/NTFS
/dev/sda4            6007       19457   108045157+   7  HPFS/NTFS
/dev/sda5               2        1278    10257471    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdb2               1           1        8001   83  Linux
/dev/sdb5               2        6471    51970243+  83  Linux
/dev/sdb6            6472       19457   104310013+  83  Linux

Partition table entries are not in disk order
junk@trap-:~$ sudo mount -t ntfs /dev/sda1 /media/sda1
mount:** mount point /media/sda1 does not exist**


The claim that**[COLOR="Red"] mount point does not exist[/COLOR]** is really
bothersome. What is it that I misinterpret?:-k

---

### Post by carlosqueso on 2006-11-21
you need to create the directory /media/sda1, using 

```
sudo mkdir /media/sda1
```

or for brad:

```
sudo mkdir /media/hda1
```

---

### Post by ububaba on 2006-11-21
> **carlosqueso said:**
> you need to create the directory /media/sda1, using 

```
sudo mkdir /media/sda1
```

or for brad:

```
sudo mkdir /media/hda1
```

Thanks. I will do that and return much later.:-D

---

### Post by ububaba on 2006-11-21
> **carlosqueso said:**
> you need to create the directory /media/sda1, using 

```
sudo mkdir /media/sda1
```



Thanks. This is the result of running dmesg
> 
junk@trap-:~$ dmesg | tail
[17179791.764000] ISO 9660 Extensions: RRIP_1991A
[17199108.160000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17199108.308000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17199108.308000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17199108.308000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount op tion errors=recover not used. Aborting without trying to recover.
[17199108.308000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS vo lume.
[17199157.996000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17199157.996000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17199157.996000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount op tion errors=recover not used. Aborting without trying to recover.
[17199157.996000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.


Would it mean that instead of **sda1** I ought to go for **sda2**?
**sda2** is the first ntfs partition. Instead of daring, right now I am 
scared of loosing everything on that disk. :frown:

---

### Post by kartikya on 2006-11-21
create on any of your panels a "custom aplication launcher" 
 call it whatever you want but for command put: gksudo nautilus
 you can now acess your harddisk in root and can copy and edit whatever you want 
 I hope this fixes your probs....

---

### Post by ububaba on 2006-11-21
> **kartikya said:**
> create on any of your panels a "custom aplication launcher" 
 call it whatever you want but for command put: gksudo nautilus
 you can now acess your harddisk in root and can copy and edit whatever you want 
 I hope this fixes your probs....

[COLOR="Blue"]
junk@trap-:~$ gksudo nautilus

(nautilus:24692): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified 
are supported and host-based authentication fail[/COLOR]


I get the failure above and when I klick **sda1** or **sdb1** icons  it shows zero folders!
Earlier, for a long period of time, I could access XP partition but it disappeared recently
when I did a re-install.

---

