---
title: "Mount partition EXT4-fs (sda4): unable to read superblock"
date: 2017-01-27
forum: General Help
---

### Post by rafaroda on 2017-01-27
Hi Ubuntu Community!

I'm trying to mount an ext4 partition but get EXT4-fs (sda4): unable to read superblock error. in SSD disk Sector size (logical/physical): 512B/4096B

The origin of my problem can be found at links [1] [2]: Windows 10 upgrade corrupted ext4 Ubuntu partition into free space unallocated

I'm now running an Ubuntu Live install.

Executing parted print: partition 4 is my /dev/sda4 ext4 that I want to mount, seems to be there

```
ubuntu@ubuntu:~$ sudo parted
GNU Parted 3.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s
(parted) print                                                            
Model: ATA Crucial_CT1024MX (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start       End          Size        Type      File system  Flags
 1      2048s       1026047s     1024000s    primary   ntfs         boot
 2      1026048s    987440363s   986414316s  primary   ntfs
 3      987441152s  988377087s   935936s     primary                diag
 4      988379134s  1953523711s  965144578s  extended

```

Executed parted rescue: no result was found

```
(parted) rescue                                                           
Start? 988377088
End? 1953523713
(parted)  

```

Trying to mount:

```

ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda4 /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

dmesg error is:

```

[ 7853.102811] EXT4-fs (sda4): unable to read superblock

```

Tried
```
ubuntu@ubuntu:~$ sudo mount -t ext4 -o loop,ro /dev/sda4 /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

Same dmesg:
```

[ 7940.056411] EXT4-fs (loop1): unable to read superblock

```

Partition seems to be there but can't mount it: any idea on how to do it so I can at least read it and get my data back?

Thanks :)

[1] [http://askubuntu.com/questions/828838/installed-windows-10-grub-problem-linux-drive-became-unallocated/](http://askubuntu.com/questions/828838/installed-windows-10-grub-problem-linux-drive-became-unallocated/)
[2] [http://askubuntu.com/questions/875960/windows-10-upgrade-corrupted-ext4-ubuntu-partition-into-free-space-unallocated](http://askubuntu.com/questions/875960/windows-10-upgrade-corrupted-ext4-ubuntu-partition-into-free-space-unallocated)

---

### Post by oldfred on 2017-01-27
Your sda4 is an extended partition. You cannot mount it.
And extended partition is a container for logical partitions. If you had partitions in your extended they would be sda5, sda6 etc.
Did you have both an ext4 and swap in the extended or only one partition?

I think if using parted rescue, you need the start & end to be inside the extended partition's start & end.
I might also try testdisk.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Dennis N on 2017-01-27
In the first display, #4 is shown as extended, which can be described as a container for logical partitons. You can only mount physical and logical partitions in an msdos partition scheme. Use gparted to create a logical partition.

---

### Post by rafaroda on 2017-01-28
Thanks oldfred and Dennis, I really appreciate your help: helps me also to better understand how partitions work :)


"Your sda4 is an extended partition. You cannot mount it.": OK, makes sense: sorry I'm not very familiar with partitioning.


I used parted rescue again with start & end values inside the extended partition but did not find anything. Any way to guess/calculate the start & end numbers? I used 988379136 (start of extended partition + 2 sectors) and 1953523711 (end of extended partition): I used other combinations of start & end but did not find anything neither.


My status now: sudo parted /dev/sda unit s print
```

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA Crucial_CT1024MX (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start       End          Size        Type      File system  Flags
 1      2048s       1026047s     1024000s    primary   ntfs         boot
 2      1026048s    987440363s   986414316s  primary   ntfs
 3      987441152s  988377087s   935936s     primary                diag
 4      988379134s  1953523711s  965144578s  extended

```


When: sudo fdisk -l /dev/sda
```

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda                                   
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x1d5a0541


Device     Boot     Start        End   Sectors   Size Id Type
/dev/sda1  *         2048    1026047   1024000   500M  7 HPFS/NTFS/exFAT
/dev/sda2         1026048  987440363 986414316 470.4G  7 HPFS/NTFS/exFAT
/dev/sda3       987441152  988377087    935936   457M 27 Hidden NTFS WinRE
/dev/sda4       988379134 1953523711 965144578 460.2G  5 Extended


Partition 4 does not start on physical sector boundary.

```


For your information, in a different computer that was given me partitioned in the same way, but with a smaller HDD (instead of SSD), my partition table looks like that (in Spanish, sorry):
```

user@casa:~$ sudo parted /dev/sda unit s print
Modelo: ATA Hitachi HTS72505 (scsi)
Disco /dev/sda: 976773168s
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones: msdos
Disk Flags: 


Numero  Inicio      Fin         Tamaño      Tipo      Sistema de archivos  Banderas
 1      2048s       1026047s    1024000s    primary   ntfs                 arranque
 2      1026048s    493807075s  492781028s  primary   ntfs
 3      493807616s  495456255s  1648640s    primary   ntfs                 diag
 4      495458302s  976771071s  481312770s  extended
 5      495458304s  968519679s  473061376s  logical   ext4
 6      968521728s  976771071s  8249344s    logical   linux-swap(v1)


user@casa:~$ sudo fdisk -l /dev/sda
sudo: imposible resolver el anfitrión casa
Disk /dev/sda: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x71a4dad7


Disposit.  Inicio     Start     Final  Sectores   Size Id Tipo
/dev/sda1  *           2048   1026047   1024000   500M  7 HPFS/NTFS/exFAT
/dev/sda2           1026048 493807075 492781028   235G  7 HPFS/NTFS/exFAT
/dev/sda3         493807616 495456255   1648640   805M 27 WinRE NTFS oculto
/dev/sda4         495458302 976771071 481312770 229,5G  5 Extendida
/dev/sda5         495458304 968519679 473061376 225,6G 83 Linux
/dev/sda6         968521728 976771071   8249344     4G 82 Linux swap / Solaris

```


Regarding testdisk: I tested it but:
1) Analyse > Intel > Search, then Deeper Search: just finds the Windows partition
2) Analyse > None > Search, then Deeper Search: also just finds the Windows partition


