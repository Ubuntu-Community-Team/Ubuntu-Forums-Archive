---
title: "update-grub2 error:invalid volume"
date: 2019-09-01
forum: General Help
---

### Post by tomdean@speakeasy.org on 2019-09-01
update-grub2 has started showing lots of error messages.  How do I either fix this or find out what is causing the error messages?

```

update-grub2
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-58-generic
Found initrd image: /boot/initrd.img-4.15.0-58-generic
Found linux image: /boot/vmlinuz-4.15.0-29-generic
Found initrd image: /boot/initrd.img-4.15.0-29-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
Found Ubuntu 18.04.3 LTS (18.04) on /dev/sdb2
error: invalid volume.
error: invalid volume.
error: invalid volume.
Found Windows 7 on /dev/sdc1
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.
error: invalid volume.

```

fdisk seems happy with all the disks.

```

fdisk -l
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x51e40634

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    976895    974848   476M 83 Linux
/dev/sda2          976896 200976383 199999488  95.4G 83 Linux
/dev/sda3       200976384 264976383  64000000  30.5G 82 Linux swap / Solaris
/dev/sda4       264976384 976771071 711794688 339.4G 83 Linux


Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x49598911

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1            2048    976656    974609 475.9M  b W95 FAT32
/dev/sdb2  *       976896 352538623 351561728 167.7G 83 Linux
/dev/sdb3       352538624 391600127  39061504  18.6G 82 Linux swap / Solaris
/dev/sdb4       391600128 976771071 585170944   279G 83 Linux


Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x228391b1

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdc1              63      2047      1985 992.5K 42 SFS
/dev/sdc2  *         2048    206847    204800   100M 42 SFS
/dev/sdc3          206848 976769023 976562176 465.7G 42 SFS
/dev/sdc4       976769024 976771119      2096     1M 42 SFS


Disk /dev/sdd: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x90909090

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdd1        2048 976773119 976771072 465.8G 83 Linux


Disk /dev/sde: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5da1783e

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sde1              63      2047      1985 992.5K 42 SFS
/dev/sde2  *         2048    206847    204800   100M 42 SFS
/dev/sde3          206848 976769023 976562176 465.7G 42 SFS
/dev/sde4       976769024 976771119      2096     1M 42 SFS

```

---

### Post by oldfred on 2019-09-01
You have dynamic disks. Seen in Linux as SFS.
```
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdc1              63      2047      1985 992.5K 42 [COLOR=#ff0000]SFS[/COLOR]

```

It used to be that Linux driver would not see dynamic partitions at all.
Now they seem to see them and may partially work. Grub does not work, so I believe that is the error.

Linux uses for the old BIOS/MBR configuration the 4 primary partitions with one primary converted to an extended partition.
Then you can have an unlimited number of logical partitions inside the extended.
Sometimes Windows convert to dynamic partitions.

 [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) 
   Other options also Aomei or even testdisk if only 4 dynamic partitions:
[http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)

---

### Post by tomdean@speakeasy.org on 2019-09-02
The problem turned out to be a non-existing swap partition.  etc/fstab had an entry for swap on dev/sdc.  dev/sdc has been converted to a one partition data disk!

---

