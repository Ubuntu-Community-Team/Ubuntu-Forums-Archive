---
title: "3ware raid drive not always recognised"
date: 2008-05-04
forum: General Help
---

### Post by Robbyx on 2008-05-04
Hardy H
Gigabyte GA-P35C-DS3R with Intel e8200

I had to buy a new board because my P6N SLI would not boot. Now I find an intermittent failure to find my 3ware raid drive.  When started as a cold boot I have found that fsck is reporting it can not find the raid drive. If I reboot it can find it. Has anyone else had similar problems or can offer a solution? 

Robin

---

### Post by fjgaude on 2008-05-05
Do you have the mount of the raid array in your fstab file? If so you might move it to the very end, or else change the nice priority for it. I'm not sure how to do the latter but you likely have a race issue. I'm sure it can be fixed but will take some cut-and-try work.

---

### Post by Robbyx on 2008-05-05
I hope you can give me a bit more help.

I have looked again at the log report and it is not the raid drive that is giving me trouble. Here is the log:

> Log of fsck -C3 -R -A -a 
Mon May  5 19:34:02 2008

fsck 1.40.8 (13-Mar-2008 )
/dev/sda2: clean, 41581/3940832 files, 2083052/7875866 blocks
Failed to open the device 'UUID=7b859c36-c68d-408f-9425-de9f525f3c71': No such file or directory


Failed to open the device 'UUID=b1bba368-3025-45c2-94cd-3ac8a32e40fd': No such file or directory


fsck died with exit status 8

Mon May  5 19:34:02 2008


Here are some device reports:

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00011035

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    59842124    29921031   83  Linux
/dev/sda2        59842125   122849054    31503465   83  Linux
/dev/sda3       122849055   964815704   420983325    5  Extended
/dev/sda4       964815705   976768064     5976180   82  Linux swap / Solaris
/dev/sda5       122849118   205358894    41254888+  83  Linux
/dev/sda6       299130363   964815704   332842671   83  Linux
/dev/sda7       205358958   299130299    46885671   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250058301440 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00075fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS
robin@robin:~$ ls /dev/disk/by-uuid -lah
total 0
drwxr-xr-x 2 root root 180 2008-05-05 19:33 .
drwxr-xr-x 5 root root 100 2008-05-05 19:33 ..
lrwxrwxrwx 1 root root  10 2008-05-05 19:33 003e4d16-908b-442c-92a6-9c3578d12c36 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-05-05 19:33 45a2e92c-c759-4732-9662-988da7f8ea7b -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-05-05 19:33 724E07853D78E7A8 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-05-05 19:33 7b859c36-c68d-408f-9425-de9f525f3c71 -> ../../sda7
lrwxrwxrwx 1 root root  10 2008-05-05 19:33 b1bba368-3025-45c2-94cd-3ac8a32e40fd -> ../../sda6
lrwxrwxrwx 1 root root  10 2008-05-05 19:33 e36cb6cf-f372-4418-bd8b-f36a27dc3e76 -> ../../sda4
lrwxrwxrwx 1 root root  10 2008-05-05 19:33 f35c7bf9-9c2b-4ec9-9522-84d73f3c37db -> ../../sda5
robin@robin:~$ 





sda5,6,7 are reiserfs
Only Sda6 and 7 are not being recognised.

Do you think that their being out of order is the cause? If so  I have not worked out how to put them into order.

here is my fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=003e4d16-908b-442c-92a6-9c3578d12c36 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd3  being new "home"
# UUID=f453ce62-336b-490b-8447-55acd2adc952 /home  ext3    nodev,nosuid,user_xattr    0       2
#/dev/sda2  being new "home"
UUID=45a2e92c-c759-4732-9662-988da7f8ea7b /home  ext3    nodev,nosuid,user_xattr    0       2
#sda7
UUID=7b859c36-c68d-408f-9425-de9f525f3c71 /media/backup reiserfs auto,user 0 2