I'm pretty sure my Ubuntu was inside the /dev/sda4 extended partition: a /dev/sda5 Linux partition plus a /dev/sda6 swap partition of 4GB. I'm hoping that it is just my partition table that was just corrupted and no data deleted (same case as in [1]): is there a way to calculate the Start and Final sectors and add the partition to the partition table? Creating a logical partition inside my extended partition will overwrite the existing data?


Thanks :)


[1] [http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/)

---

### Post by oldfred on 2017-01-29
Not sure if others have posted more details on how  they fixed it.
 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462) 

You can run photorec to try to recover data.

You also can force a new partition into the space in the extended partition. I might not worry about swap.
      
 Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors 
   Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by rafaroda on 2017-01-30
Thanks oldfred for your links and explanation :)

Following your links, I tried to manually fix my partition table.

Old old-parts.txt: sudo sfdisk -d /dev/sda > old-parts.txt
```

label: dos
label-id: 0x1d5a0541
device: /dev/sda
unit: sectors


/dev/sda1 : start=        2048, size=     1024000, type=7, bootable
/dev/sda2 : start=     1026048, size=   986414316, type=7
/dev/sda3 : start=   987441152, size=      935936, type=27
/dev/sda4 : start=   988379134, size=   965144578, type=5

```

New new-parts.txt I edited: sudo sfdisk -f /dev/sda < new-parts.txt
```

label: dos
label-id: 0x1d5a0541
device: /dev/sda
unit: sectors


/dev/sda1 : start=        2048, size=     1024000, type=7, bootable
/dev/sda2 : start=     1026048, size=   986414316, type=7
/dev/sda3 : start=   987441152, size=      935936, type=27
/dev/sda4 : start=   988379134, size=   965144578, type=5
/dev/sda5 : start=   988379136, size=   965144578, type=83

```

Now: sudo fdisk -l /dev/sda
```

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x1d5a0541


Device     Boot     Start        End   Sectors   Size Id Type
/dev/sda1  *         2048    1026047   1024000   500M  7 HPFS/NTFS/exFAT
/dev/sda2         1026048  987440363 986414316 470.4G  7 HPFS/NTFS/exFAT
/dev/sda3       987441152  988377087    935936   457M 27 Hidden NTFS WinRE
/dev/sda4       988379134 1953523711 965144578 460.2G  5 Extended
/dev/sda5       988379136 1953523711 965144576 460.2G 83 Linux


Partition 4 does not start on physical sector boundary.

```

And sudo parted /dev/sda unit s print
```

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA Crucial_CT1024MX (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start       End          Size        Type      File system  Flags
 1      2048s       1026047s     1024000s    primary   ntfs         boot
 2      1026048s    987440363s   986414316s  primary   ntfs
 3      987441152s  988377087s   935936s     primary                diag
 4      988379134s  1953523711s  965144578s  extended
 5      988379136s  1953523711s  965144576s  logical

```

Problem: file system of sda5 partition is not recognized as ext4.

```

ubuntu@ubuntu:~$ sudo fsck -t ext4 /dev/sda5
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
ext2fs_open2: Bad magic number in super-block
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sda5


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

```

Following [1], I run:
```

ubuntu@ubuntu:~$ sudo mke2fs -n /dev/sda5
mke2fs 1.42.13 (17-May-2015)
Creating filesystem with 120643072 4k blocks and 30162944 inodes
Filesystem UUID: 905daa50-f427-4c27-904b-cba75f0b69f0
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000

```

