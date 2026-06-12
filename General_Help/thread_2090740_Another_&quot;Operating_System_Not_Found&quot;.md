---
title: "Another &quot;Operating System Not Found&quot;"
date: 2012-12-03
forum: General Help
---

### Post by Arrick on 2012-12-03
I've seen a number of threads which are tangential to this, but all seem to involve special dual operating systems, or such.  If this should be addressed in another thread, please let me know.

I am fairly computer literate, but not by any stretch a linux wizard.  I have an Ubuntu system that has been running here for about 4 years, simply as a SVN repository, and to run apache and service an internal Wiki and some web pages.   I have upgraded it periodically, and it is now at 12.04.  The system is not intended as a dual boot, it's as plain-vanilla as I can get it.

On Friday I noticed that it was suggesting some auto-updates, and without paying too much attention I let it proceed.  At the end of the process when it tried to reboot I got a blank screen with "Operating System Not Found".

I booted a Ubuntu/Live CD, and read gparted which found no problems, showing /dev/sda1 as a boot disk.  Bootinfoscript seems to show grub installed, and a bootable partition.  Output is at the end of this post.

While I have an external disk which is supposedly backing up the SVN data, zapping and reinstalling the system is my absolute last choice.  I'd appreciate any suggestions as to what to try next to recover this.

Thanks,

Al F.
```

  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   300,447,629   300,447,567  83 Linux
/dev/sda2         300,447,630   312,576,704    12,129,075   5 Extended
/dev/sda5         300,447,693   312,576,704    12,129,012  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        dc31e754-831c-48d3-a21b-ccece04452b0   ext3       
/dev/sda5        e0114744-0ac4-4711-b555-7f1b47bf30d1   swap       
/dev/sdb1        CB08-0F06                              vfat       Elements
/dev/sr0                                                iso9660    Ubuntu 12.04.1 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

```

---

### Post by dino99 on 2012-12-03
with an oldish  "rolling" system dist-upgraded again & again, lot of old settings & garbage are left behind and can aday or an other conflict with the latest config. Its the case with grub2/grub1 for example, and init/upstart, broken symlinks and ...

So experience have proved that doing a clean install after 1 or 2 dist-upgrades is a good idea to avoid such troubles. Otherwise clean the system as much as you can (deborphan & bleachbit) 

some config folders can also be removed, to get fresh new ones on reboot: .local, .gnome2, .config, .gconf

---

### Post by Arrick on 2012-12-03
If I do a fresh install from the Ubuntu/Live CD, is there any risk of losing the data on the system?  Sorry for sounding ignorant, but in this cae, I guess I am.

Thanks,

Al F.

---

### Post by oldfred on 2012-12-03
Yes a normal new install overwrites everything.

Did you try to boot from sdb for some reason. It shows Windows in MBR but you have no Windows in sdb.

You still are booting with grub legacy and the default since 9.10 has been grub2. But legacy still should work. Did you post full bootinfoscript report? It is not showing the menu.lst and other data.

I also tend to prefer clean installs but I separate data from system and install to another 25GB system partition so I still have my old install. Data stays on its partitions. It forces a good houseclean. But there is a "dirty" install that just overwrites system files. That then does not do the houseclean and overwrites all system files & settings, so if you have any custom settings those will also get overwritten.

I would try Boot-Repair you can install it to your Ubuntu liveCD.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Arrick on 2012-12-03
Reinstalling Grub via boot-repair seems to have done the trick, I can now boot and access my data.

Thank you very much for your help.

---

