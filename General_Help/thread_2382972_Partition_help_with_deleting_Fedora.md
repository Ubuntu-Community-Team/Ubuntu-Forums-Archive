---
title: "Partition help with deleting Fedora"
date: 2018-01-19
forum: General Help
---

### Post by sports fan Matt on 2018-01-19
I am right now running Fedora and Ubuntu and since I'm finished with Fedora, I'd like to give that space back to Ubuntu.  With the help of Boot repair and GParted, can I delete the Fedora partition?

---

### Post by oldfred on 2018-01-19
Did you let Fedora use it default LVM with separate /boot partition install or just a standard (like Ubuntu) ext4 / (root) partition?

Post this:
sudo parted -l

Also when booting are you using Ubuntu's grub or Fedora's grub. Generally last install is default grub. And that install then will be first in grub's menu with other installs at bottom. 
You need to make sure Ubuntu's grub is working before deleting other install's partitions or system will not boot.

---

### Post by sports fan Matt on 2018-01-19
Model: ATA TOSHIBA MK6475GS (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  309GB  309GB   primary   ext4            boot
 3      309GB   310GB  1074MB  primary   ext4
 4      310GB   636GB  326GB   primary                   lvm
 2      636GB   640GB  4179MB  extended
 5      636GB   640GB  4179MB  logical   linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora-home: 268GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  268GB  268GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora-swap: 4161MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  4161MB  4161MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora-root: 53.7GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  53.7GB  53.7GB  ext4

---

### Post by oldfred on 2018-01-19
You have what looks like a very large /boot partition. 
As if you installed Ubuntu into Fedora's /boot. And then maybe installs are mixed?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
But whatever you should have full backups of all your data, /home, maybe settings in /etc you manually edited and a list of installed apps to make it easy to reinstall.
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by sports fan Matt on 2018-01-23
So sorry for the late reply, my busy time of year.  Actually I shrunk my Ubuntu partition by half and added the rest to Fedora via USB. So if that's the case I installed Fedora into Ubuntu's boot? 

I can post more but can't attach for some reason.  

```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub2/grub.cfg /grub2/i386-pc/core.img

sda4: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

fedora-home: ___________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

fedora-root: ___________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Fedora 27 (Workstation Edition)
    Boot files:        /etc/fstab

fedora-swap: ___________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 596.2 GiB, 640135028736 bytes, 1250263728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   604,215,295   604,213,248  83 Linux
/dev/sda2       1,242,101,758 1,250,263,039     8,161,282   5 Extended
/dev/sda5       1,242,101,760 1,250,263,039     8,161,280  82 Linux swap / Solaris
/dev/sda3         604,215,296   606,312,447     2,097,152  83 Linux
/dev/sda4         606,312,448 1,242,099,711   635,787,264  8e Linux LVM
```

---

### Post by oldfred on 2018-01-23
Please use code tags, easy to add with Forum's advanced editor and # icon.

Looks like grub in MBR is booting Ubuntu install in sda1.

The /boot and partition containing the LVM is then Fedora.

---