And tried every single superblock without success:
```

ubuntu@ubuntu:~$ sudo e2fsck -b 71663616 /dev/sda5

```

blkid is
```

ubuntu@ubuntu:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/loop0 squashfs         /rofs          
/dev/sr0   iso9660 Ubuntu 16.04.1 LTS amd64 /cdrom 2016-07-19-21-27-51-00
/dev/sda1  ntfs    Reservado para el sistema (not mounted) 00E40FE9E40FE030
/dev/sda2  ntfs             (not mounted)  02881C62881C570F
/dev/sda3                   (not mounted)  
/dev/sda5                   (not mounted)  

```

Regarding testdisk, running it with selecting Intel:
```

TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors


 1 * HPFS - NTFS              0  32 33    63 221 30    1024000
 2 P HPFS - NTFS             63 221 31 61465  81 36  986414316
 3 P Windows RE(store)    61465  94  6 61523 160 13     935936
 4 E extended             61523 192 44 121601  57 56  965144578
No ext2, JFS, Reiser, cramfs or XFS marker
 5 L Linux                61523 192 46 121601  57 56  965144576
 5 L Linux                61523 192 46 121601  57 56  965144576

```

And testdisk selecting None:
```

TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors
>P NTFS                     0  32 33    63 221 30    1024000
 P NTFS                    63 221 31 61465  81 36  986414316

```


My questions at this point:
[LIST=1]
[*]Is my new-parts.txt correct?
[*]How to make the partition be recognised as ext4?
[/LIST]

Thank you in advance for any suggestion :)

[1] [https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)[FONT=Verdana]
[/FONT]

---

### Post by oldfred on 2017-01-30
I would have thought that the e2fsck would have fixed it.


Perhaps including your old swap confuses it?
If you know swap size, you can make sda5 smaller by approx size of swap in sectors.
Or was swap first logical partition, and your ext4 second logical?

Not sure what else to suggest.

Disks under format partition (gear icon) has the option to set to ext4 but not overwrite data or quick format.

---

### Post by rafaroda on 2017-01-31
Thanks again oldfred :)

I tried making sda5 smaller but still same issue. 

Some basic questions:
[LIST]
[*]ext4 is not detected as file system just because the correct start and end values of the partition are not set? Or could this be caused by a different issue?
[*]If I'm able to guess the start and end of the partition, will the file system be recognised as ext4? For instance, if I get the partition values from a hard drive of the same size partitioned exactly the same way.
[*]Why testdisk is not finding my Linux partition? I understand that parted rescue might not find it if I don't pass the correct values.
[/LIST]

Is there some other checks I could do?

---

### Post by oldfred on 2017-01-31
I would expect testdisk to find it. Issue is probably the same with parted rescue.

Some with BIOS installs of Windows 10 were just able to use testdisk or parted rescue to restore partition and it worked.
Most had to reinstall grub (as Windows put its boot loader in MBR), some had to run e2fsck.

 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by rafaroda on 2017-02-01
Thanks for the links oldfred :)


testdisk and parted rescue did not find my Linux partitions inside my /dev/sda4 extended partition, and photorec is not finding files (just 23 useless files): is there a possibility that the content of my extended partition is gone? Is there a way to check if that happened?


Meanwhile, I'll try to do the maths to find /dev/sda5 (Ubuntu) and /dev/sda6 (Swap 4GB) which should be inside the /dev/sda4 extended partition following these links:

