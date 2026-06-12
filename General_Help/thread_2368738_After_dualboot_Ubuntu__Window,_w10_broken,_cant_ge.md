---
title: "After dualboot Ubuntu / Window, w10 broken, cant get my old data"
date: 2017-08-14
forum: General Help
---

### Post by abra44 on 2017-08-14
Hello,

Few days ago, i have installed Ubuntu on my laptop (w10 was on it).
Once ubuntu installed, laptop continue to boot on w10, so i follow some tuto without thinking and now i can only boot on ubuntu and no longer on w10.

When i try, i have this error message :
Windows has failed to start
...
File: nst/nst_linux.mbr

I tried many solution, boot-repair usb flash drive with w10 on it, and others but no one works.

So now i kinda give up repair my windows 10 boot (if you have any idea, i take it).

I want to get my old data and after i could try to reinstall the all thing.

So there is the result :
```

guillaume@guillaume-PC:/mnt/sda1$ sudo mount /dev/sda2 /mnt/sda2
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

fdisk -l
```

guillaume@guillaume-PC:/mnt/sda1$ sudo fdisk -l
[...]
Disque /dev/sda : 465,8 GiB, 500107862016 octets, 976773168 secteurs
Unités : sectors of 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xdb261e86

Périphérique Amorçage     Start       Fin  Secteurs   Size Id Type
/dev/sda1    *             2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2                206848 936771583 936564736 446,6G  7 HPFS/NTFS/exFAT
/dev/sda3             946774016 976771071  29997056  14,3G 83 Linux
/dev/sda4             936773632 946774015  10000384   4,8G 82 partition d'échange Linux / Solaris

Partition table entries are not in disk order.

```

sudo blkid
```

guillaume@guillaume-PC:/mnt/sda1$ sudo blkid
/dev/sda1: LABEL="RM-CM-)servM-CM-) au systM-CM-(me" UUID="1A8065B380659653" TYPE="ntfs" PARTUUID="db261e86-01"
/dev/sda3: UUID="b01e65c0-15ef-4d1a-8d9e-487b8591bc53" TYPE="ext4" PTTYPE="dos" PARTUUID="db261e86-03"
/dev/sda4: UUID="e758f2f5-f477-4e18-b471-04c9343a2ad1" TYPE="swap" PARTUUID="db261e86-04"
/dev/sda2: PARTUUID="db261e86-02"

```

sudo file -s
```

guillaume@guillaume-PC:/mnt/sda1$ sudo file -s /dev/sda2
/dev/sda2: DOS/MBR boot sector

```

When i try to change type of partition :
```

