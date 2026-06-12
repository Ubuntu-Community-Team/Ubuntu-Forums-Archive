---
title: "I can't write on my thumb drive."
date: 2007-09-18
forum: General Help
---

### Post by wersdaluv on 2007-09-18
For some reason that I do not know, I cannot write on my thumb drive. I tried restarting X and rebooting my computer but I still can't. 

How do I solve this problem?

:KS

---

### Post by wersdaluv on 2007-09-18
Oh.. and I forgot to add.. I can access the drive, but I cannot write on it.

---

### Post by wersdaluv on 2007-09-18
```
~$ sudo fdisk -l ;mount; cat /etc/fstab
Password:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
16 heads, 63 sectors/track, 116280 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       67050    33792696   83  Linux
/dev/hda2           67050       90302    11719417+  83  Linux
/dev/hda3          112838      116280     1735020   82  Linux swap / Solaris
/dev/hda4   *       90302      112838    11357955   83  Linux
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sda: 503 MB, 503840256 bytes
4 heads, 8 sectors/track, 30751 cylinders
Units = cylinders of 32 * 512 = 16384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30752      492027+   e  W95 FAT16 (LBA)
/dev/hda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hda1 on /home type ext3 (rw)
/dev/hda2 on /media/hda2 type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/ALLAN'SDISK-1 type vfat (rw,nosuid,nodev,noatime,uid=1000,utf8,shortname=lower)
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=c4e65557-a1a8-48b7-a7e1-4918761f0957 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=7a8ef331-aaa4-4285-abf3-26aba5026db9 /home           ext3    defaults        0       2
# /dev/hda2
UUID=a0d59965-348b-492f-a12f-82e045610d88 /media/hda2     ext3    defaults        0       2
# /dev/hda3
UUID=c1f46875-c3d9-4193-85de-35e159e5acbd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Last few lines of dmesg after pulling the drive out ```
[ 1625.300000] FAT: Directory bread(block 508) failed
[ 1625.300000] scsi 1:0:0:0: rejecting I/O to dead device
[ 1625.300000] FAT: Directory bread(block 509) failed
[ 1625.300000] scsi 1:0:0:0: rejecting I/O to dead device
[ 1625.300000] FAT: Directory bread(block 510) failed
[ 1625.300000] scsi 1:0:0:0: rejecting I/O to dead device
[ 1625.300000] FAT: Directory bread(block 511) failed
[ 1625.300000] scsi 1:0:0:0: rejecting I/O to dead device
[ 1625.300000] FAT: Directory bread(block 512) failed
[ 1625.300000] scsi 1:0:0:0: rejecting I/O to dead device
[ 1625.300000] FAT: Directory bread(block 513) failed
[ 1625.300000] scsi 1:0:0:0: rejecting I/O to dead device
[ 1625.300000] FAT: Directory bread(block 514) failed
[ 1626.460000] scsi 1:0:0:0: rejecting I/O to dead device

```

---

### Post by wersdaluv on 2007-09-18
last few lines of dmesg after plugging the drive 
```
[ 1625.300000] FAT: Directory bread(block 511) failed
[ 1625.300000] scsi 1:0:0:0: rejecting I/O to dead device
[ 1625.300000] FAT: Directory bread(block 512) failed
[ 1625.300000] scsi 1:0:0:0: rejecting I/O to dead device
[ 1625.300000] FAT: Directory bread(block 513) failed
[ 1625.300000] scsi 1:0:0:0: rejecting I/O to dead device
[ 1625.300000] FAT: Directory bread(block 514) failed
[ 1626.460000] scsi 1:0:0:0: rejecting I/O to dead device
[ 3585.904000] usb 4-3: new high speed USB device using ehci_hcd and address 3
[ 3586.092000] usb 4-3: configuration #1 chosen from 1 choice
[ 3586.100000] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3586.100000] usb-storage: device found at 3
[ 3586.100000] usb-storage: waiting for device to settle before scanning
[ 3591.104000] usb-storage: device scan complete
[ 3591.116000] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 6.50 PQ: 0 ANSI: 0 CCS
[ 3591.140000] SCSI device sda: 984063 512-byte hdwr sectors (504 MB)
[ 3591.156000] sda: Write Protect is off
[ 3591.156000] sda: Mode Sense: 45 00 00 08
[ 3591.156000] sda: assuming drive cache: write through
[ 3591.212000] SCSI device sda: 984063 512-byte hdwr sectors (504 MB)
[ 3591.228000] sda: Write Protect is off
[ 3591.228000] sda: Mode Sense: 45 00 00 08
[ 3591.228000] sda: assuming drive cache: write through
[ 3591.228000]  sda: sda1
[ 3591.248000] sd 2:0:0:0: Attached scsi removable disk sda
[ 3591.248000] sd 2:0:0:0: Attached scsi generic sg0 type 0

