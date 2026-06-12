---
title: "How to make visible a second internal hdd"
date: 2019-08-19
forum: General Help
---

### Post by salvo27sf on 2019-08-19
Hello, I aks for your help. 

I'm facing with a pc that has an sdd and an hdd working with Windows10 (s.o. installed on the sdd and files/documents/programs saved on the hdd). After an electric black-out Windows had difficult to start and did not manage anymore to access hdd and to work properly.

The idea was to use Ubuntu 19 live to try to rescue and backup hdd's files.

From "Other devices" in Ubuntu i can see ssd and read the files saved in it but the hdd is not visible.

So I launched *sudo fdisk -l*
```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1,9 GiB, 2027323392 bytes, 3959616 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 89,3 MiB, 93581312 bytes, 182776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 53,7 MiB, 56315904 bytes, 109992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 151 MiB, 158343168 bytes, 309264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 4 MiB, 4218880 bytes, 8240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 14,8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 1008 KiB, 1032192 bytes, 2016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop7: 3,7 MiB, 3821568 bytes, 7464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 119,2 GiB, 128035676160 bytes, 250069680 sectors
Disk model: SAMSUNG SSD 830 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7521ee3d


Dispositivo Avvio     Start      Fine   Settori   Size Id Tipo
/dev/sda1   *          2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2            206848 248971126 248764279 118,6G  7 HPFS/NTFS/exFAT
/dev/sda3         248971264 250064895   1093632   534M 27 Hidden NTFS WinRE




Disk /dev/sdb: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000VX000-9YW1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xa10a2849


Dispositivo Avvio Start       Fine    Settori   Size Id Tipo
/dev/sdb1          2048 1953521663 1953519616 931,5G  7 HPFS/NTFS/exFAT




Disk /dev/loop8: 35,3 MiB, 37027840 bytes, 72320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

And then *[FONT=Arial] sudo parted -l[/FONT]*

```
[FONT=Arial]ubuntu@ubuntu:~$ sudo parted -l[/FONT]
[FONT=Arial]Modello: ATA SAMSUNG SSD 830 (scsi)[/FONT]
[FONT=Arial]Disco /dev/sda: 128GB[/FONT]
[FONT=Arial]Dimensione del settore (logica/fisica): 512B/512B[/FONT]
[FONT=Arial]Tabella delle partizioni: msdos[/FONT]
[FONT=Arial]Flag del disco: [/FONT]

[FONT=Arial]Numero  Inizio  Fine   Dimensione  Tipo     File system  Flag[/FONT]
[FONT=Arial] 1      1049kB  106MB  105MB       primary  ntfs         avvio[/FONT]
[FONT=Arial] 2      106MB   127GB  127GB       primary  ntfs[/FONT]
[FONT=Arial] 3      127GB   128GB  560MB       primary  ntfs         diag[/FONT]


[FONT=Arial]Modello: ATA ST1000VX000-9YW1 (scsi)[/FONT]
[FONT=Arial]Disco /dev/sdb: 1000GB[/FONT]
[FONT=Arial]Dimensione del settore (logica/fisica): 512B/4096B[/FONT]
[FONT=Arial]Tabella delle partizioni: msdos[/FONT]
[FONT=Arial]Flag del disco: [/FONT]

[FONT=Arial]Numero  Inizio  Fine    Dimensione  Tipo     File system  Flag[/FONT]
[FONT=Arial] 1      1049kB  1000GB  1000GB      primary  ntfs[/FONT]


[FONT=Arial]Avviso: Impossibile aprire /dev/sr0 in lettura-scrittura (File system in sola[/FONT]
[FONT=Arial]lettura). /dev/sr0 è stato aperto in sola lettura.[/FONT]
[FONT=Arial]Modello: HL-DT-ST DVDRAM GH22NS70 (scsi)                                  [/FONT]
[FONT=Arial]Disco /dev/sr0: 2097MB[/FONT]
[FONT=Arial]Dimensione del settore (logica/fisica): 2048B/2048B[/FONT]
[FONT=Arial]Tabella delle partizioni: mac[/FONT]
[FONT=Arial]Flag del disco: [/FONT]

