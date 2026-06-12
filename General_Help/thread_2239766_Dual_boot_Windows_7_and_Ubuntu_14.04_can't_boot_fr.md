---
title: "Dual boot Windows 7 and Ubuntu 14.04 can't boot from Windows"
date: 2014-08-15
forum: General Help
---

### Post by bizhat on 2014-08-15
Hi,

I have dual boot between Windows 7 and Ubuntu 14.04.

Today i run apt-get upgrade and it installed grub update. Now i can't boot from Windows installation.

Bootrepair is not helping, my boot repair file is 

[http://paste.ubuntu.com/8056258/](http://paste.ubuntu.com/8056258/)

My partitions are

```

boby@fwhlin:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc5       243G   89G  142G  39% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           596M  1.6M  595M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.0G  220K  3.0G   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sdc1       245G   43G  202G  18% /mnt/drive_c
/dev/sda1       928G  593G  336G  64% /home/boby/disks/drive_d
/dev/sda2       928G  696G  233G  75% /home/boby/disks/backup
/dev/sdb3       1.7T   37G  1.5T   3% /home/boby/disks/part_data
boby@fwhlin:~$ 

```

/dev/sdc1 is where Windows installed. Ubuntu also installed on same drive.

How do i get Windows 7 back ?

Thanks,

Boby

---

### Post by oldfred on 2014-08-15
It is only because you have two issues that you can currently boot Ubuntu.
You rarely install grub to a partition boot sector or PBR as it does not fully fit and has to convert to blocklists which are hard coded addresses. Those addresses can easily change with updates forcing a repair reinstall of grub from a live installer.
And you never install grub2's boot loader to a NTFS PBR as that has essential Windows boot code. A Windows boot loader boots from the MBR to the PBR to boot Windows. But you have grub installed to the Windows PBR which does let you boot Ubuntu but never Windows.

Windows does keep a backup of the PBR, and if only installed once, you should be able to easily restore the backup with testdisk. But if that does not work then you need a Windows repair flash drive. And after using testdisk you will need to reinstall grub to the MBR to boot.

You could first install grub to the MBR of sdb, so you could boot Ubuntu without the repair flash drive. But usually better to have grub in MBR of same drive as Windows. Note that sdb is a gpt partitioned drive, but with bios_grub partition, grub still should install correctly.

You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

You also somehow converted sda to dynamic partitions as seen with fdisk as SFS. That does not work with Linux and not even with all Windows tools. Better to convert back to basic, but Windows will not do that. Third party Windows repair tools should work.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

            EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

Since you have several drives, generally better to have Windows on one drive and Ubuntu on another drive. While Windows only boots from gpt partitioned drives with UEFI, Ubuntu will boot in BIOS mode from a gpt drive as long as you have the bios_grub partition. I also suggest if newer system or drive may be moved to newer system best to also include an efi partition at beginning of drive for future UEFI use.

Do not run auto fix from Boot-Repair as that will always just install grub to the MBR on every drive. Typically with mulitple drives you want different boot loaders in each drive.

---

### Post by bizhat on 2014-08-16
Thank you very much for the very informative reply. I will go through the links and tools you provided.

> **oldfred said:**
> 
You could first install grub to the MBR of sdb, so you could boot Ubuntu without the repair flash drive. But usually better to have grub in MBR of same drive as Windows. Note that sdb is a gpt partitioned drive, but with bios_grub partition, grub still should install correctly.



I partitioned /dev/sdb so that in future i can install Ubuntu on this disk. Then set BIOS to boot from this disk, so it work with out messing with windows install. Windows i rarely use and usage will go down in fture, so i can press F8 key and select the Win disk and boot from it as required. 

So when i re-install Ubuntu, i install it on /dev/sdb, then grub will only get installed in /dev/sdb and Windows MBR will be safe ?

> **oldfred said:**
> 
You also somehow converted sda to dynamic partitions as seen with fdisk as SFS.


This is because i was using 2 * 2 TB disks in Windows Software RAID 1 before installing Ubuntu. When i get comfortable with Ubuntu, i removed one of the 2 TB disk from Windows Raid, formatted it for the use of future Ubuntu installation. I done some search, found it need some grub partition and set it up. I will look into efi partition too. I don't think my motherboard will support UEFI now (Asus Sabertooth X58).

For now, i got the problem fixed by editing /boot/grub/grub.cfg

Find

```

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sdc1)' --class windows --class os $menuentry_id_option 'osprober-chain-E0EA12E0EA12B2B0' {
    insmod part_msdos
    insmod ntfs
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  E0EA12E0EA12B2B0
    else
      search --no-floppy --fs-uuid --set=root E0EA12E0EA12B2B0
    fi
    parttool ${root} hidden-
    chainloader +1
}

```

Replaced With

```

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sdc1)' --class windows --class os $menuentry_id_option 'osprober-chain-E0EA12E0EA12B2B0' {
    insmod part_msdos
    insmod ntfs
        insmod ntldr
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  E0EA12E0EA12B2B0
    else
      search --no-floppy --fs-uuid --set=root E0EA12E0EA12B2B0
    fi
    parttool ${root} hidden-
        ntldr ($root)/bootmgr
}
```

Changes are 

"insmod ntldr" added after " insmod ntfs", 

"chainloader +1" replaced with  "ntldr ($root)/bootmgr"


Thanks again for the help.

---

### Post by oldfred on 2014-08-16
I think I had a typo, as it is always better to have each systems boot loader in the same drive as its install.

So is ntldr ($root)/bootmgr entry working even with the grub in the PBR of Windows? I have seen this as the newer way to specify the boot rather than the chain entry to the PBR. Essentially the Windows PBR has reference to the bootmgr (or with XP ntldr)  to boot Windows, but it also has other info that a chkdsk will try to update and if grub is in the PBR Windows will not recognize it as a NTFS partition.

Some info on partitioning, but it varies depending on what you want to use system for.
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