guillaume@guillaume-PC:/mnt/sda1$ sudo fdisk /dev/sda2

Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Commande (m pour l'aide) : t
Numéro de partition (1-4, 4 par défaut) : 1
Partition type (type L to list all types): 87

Changed type of partition 'NTFS volume set' to 'NTFS volume set'.

Commande (m pour l'aide) : t
Numéro de partition (1-4, 4 par défaut) : 2
Partition type (type L to list all types): 87

Changed type of partition 'NTFS volume set' to 'NTFS volume set'.

Commande (m pour l'aide) : t
Numéro de partition (1-4, 4 par défaut) : 3
Partition type (type L to list all types): 87

Changed type of partition 'NTFS volume set' to 'NTFS volume set'.

Commande (m pour l'aide) : t
Numéro de partition (1-4, 4 par défaut) : 4
Partition type (type L to list all types): 87

Changed type of partition 'NTFS volume set' to 'NTFS volume set'.

Commande (m pour l'aide) : w
The partition table has been altered.
Calling ioctl() to re-read partition table.
Re-reading the partition table failed.: Argument invalide

The kernel still uses the old table. The new table will be used at the next reboot or after you run partprobe(8) or kpartx(8).

```

Sorry for my poor english and thanks for any help.

Best Regards,

Abra.

---

### Post by oldfred on 2017-08-14
If code or text output like from terminal, please copy & paste to forum. Best to use code tags to preserve formatting. Easy to add code tags with Forum's Advanced editor & # icon.

Did you turn off Windows 10's always on hibernation or fast boot. Especially with BIOS boot versions you will continue to have various boot issues. Windows on larger updates will reinstall its boot loader to MBR and turn fast start back on.
Grub only boots working Windows. And that means it cannot be hibernated nor need chkdsk. You will always need both Ubuntu live installer & Windows repair flash drive to fix issues, if you do not correct them before shutting down.
You may now need to temporarily reinstall a Windows boot loader to MBR, turn off fast start up, and otherwise fix Windows. Then restore grub boot loader to MBR.

 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 


       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by abra44 on 2017-08-14
I correct my original thread for the output text.

So i try to repair with boot-repair, but doesn't work, when i restore MBR, my laptop display black screen with just MBR 23FA.
I don't know what is hibernation or fast boot.
When i boot on a usb flash drive with w10 on it, i can't repair my installation (different error message).


I think there is no hope to repair the boot menu ..
But how can i mount my disk ? to get my data back and reinstall w10 totally ?

---

### Post by leunam12 on 2017-08-14
```
mount -t ntfs-3g /dev/sda2 /mnt/sda2
```

---

### Post by oldfred on 2017-08-14
The Linux NTFS driver does not mount read/write if hibernated or needs chkdsk.

You may be able to mount read only. 

Slight adjustment to leunam12's suggestion to add read only parameter.

 sudo mount -t ntfs-3g -o ro /dev/sda2 /media/windows 

Threads posted above all all about Windows 8 or 10 fast start up or hibernation.

If Boot-Repair cannot see the NTFS partition it may not offer to install a Windows type boot loader.
You can manually add a Windows boot loader and then see if f8 gets you into the internal repair console. But Windows repair or install disk in its repair console should also work.

This adds the syslinux boot loader to MBR which is a Windows type boot loader. Boot flag must be on the NTFS partition. Do not install all of syslinux, we just want the boot loader in the MBR.
      
 sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

---

### Post by abra44 on 2017-08-14
Mount with arguments doesn't work either.
```

guillaume@guillaume-PC:~$ sudo mount -t ntfs-3g /dev/sda2 /mnt/sda2
NTFS signature is missing.
Failed to mount '/dev/sda2': Argument invalide
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

```

guillaume@guillaume-PC:~$ sudo mount -t ntfs-3g -o ro /dev/sda2 /mnt/sda2
NTFS signature is missing.
Failed to mount '/dev/sda2': Argument invalide
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

I already try that and doen't work, i try again and take a picture
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

For 2nd line i must add :
sudo dd if=/usr/lib/syslinux**/mbr**/mbr.bin of=/dev/sda

So there is the result :
[IMG]http://i.imgur.com/ET3DeIg.jpg[/IMG]

For getting back to ubuntu, i must boot on live flashdrive, install boot-repair and i can boot again on ubuntu, never w10.

If i boot with w10 usb flash drive, i can launch things but nothing works, i tried to use bootrec.exe with /FixMbr /FixBoot and the other option but same result

---

### Post by oldfred on 2017-08-14
You get same error message from the Linux NTFS driver is NTFS is now unformatted, or hibernated or needs chkdsk.
If you installed grub to NTFS partition then it becomes unformatted as NTFS has to have its signature in the PBR - partition boot sector.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by abra44 on 2017-08-14
I already use ppa version for boot-repair. When i said live flash drive i meant Ubuntu live flash drive.
Here is the boot info result :
[https://pastebin.com/m3Bn6DYj](https://pastebin.com/m3Bn6DYj)

---

### Post by oldfred on 2017-08-14
It looks like NTFS boot sector is totally missing or corrupt. 
In some places it sees it as type 07, NTFS and others just blank.

I might see if the backup boot sector is valid, you can use test disk in Linux to restore a backup.
       You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

If that does not work you need to use bootsect.exe from a Windows repair disk.
       
 [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