[FONT=Arial]Numero  Inizio  Fine    Dimensione  File system  Nome   Flag[/FONT]
[FONT=Arial] 1      2048B   6143B   4096B                    Apple[/FONT]
[FONT=Arial] 2      2082MB  2086MB  3834kB                   EFI[/FONT]
```

Now, what can I do to make visible the hdd and rescue the files?

Thank you!

---

### Post by TheFu on 2019-08-19
If the file systems weren't really closed, then Ubuntu can't see them.  Windows leaves file systems open as a way to make booting "seem" faster.  Look up "fast boot" on some Windows forums. [https://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/](https://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/) explains more.  I don't know if this is the issue or not, just my first guess.

If the files are on /dev/sdb1 , why not just mount it?  Is this a trick question?  That's the 1st partition on the 2nd HDD and both fdisk and parted are showing it.  [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)  It is just 3 commands:
```
mkdir /mnt/tmp  # create a mount point (empty directory)
# mount the ntfs partition to the mount point, change the uid to your userid
sudo mount -t ntfs     -o uid=salvo27sf,big_writes          /dev/sdb1        /mnt/tmp
# access the files as you like from Ubuntu/Linux

# when you finish, be certain to un-mount it or bad things are likely.
sudo umount   # yes, that is the correct command. 

```

Or you can use those backups that we all have because everyone tells us we should ;)

---

### Post by salvo27sf on 2019-08-20
Hello, thank you for help, I'm a noob!

So I tried your solution but:
```
[FONT=Arial]ubuntu@ubuntu:~$ sudo mkdir /mnt/tmp[/FONT]
[FONT=Arial]ubuntu@ubuntu:~$ sudo mount -t ntfs  -o uid=999,big_writes  /dev/sdb1[/FONT]
[FONT=Arial]mount: /dev/sdb1: can't find in /etc/fstab.
[/FONT]
```

So I tried with this other one:
```
[FONT=Arial]ubuntu@ubuntu:~$ sudo mkdir /mnt/mydrive[/FONT]
[FONT=Arial]ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt/mydrive[/FONT]
[FONT=Arial]mount: /mnt/mydrive: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error.[/FONT]
```

Then with this:
```
[FONT=Arial]ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sdb1 /mnt/mydrive[/FONT]
[FONT=Arial]ntfs_attr_pread_i: ntfs_pread failed: Errore di input/output[/FONT]
[FONT=Arial]Failed to read $MFTMirr: Errore di input/output[/FONT]
[FONT=Arial]Failed to mount '/dev/sdb1': Errore di input/output[/FONT]
[FONT=Arial]NTFS is either inconsistent, or there is a hardware fault, or it's a[/FONT]
[FONT=Arial]SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows[/FONT]
[FONT=Arial]then reboot into Windows twice. The usage of the /f parameter is very[/FONT]
[FONT=Arial]important! If the device is a SoftRAID/FakeRAID then first activate[/FONT]
[FONT=Arial]it and mount a different device under the /dev/mapper/ directory, (e.g.[/FONT]
[FONT=Arial]/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation[/FONT]
[FONT=Arial]for more details.[/FONT]
```

And with ntfsfix:
```
[FONT=Arial]ubuntu@ubuntu:~$ sudo ntfsfix /dev/sdb1[/FONT]
[FONT=Arial].Mounting volume... ntfs_attr_pread_i: ntfs_pread failed: Input/output error[/FONT]
[FONT=Arial]Failed to read $MFTMirr: Input/output error[/FONT]
[FONT=Arial]FAILED[/FONT]
[FONT=Arial]Attempting to correct errors... [/FONT]
[FONT=Arial]Processing $MFT and $MFTMirr...[/FONT]
[FONT=Arial]Reading $MFT... OK[/FONT]
[FONT=Arial]Reading $MFTMirr... ntfs_attr_pread_i: ntfs_pread failed: Input/output error[/FONT]
[FONT=Arial]FAILED[/FONT]
[FONT=Arial]Failed to read $MFTMirr: Input/output error[/FONT]
```


With the "chkdsk" command on Windows I do not have more luck: “The type of the File System is RAW”


Do you have more idea?

---

### Post by oldfred on 2019-08-20
Windows has essential boot & partition size info in the PBR - partition boot sector (even if not bootable). RAW means that info is all missing, as if it has never been formatted.

NTFS does keep a backup of the PBR, Some Windows tools & testdisk can restore backup if it is valid. You may still need chkdsk after recovery of backup.

       [http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)
PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

---