```

---

### Post by tgalati4 on 2007-09-18
With the thumb drive plugged in, post the output of:

>sudo umount /dev/sda
>sudo fsck /dev/sda1

---

### Post by wersdaluv on 2007-09-18
I think, you asked me to post the right stuff. As for the first code, there is no output.

As for the second, ```
fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
?

```

---

### Post by wersdaluv on 2007-09-18
I think, you asked me to post the right stuff. As for the first code, there is no output.

As for the second, ```
fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
?

```

By the way, the drive can be written on on Windows. What do I do now?

:KS

Edit: I chose FAT number 1 ```
fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 1
/.Trash-allanc
  Contains a free cluster (2260). Assuming EOF.
Reclaimed 384 unused clusters (3145728 bytes).
Leaving file system unchanged.
/dev/sda1: 4663 files, 53803/61471 clusters

```

After that, I still can't write on it (on Kubuntu).

---

### Post by tgalati4 on 2007-09-18
Well, it's not a good idea to run filesystem check on a mounted drive.  So you unmount it.

Try fsck again, but choose the second FAT.

After mounting the drive, post:

>df -h

The drive could be full, so you need to empty the trash by manually deleting the .Trash files

---

### Post by wersdaluv on 2007-09-18
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4              11G  5.3G  4.9G  53% /
varrun                221M  108K  221M   1% /var/run
varlock               221M     0  221M   0% /var/lock
procbususb            221M  116K  221M   1% /proc/bus/usb
udev                  221M  116K  221M   1% /dev
devshm                221M     0  221M   0% /dev/shm
lrm                   221M   33M  188M  15% /lib/modules/2.6.20-16-generic/volatile
/dev/hda1              32G   28G  2.8G  91% /home
/dev/hda2              12G  2.4G  8.2G  23% /media/hda2
/dev/sda1             481M  424M   57M  89% /media/ALLAN'SDISK-1

```

---

### Post by wersdaluv on 2007-09-18
The output of ls -l /media/ALLAN\'SDISK-1/ is ```
total 96296
drwxr-xr-x 7 user root     8192 2007-08-13 22:00 2ndYear1stTermSchoolStuff
-r-xr-xr-x 1 user root      121 2007-09-30 10:33 AutoRun.inf
drwxr-xr-x 2 user root     8192 2007-07-16 08:07 BasketArchives
drwxr-xr-x 2 user root     8192 2005-06-20 21:40 connect_files
drwxr-xr-x 3 user root     8192 2007-04-16 13:43 ENGLCOM Portfolio
-r-xr-xr-x 1 user root    36864 2006-10-25 08:32 explorer.exe
-rwxr-xr-x 1 user root    31872 2007-03-25 11:13 inferioreast.pdf
-rwxr-xr-x 1 user root   348160 2007-05-01 11:50 msvcr71.dll
-rwxr-xr-x 1 user root    71168 2004-08-04 00:47 netsvcs.exe
drwxr-xr-x 2 user root     8192 2007-09-07 15:05 New Folder
drwxr-xr-x 4 user root     8192 2007-06-25 14:50 PortableApps
-rwxr-xr-x 1 user root 93938500 2007-06-24 00:11 PortableApps_Suite_Standard_1.0.exe
-rwxr-xr-x 1 user root    39936 2007-03-22 09:44 PORTFOLIO.ppt
drwxr-xr-x 2 user root     8192 2007-08-30 07:04 Print
-rwxr-xr-x 1 user root    23995 2007-04-16 00:13 print2.docx
-rwxr-xr-x 1 user root    30720 2007-02-20 06:16 q4-1.xls
-rwxr-xr-x 1 user root  3514318 2007-05-09 09:48 RavMonE.exe
dr-xr-xr-x 2 user root     8192 2007-09-30 10:33 recycler
-r-xr-xr-x 1 user root   184352 2007-07-09 07:33 RootFolder.com
-rwxr-xr-x 1 user root    40448 2007-04-04 10:17 RULEMAKERS1.doc
-rwxr-xr-x 1 user root    14236 2007-02-27 00:08 SumerianInfluence.odt
drwxr-xr-x 2 user root     8192 2007-05-01 11:27 System Volume Information
-rwxr-xr-x 1 user root        1 2007-05-01 11:27 Thumbs.db
-rwxr-xr-x 1 user root    22312 2007-03-30 18:33 vcalout.vcs
drwxr-xr-x 3 user root     8192 2007-02-28 13:49 windows
-rwxr-xr-x 1 user root   167508 2007-07-29 00:01 wlassistant_0.5.7-1+b1_i386.deb
-rwxr-xr-x 1 user root      296 2007-09-07 10:27 WMPInfo.xml

```

---

### Post by tgalati4 on 2007-09-19
To see the hidden files you need to use:

>ls -la

Your disk is 89% full.  What is in recycler and .Trash?

If I was an operating system, I wouldn't write anything to that drive.

---

### Post by wersdaluv on 2007-09-19
No more problem. I reformatted it already. 

:KS

---

