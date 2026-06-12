---
title: "Unable to mount ext3 drive."
date: 2013-06-10
forum: General Help
---

### Post by sebin on 2013-06-10
I was moving some files from one hard disk to another few days before. And i got some error and the move didnot complete. From the next restart i am not able to mount the drive.

I used a utility Disks3.4.1 and tired the 'extended' Self test and found no issues. [ATTACH=CONFIG]243698[/ATTACH]

When I click the Nautilus, i get this error

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

From the Disks i tried to mount the drive.

```
Error mounting /dev/sdc1 at /run/media/seb/Backup: Command-line `mount -t "ext3" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdc1" "/run/media/seb/Backup"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

 (udisks-error-quark, 0)
```

```

seb@seb-desk:~$ sudo blkid -c /dev/null -o list
[sudo] password for seb:
device                                             fs_type         label            mount point                                            UUID
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                          ext2                             /boot                                                  4eae45cd-b144-42c6-b639-2c3b4c94a574
/dev/sda3                                          ext4            Data             (not mounted)                                          86643ccc-edea-4403-94ad-7d6f9e359720
/dev/sda5                                          swap                             <swap>                                                 ca172f50-7d6c-4790-a066-c2898c6fac2f
/dev/sda6                                          ext3                             /                                                      5c857b8b-bd20-49a6-9579-5db8ff513124
/dev/sdb1                                          vfat            B!B!N            (not mounted)                                          C0BD-EFDC
/dev/sdb5                                          ntfs            B!b!n(softwares) (not mounted)                                          08BED2A9BED28F16
/dev/sdb6                                          ntfs            B!b!n(resources) (not mounted)                                          02202D8E202D8A2D
/dev/sdb7                                          ntfs            B!b!n(x)         (not mounted)                                          F2406C5F406C2C93
/dev/sdc1                                          ext3            Backup           (not mounted)                                          2e8d6192-0656-4b29-ab2f-fdaf35336ee0
/dev/sdd                                           ext4            Video            /media/Video                                           173cc407-f6b1-4e68-ba42-50f473a58bea
seb@seb-desk:~$ 


```

```
seb@seb-desk:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009fa6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      976895      487424   83  Linux
/dev/sda2          978942   211527679   105274369    5  Extended
/dev/sda3       211527855   976768064   382620105   83  Linux
/dev/sda5          978944    32976895    15998976   82  Linux swap / Solaris
/dev/sda6        32978944   211527679    89274368   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xef125d1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    58605119    29302528+   c  W95 FAT32 (LBA)
/dev/sdb2        58605120   312576704   126985792+   f  W95 Ext'd (LBA)
/dev/sdb5        58605183   117210239    29302528+   7  HPFS/NTFS/exFAT
/dev/sdb6       117210303   214869374    48829536    7  HPFS/NTFS/exFAT
/dev/sdb7       214869438   312576704    48853633+   7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table


```


I am using ubuntu 12.04.  and
```
seb@seb-desk:~$ uname -r
3.2.0-45-generic


```

---

### Post by ajgreeny on 2013-06-10
Just to be sure the partition sdc1 is not mounted run the command ```
sudo umount /dev/sdc1
```  then run command ```
sudo e2fsck /dev/sdc1
``` and see if any errors are reported.

---

### Post by sum1nil on 2013-06-10
According to this Debian info at [http://www.pjc.me.uk/efi-gpt/index.html](http://www.pjc.me.uk/efi-gpt/index.html)

You can use 'parted /dev/sdc print' to get the real partitions since the fdisk listing is going to be wrong.

I hope the conversion didn't destroy the partitions.

---

### Post by sebin on 2013-06-10
```
seb@seb-desk:~$ sudo umount /dev/sdc1
[sudo] password for seb: 
umount: /dev/sdc1: not mounted
seb@seb-desk:~$ sudo e2fsck /dev/sdc1
e2fsck 1.42 (29-Nov-2011)
Backup: recovering journal
Backup contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (27167119, counted=27221687).
Fix<y>? yes

Free inodes count wrong (122064318, counted=122064323).
Fix<y>? yes


Backup: ***** FILE SYSTEM WAS MODIFIED *****
Backup: 37437/122101760 files (18.7% non-contiguous), 461156950/488378637 blocks
seb@seb-desk:~$ 


```

Thank you ajgreeny, now i am able to mount the drive in Nautilus. But when i select the files, the menu item cut is active why?

```
seb@seb-desk:/media/Backup/Sounds$ ls -l
total 4704
drwx------ 11 seb seb    4096 Oct 14  2010 aarthycb
drwx------ 14 seb seb    4096 Jan 15  2011 Alexander
drwx------  2 seb seb    4096 May 27  2012 A Sivamani - Mahaleela [2008-MP3-VBR-320Kbps] - xDR
-rwxrwxrwx  1 seb seb 4724780 Jan  1  1980 Clapping.WAV
drwx------ 81 seb seb    4096 Mar 19  2012 Jubin
drwx------ 11 seb seb    4096 Jan 18  2011 Malayalam
drwxr-xr-x  8 seb seb    4096 Jun  1  2011 Melam
drwx------ 41 seb seb   12288 May 27  2012 MUZIK VIDEO THEATRE
drwx------ 22 seb seb    4096 Oct 14  2010 New hares
drwx------ 11 seb seb    4096 Nov  1  2011 new_songs
drwx------  8 seb seb    4096 Oct 14  2010 non-mp3
seb@seb-desk:/media/Backup/Sounds$ 

```

---

### Post by sebin on 2013-06-11
One more question. How will i know, which are the damaged files?

---