[LIST]
[*][https://ubuntuforums.org/showthread.php?t=1192598](https://ubuntuforums.org/showthread.php?t=1192598)
[*][http://www.rodsbooks.com/missing-parts/#hardway](http://www.rodsbooks.com/missing-parts/#hardway)
[/LIST]

My current status is:
```

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA Crucial_CT1024MX (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start       End          Size        Type      File system  Flags
 1      2048s       1026047s     1024000s    primary   ntfs         boot
 2      1026048s    987440363s   986414316s  primary   ntfs
 3      987441152s  988377087s   935936s     primary                diag
 4      988379134s  1953523711s  965144578s  extended


ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda                                   
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x1d5a0541


Device     Boot     Start        End   Sectors   Size Id Type
/dev/sda1  *         2048    1026047   1024000   500M  7 HPFS/NTFS/exFAT
/dev/sda2         1026048  987440363 986414316 470.4G  7 HPFS/NTFS/exFAT
/dev/sda3       987441152  988377087    935936   457M 27 Hidden NTFS WinRE
/dev/sda4       988379134 1953523711 965144578 460.2G  5 Extended


Partition 4 does not start on physical sector boundary.


ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda > old-parts.txt
ubuntu@ubuntu:~$ cat old-parts.txt
label: dos
label-id: 0x1d5a0541
device: /dev/sda
unit: sectors




/dev/sda1 : start=        2048, size=     1024000, type=7, bootable
/dev/sda2 : start=     1026048, size=   986414316, type=7
/dev/sda3 : start=   987441152, size=      935936, type=27
/dev/sda4 : start=   988379134, size=   965144578, type=5

```


At the beginning of BootRepair log I got this, which shows /dev/sda5 and /dev/sda6 with messed values:


```

/dev/sda1    *          2,048     1,026,047     1,024,000   7 NTFS / exFAT / HPFS
/dev/sda2           1,026,048   987,440,363   986,414,316   7 NTFS / exFAT / HPFS
/dev/sda3         987,441,152   988,377,087       935,936  27 Hidden NTFS (Recovery Environment)
/dev/sda4         988,379,134 1,953,523,711   965,144,578   5 Extended
/dev/sda5     ? 3,470,454,433 6,346,938,437 2,876,484,005  a5 FreeBSD
/dev/sda6     ? 3,446,945,920 5,772,703,833 2,325,757,914  69 Unknown

```


Complete BootRepair log:
```

Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]




============================= Boot Info Summary: ===============================


 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe


sda3: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


sda4: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''


sda6: __________________________________________________________________________


    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1,953,525,168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048     1,026,047     1,024,000   7 NTFS / exFAT / HPFS
/dev/sda2           1,026,048   987,440,363   986,414,316   7 NTFS / exFAT / HPFS
/dev/sda3         987,441,152   988,377,087       935,936  27 Hidden NTFS (Recovery Environment)
/dev/sda4         988,379,134 1,953,523,711   965,144,578   5 Extended
/dev/sda5     ? 3,470,454,433 6,346,938,437 2,876,484,005  a5 FreeBSD
/dev/sda6     ? 3,446,945,920 5,772,703,833 2,325,757,914  69 Unknown


/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda4
/dev/sda5 overlaps with /dev/sda6
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda4


"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        00E40FE9E40FE030                       ntfs       Reservado para el sistema
/dev/sda2        02881C62881C570F                       ntfs       
/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit
/dev/zram0       749f6eba-7fe8-4997-b2b1-260ddb2959eb   swap       
/dev/zram1       b6d17ab7-6e0f-4971-b793-f9fcab8bdec9   swap       
/dev/zram2       ecd6f321-3f03-441f-ad4e-a65c50c8e654   swap       
/dev/zram3       30902d00-2d93-4509-8e44-2e820b4c8294   swap       
/dev/zram4       678df62e-c868-4de3-b148-9be63f094213   swap       
/dev/zram5       b7ef2b6d-224f-4b26-9fef-bd45d9afdc93   swap       
/dev/zram6       5e14acc1-b1d4-4bf2-86a3-90f991e9fadb   swap       
/dev/zram7       3af2ee43-2532-438c-b009-355cb31bef7b   swap       


========================= "ls -l /dev/disk/by-id" output: ======================


total 0
lrwxrwxrwx 1 root root  9 Dec 13 13:02 ata-Crucial_CT1024MX200SSD1_16011167DEB1 -> ../../sda
lrwxrwxrwx 1 root root 10 Dec 13 13:02 ata-Crucial_CT1024MX200SSD1_16011167DEB1-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Dec 13 13:02 ata-Crucial_CT1024MX200SSD1_16011167DEB1-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Dec 13 13:00 ata-Crucial_CT1024MX200SSD1_16011167DEB1-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Dec 13 13:00 ata-Crucial_CT1024MX200SSD1_16011167DEB1-part4 -> ../../sda4
lrwxrwxrwx 1 root root  9 Dec 13 13:00 ata-HL-DT-ST_DVDRAM_GTC0N_KM9FB4I5458 -> ../../sr0
lrwxrwxrwx 1 root root  9 Dec 13 13:00 wwn-0x5001480000000000 -> ../../sr0
lrwxrwxrwx 1 root root  9 Dec 13 13:02 wwn-0x500a07511167deb1 -> ../../sda
lrwxrwxrwx 1 root root 10 Dec 13 13:02 wwn-0x500a07511167deb1-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Dec 13 13:02 wwn-0x500a07511167deb1-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Dec 13 13:00 wwn-0x500a07511167deb1-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Dec 13 13:00 wwn-0x500a07511167deb1-part4 -> ../../sda4


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)




======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sda4


00000000  1f bf af ae 64 9d cb 5d  8a c9 aa 81 ca b5 e5 c1  |....d..]........|
00000010  fc 5f 2f 73 4f a9 12 1d  0c f2 f6 1c 7d e6 c8 30  |._/sO.......}..0|
00000020  f7 f7 20 7e 79 52 4b a6  cc 30 e6 38 af 5e 69 a3  |.. ~yRK..0.8.^i.|
00000030  28 0d 74 4c 1b 06 f3 aa  e9 81 2d 1e f9 f1 15 d9  |(.tL......-.....|
00000040  73 c0 b5 61 12 24 01 2f  ea b5 b3 71 14 0f 43 cb  |s..a.$./...q..C.|
00000050  5b 4c 11 ee f3 27 27 d6  dd 77 08 05 41 fc 2d 0e  |[L...''..w..A.-.|
00000060  40 22 86 f0 fe d8 c5 1d  81 23 fd 0a 0b 9d 05 b5  |@".......#......|
00000070  1a 65 72 49 fc 5c 94 96  81 42 05 bd 5f c8 4e 06  |.erI.\...B.._.N.|
00000080  93 2f 38 93 6b 56 7c 98  48 5d 55 68 66 e2 08 0e  |./8.kV|.H]Uhf...|
00000090  ee 30 08 5a 4c 88 ea c5  a0 fd ae 52 eb 5a 88 9b  |.0.ZL......R.Z..|
000000a0  9d b4 f9 13 1d dd a0 04  12 a2 54 5e fa 4f bb 1b  |..........T^.O..|
000000b0  64 29 c5 90 59 dc fe bb  f6 98 59 ea 45 78 ba 35  |d)..Y.....Y.Ex.5|
000000c0  a3 56 73 95 cd e7 25 3d  11 f9 25 85 ff 18 1b 8c  |.Vs...%=..%.....|
000000d0  e2 59 82 d2 f5 9b 1b 62  e6 5b ec de 8b a4 ce a9  |.Y.....b.[......|
000000e0  e1 3f 7d f7 ac 19 09 b8  c6 f1 95 ab 92 f8 c2 f7  |.?}.............|
000000f0  f0 43 ab a4 24 6d f5 f7  f6 5d 81 79 4d 9e 95 1c  |.C..$m...].yM...|
00000100  af bd e4 f8 46 d6 e2 94  bd f8 fc 84 83 07 4f 02  |....F.........O.|
00000110  6a 07 26 e8 2d cb 3c 33  da 14 0f 40 d0 0f 97 e2  |j.&.-.<3...@....|
00000120  29 cc bf a4 a1 d4 f1 83  ba 6a 0c 4e a5 4a 06 81  |)........j.N.J..|
00000130  2c 9e b9 bc 3e 0b 57 d4  b1 c9 6c 1d 70 2c 89 df  |,...>.W...l.p,..|
00000140  f2 0a b0 3e 82 e9 4c d6  9a 36 af 0f 5c d2 c2 3e  |...>..L..6..\..>|
00000150  88 b6 f8 11 a9 87 40 0c  52 b9 80 2f c0 f4 ef 0c  |......@.R../....|
00000160  81 8f be 1d 95 b1 22 4f  94 71 8c cf 22 fd b5 4f  |......"O.q.."..O|
00000170  fc 7b 5c 94 f8 b5 bb 50  f5 0f 77 81 bd 41 e0 1e  |.{\....P..w..A..|
00000180  bd 90 a0 81 c3 e3 3b 36  62 6b c2 77 14 41 03 e6  |......;6bk.w.A..|
00000190  62 06 0f 0f 9d 7c 61 d8  99 01 e6 52 56 9e 62 20  |b....|a....RV.b |
000001a0  6c b4 80 b1 53 69 95 98  91 67 e6 26 1a dd 08 c4  |l...Si...g.&....|
000001b0  d1 c5 a0 a5 02 9a ef 10  ca 3a 14 21 f2 dd 85 7d  |.........:.!...}|
000001c0  ad e3 a5 1a 48 6b a3 76  f1 93 a5 a9 73 ab b0 1b  |....Hk.v....s...|
000001d0  af 0c 69 3d 17 4d 82 c0  8a 92 da 3f a0 8a 00 00  |..i=.M.....?....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


Unknown BootLoader on sda5




Unknown BootLoader on sda6






=============================== StdErr Messages: ===============================


hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
File descriptor 9 (/proc/3022/mounts) leaked on lvs invocation. Parent PID 9793: bash
File descriptor 63 (pipe:[28823]) leaked on lvs invocation. Parent PID 9793: bash
  No volume groups found


ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-12-13__13h01 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/3022/mounts) leaked on lvs invocation. Parent PID 4818: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- debian-installer/language=es keyboard-configuration/layoutcode?=es


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Warning: ignoring extra data in partition table 5


=================== os-prober:
/dev/sda1:Windows Recovery Environment (loader):Windows:chain


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sda1: LABEL="Reservado para el sistema" UUID="00E40FE9E40FE030" TYPE="ntfs"
/dev/sda2: UUID="02881C62881C570F" TYPE="ntfs"
/dev/zram0: UUID="749f6eba-7fe8-4997-b2b1-260ddb2959eb" TYPE="swap"
/dev/zram1: UUID="b6d17ab7-6e0f-4971-b793-f9fcab8bdec9" TYPE="swap"
/dev/zram2: UUID="ecd6f321-3f03-441f-ad4e-a65c50c8e654" TYPE="swap"
/dev/zram3: UUID="30902d00-2d93-4509-8e44-2e820b4c8294" TYPE="swap"
/dev/zram4: UUID="678df62e-c868-4de3-b148-9be63f094213" TYPE="swap"
/dev/zram5: UUID="b7ef2b6d-224f-4b26-9fef-bd45d9afdc93" TYPE="swap"
/dev/zram6: UUID="5e14acc1-b1d4-4bf2-86a3-90f991e9fadb" TYPE="swap"
/dev/zram7: UUID="3af2ee43-2532-438c-b009-355cb31bef7b" TYPE="swap"




1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.


Windows not detected by os-prober on sda2.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Warning: ignoring extra data in partition table 5


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Warning: ignoring extra data in partition table 5
=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.




=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.


sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes




=================== parted -l:




                                                                          
Error: Can't have a partition outside the disk!




                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.


                                                                          
Error: /dev/sr0: unrecognised disk label




                                                                          
Error: /dev/zram0: unrecognised disk label




                                                                          
Error: /dev/zram1: unrecognised disk label




                                                                          
Error: /dev/zram2: unrecognised disk label




                                                                          
Error: /dev/zram3: unrecognised disk label




                                                                          
Error: /dev/zram4: unrecognised disk label




                                                                          
Error: /dev/zram5: unrecognised disk label




                                                                          
Error: /dev/zram6: unrecognised disk label




                                                                          
Error: /dev/zram7: unrecognised disk label


=================== parted -lm:




                                                                          
Error: Can't have a partition outside the disk!




                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.


                                                                          
Error: /dev/sr0: unrecognised disk label




                                                                          
Error: /dev/zram0: unrecognised disk label




                                                                          
Error: /dev/zram1: unrecognised disk label




                                                                          
Error: /dev/zram2: unrecognised disk label




                                                                          
Error: /dev/zram3: unrecognised disk label




                                                                          
Error: /dev/zram4: unrecognised disk label




                                                                          
Error: /dev/zram5: unrecognised disk label




                                                                          
Error: /dev/zram6: unrecognised disk label




                                                                          
Error: /dev/zram7: unrecognised disk label




=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)




=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control


=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 9f 0f 00 00 00 00 00  |................|
00000030  aa a6 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  30 e0 0f e4 e9 0f e4 00  |........0.......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200


=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 0f 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  eb 7c cb 3a 00 00 00 00  |.........|.:....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  0f 57 1c 88 62 1c 88 02  |.........W..b...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 45 72 72 6f  |............Erro|
00000190  72 20 64 65 20 64 69 73  63 6f 00 0d 0a 42 4f 4f  |r de disco...BOO|
000001a0  54 4d 47 52 20 63 6f 6d  70 72 69 6d 69 64 6f 00  |TMGR comprimido.|
000001b0  0d 0a 50 72 65 73 2e 20  43 74 72 6c 2b 41 6c 74  |..Pres. Ctrl+Alt|
000001c0  2b 53 75 70 72 20 70 61  72 61 20 72 65 69 6e 69  |+Supr para reini|
000001d0  63 69 61 72 0d 0a 00 72  65 73 74 61 72 74 0d 0a  |ciar...restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  9b 01 b0 01 00 00 55 aa  |..............U.|
00000200


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Warning: ignoring extra data in partition table 5


=================== df -Th:


Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  7.8G   15M  7.8G   1% /
udev           devtmpfs   7.8G   12K  7.8G   1% /dev
tmpfs          tmpfs      1.6G  1.2M  1.6G   1% /run
/dev/sr0       iso9660    614M  614M     0 100% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      7.8G  8.0K  7.8G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      7.8G     0  7.8G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda1      fuseblk    500M   62M  439M  13% /mnt/boot-sav/sda1
/dev/sda2      fuseblk    471G   59G  413G  13% /mnt/boot-sav/sda2


=================== fdisk -l:


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1d5a0541


Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1026047      512000    7  HPFS/NTFS/exFAT
/dev/sda2         1026048   987440363   493207158    7  HPFS/NTFS/exFAT
/dev/sda3       987441152   988377087      467968   27  Hidden NTFS WinRE
/dev/sda4       988379134  1953523711   482572289    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5   ?  3470454433  6346938437  1438242002+  a5  FreeBSD
Partition 5 does not start on physical sector boundary.




Partition outside the disk detectado.


=================== Recommended repair
The default repair of the Boot-Repair utility will restore the [(generic mbr)] MBR in sda, and make it boot on sda2.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot




Quantity of real Windows: 1
Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
parted /dev/sda set 2 boot on


                                                                          
Error: Can't have a partition outside the disk!


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Warning: ignoring extra data in partition table 5
parted /dev/sda set 1 boot off


                                                                          
Error: Can't have a partition outside the disk!


Arranque reparado con éxito.


Ahora puede reiniciar el equipo.

```

---

### Post by oldfred on 2017-02-01
Logical partitions depend on linked list from extended to next logical, & then next logical. That is why you can have an unlimited number of logical partitions.
And each partition has the same partition table structure (PBR) as the MBR, but is just the partition start and a link to next partition.

But the Boot-Repair output is showing the PBR(s) are corrupted as they have wrong size & types. Not sure what else to suggest as if standard tools are not finding data then you do have major issues. 

[http://www.win.tue.nl/~aeb/partitions/partition_tables.html#toc3](http://www.win.tue.nl/~aeb/partitions/partition_tables.html#toc3)

As an aside, this is why I converted to gpt back in 2010. It has backup partition table. 
While Linux can boot in BIOS or UEFI from gpt, but Windows must have UEFI boot to use gpt partitioning.
In 2010 my Windows XP was on a separate MBR drive. Then it got retired, so no more MBR drives. I also use gpt on larger flash drives.

---

### Post by rafaroda on 2017-02-02
Thanks again oldfred for your help and explanations: I will try to find alternatives :)

---

### Post by oldfred on 2017-02-02
Have you tried photorec?
I have used it. It recovers anything that looks like a file, but not full filename. I had some .txt files I wanted to recover as backup was a month old.
But I had saved some of the files multiple times & it recovered all of them, even deleted ones and some partials. And sorting which was which and comparing them to backup to see which had more or newer data was a long process.
       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) 
    

 Last ditch redo superblocks:
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)
Worked for this user:
[http://ubuntuforums.org/showthread.php?t=2033778](http://ubuntuforums.org/showthread.php?t=2033778)
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)
Some additional advanced ways:
[http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/](http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/)
[http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki](http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki)