#records and my docs (rade sdb1)
UUID=724E07853D78E7A8 /media/mydocs ntfs user,auto,noexec 0  2

#old download partition hdb5
#UUID=7E0442D704429257 /media/downloads ntfs auto,user 0 0

#media
UUID=b1bba368-3025-45c2-94cd-3ac8a32e40fd /media/flm reiserfs auto,user 0 2


/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#/dev/fd0        /media/floppy0  auto,umsdos,vfat,ext2    rw,user,sync,dirsync 0       0

none /proc/bus/usb usbfs defaults,devmode=0666 0 0 


#list partitions by uuid
# ls /dev/disk/by-uuid -lah

#list partitions by device
# sudo fdisk -lu

Can you see anything that could be causing fsck to  fail?

R

---

### Post by fjgaude on 2008-05-05
No, I don't see anything wrong... it is normal for the out of order notice... it's always that way: just a notice, an alert to be careful with how you look at the partition table.

Since your raid array seems to be on a card with its own driver that is already in Ubuntu I really can't see why it loads sometimes and sometimes not.

The sda6 and 7 could be a drive going bad. You could take the Live CD and run gparted on those partitions and see if anything is wrong. Do a Check. Gparted can fix most things in an ext3 filesystem.

Let us know how you are doing.

---

### Post by polski on 2008-09-13
I have very much the same problem, but it has gotten worse. Now  my system cannot seem to find the 3ware raid at all. That is to say, Xubuntu cannot. The command line utilities for the raid card says all is fine. This all happened after I did a verify of the raid array.

Original poster: Did you solve you problem?

---

### Post by fjgaude on 2008-09-13
What do you mean, "cannot seem to find"? What does

```
sudo fdisk -l
```

show?

---

### Post by polski on 2008-09-13
Sorry guys, I was sloppy. I am not new to linux but not very experienced.

This is what it shows

============================================
>:/dev$ sudo fdisk -l

Disk /dev/sda: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00050371

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3577    28732221   83  Linux
/dev/sda2            3578        3737     1285200    5  Extended
/dev/sda5            3578        3737     1285168+  82  Linux swap / Solaris

Disk /dev/sdb: 1254.9 GB, 1254995722240 bytes
255 heads, 63 sectors/track, 152577 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1519639

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      152577  1225574721   83  Linux
============================================

> **fjgaude said:**
> What do you mean, "cannot seem to find"? What does

```
sudo fdisk -l
```

show?

---

### Post by polski on 2008-09-13
After some more checking. I cannot even mount the raid partition anymore. I get this message.

>:/$ sudo mount /dev/sdb1 /mnt/raid/
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I have had no problem before. 
After I did a raid unit verify using the tools that 3ware offer then these problems started.

Any advice greatly appreciated.

---

### Post by polski on 2008-09-14
Well if anybody is interested I got it working again, but I lost a lot of data. Still trying to figure out if that was a fault of my own as I am still not very experienced with linux.

From what I understand my filesystem was bad so I did a
e2fsck

This did the trick, but afterwards I found out a lot of my files were corrupt. So dataloss! I still fear there is something not right with the raid array and I would like to re-format it, but need to find somewhere to move my data first :(

Now reading a little more after I have tried and failed. It seems that you should not use fsck AT ALL on a raid.
Can someone explain this too me?

So does that mean I did a big no no when I e2fsck:ed the unmounted raid.

Hope this has helped anyone, that is, not to make the same mistakes I did.

Cheers

---

### Post by fjgaude on 2008-09-14
Well, **fsck** checks my raid5 every 70 boot-ups without issue. My filesystem is an **ext3** and it seems the commands that the kernel gives to run fsck handles the file type correctly... the thing is, I'm sure the array is not mounted when the check occurs.

I've always had two backups to criticl data even using raid5 arrays, one online, one near-line. Sometimes have a third backup off-line, a daily.

---