---

### Post by rafaroda on 2017-02-06
Hi oldfred, yes, I tried photorec but does not find any useful file (just 23 useless files) :(

I had a closer look at testdisk and have this message on both Search and Deep Search:
```

TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63


The harddisk (1000 GB / 931 GiB) seems too small! (< 3475 GB / 3236 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...


The following partition can't be recovered:
     Partition               Start        End    Size in sectors
>  FAT16 >32M           341072 120 46 422535 178 54 1308706758

```
[CENTER][IMG]https://ibin.co/3BTiivtBZdpU.png[/IMG]



[IMG]https://ibin.co/3BTj2I3UJP12.png[/IMG][/CENTER]



The testdisk.log shows some disk limit error, but I can't see how to fix those data in the partition table: *This partition ends after the disk limits. (start=5479329285, size=1308706758, end=6788036042, disk end=1953525168)*
```
Mon Feb  6 15:19:26 2017
Command line: TestDisk


TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 4.4.0-31-generic (#50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016) x86_64
Compiler: GCC 5.3
ext2fs lib: 1.42.13, ntfs lib: libntfs-3g, reiserfs lib: none, ewf lib: none, curses lib: ncurses 6.0
/dev/sda: LBA, LBA48 support
/dev/sda: size       1953525168 sectors
/dev/sda: user_max   1953525168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - 0 sectors, sector size=512
/dev/sr0 is not an ATA disk
Hard disk list
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - Crucial_CT1024MX200SSD1, S/N:16011167DEB1, FW:MU03
Disk /dev/sr0 - 1513 MB / 1443 MiB - 738928 sectors (RO), sector size=2048 - HL-DT-ST DVDRAM GTC0N, S/N:KM9FB4I5458, FW:1.00


Partition table type (auto): Intel
Disk /dev/sda - 1000 GB / 931 GiB - Crucial_CT1024MX200SSD1
Partition table type: Intel


Analyse Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
Geometry from i386 MBR: head=222 sector=56
NTFS at 0/32/33
NTFS at 63/221/31
check_part_i386 3 type 27: no test
check_part_i386 failed for partition type 83
Current partition structure:
 1 * HPFS - NTFS              0  32 33    63 221 30    1024000
 2 P HPFS - NTFS             63 221 31 61465  81 36  986414316
 3 P Windows RE(store)    61465  94  6 61523 160 13     935936
 4 E extended             61523 192 44 121601  57 56  965144578
No ext2, JFS, Reiser, cramfs or XFS marker
 5 L Linux                61523 192 46 121601  57 56  965144576
 5 L Linux                61523 192 46 121601  57 56  965144576


search_part()
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
NTFS at 0/32/33
filesystem size           1024000
sectors_per_cluster       8
mft_lcn                   42666
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33    63 221 30    1024000
     NTFS, blocksize=4096, 524 MB / 500 MiB
NTFS at 63/221/31
filesystem size           986414316
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             63 221 31 61465  81 36  986414316
     NTFS, blocksize=4096, 505 GB / 470 GiB
BAD_RS LBA=5479329285 15396299
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 06
     FAT16 >32M           341072 120 46 422535 178 54 1308706758
This partition ends after the disk limits. (start=5479329285, size=1308706758, end=6788036042, disk end=1953525168)
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (1000 GB / 931 GiB) seems too small! (< 3475 GB / 3236 GiB)
The following partition can't be recovered:
     FAT16 >32M           341072 120 46 422535 178 54 1308706758


Results
   * HPFS - NTFS              0  32 33    63 221 30    1024000
     NTFS, blocksize=4096, 524 MB / 500 MiB
   P HPFS - NTFS             63 221 31 61465  94  5  986415104
     NTFS, blocksize=4096, 505 GB / 470 GiB


Hint for advanced users. dmsetup may be used if you prefer to avoid to rewrite the partition table for the moment:
echo "0 1024000 linear /dev/sda 2048" | dmsetup create test0
echo "0 986415104 linear /dev/sda 1026048" | dmsetup create test1


interface_write()
 1 * HPFS - NTFS              0  32 33    63 221 30    1024000
 2 P HPFS - NTFS             63 221 31 61465  94  5  986415104


search_part()
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
NTFS at 0/32/33
filesystem size           1024000
sectors_per_cluster       8
mft_lcn                   42666
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33    63 221 30    1024000
     NTFS, blocksize=4096, 524 MB / 500 MiB
NTFS at 63/221/30
filesystem size           1024000
sectors_per_cluster       8
mft_lcn                   42666
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33    63 221 30    1024000
     NTFS found using backup sector, blocksize=4096, 524 MB / 500 MiB
NTFS at 63/221/31
filesystem size           986414316
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             63 221 31 61465  81 36  986414316
     NTFS, blocksize=4096, 505 GB / 470 GiB
BAD_RS LBA=5479329285 15396299
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 06
     FAT16 >32M           341072 120 46 422535 178 54 1308706758
This partition ends after the disk limits. (start=5479329285, size=1308706758, end=6788036042, disk end=1953525168)
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (1000 GB / 931 GiB) seems too small! (< 3475 GB / 3236 GiB)
The following partition can't be recovered:
     FAT16 >32M           341072 120 46 422535 178 54 1308706758


Results
   * HPFS - NTFS              0  32 33    63 221 30    1024000
     NTFS, blocksize=4096, 524 MB / 500 MiB
   P HPFS - NTFS             63 221 31 61465  94  5  986415104
     NTFS, blocksize=4096, 505 GB / 470 GiB


Hint for advanced users. dmsetup may be used if you prefer to avoid to rewrite the partition table for the moment:
echo "0 1024000 linear /dev/sda 2048" | dmsetup create test0
echo "0 986415104 linear /dev/sda 1026048" | dmsetup create test1


interface_write()
 1 * HPFS - NTFS              0  32 33    63 221 30    1024000
 2 P HPFS - NTFS             63 221 31 61465  94  5  986415104
simulate write!


write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition


TestDisk exited normally.

```

Regarding your suggestion to redo the superblocks [https://ubuntuforums.org/showthread.php?t=1681972&page=5&p=10434656#post10434656](https://ubuntuforums.org/showthread.php?t=1681972&page=5&p=10434656#post10434656)

Should I run this in my extended partition /dev/sda4 or my guessed Linux partition /dev/sda5?

Thanks again for your help and patience :)

---

### Post by oldfred on 2017-02-06
It looks like sda4 is just your extended partition. It does not really contain any data, just other partitions like sda5 or sda6.
You can try recovery on those partition(s).

That testdisk & photorec are not recovering anything is not a good sign. 

Did you at one time have a vendor recovery partition that was FAT32, or is testdisk just finding random data and thinking it is FAT32 partition?

---

### Post by raventhh-rs on 2017-02-27
I know it's not 'quote on quote' a good answer, but if I were you, I'd just reinstall the OS. I have to anyway because linux isn't recognizing ANY commands. like sudo :P

---

### Post by rafaroda on 2017-12-31
Hi Oldfred,

Just for your information: I sent the disk to a company that recovers this kind of situations but no luck neither, no way to recover it.

Thanks for your help and happy 2018!

---

