---
title: "Old Disk partition info seems to remain"
date: 2007-04-01
forum: General Help
---

### Post by woodgdo1 on 2007-04-01
I have a unique setup of Edgy and WinXP in that I have the ability to boot into my physical WinXP install from Ubuntu, and now I want to setup the vice-versa. In order to make this work, I have applied a disk label and UUID to my root partition, and configured grub to boot from it. The only problem is that this isn't working. 

From some diagnostics that I have been performing, It looks like my old Fedora LVM info is stuck on the disk still, and the install of Edgy never cleaned it up.

vol_id output of root partition
```

sudo vol_id /dev/sda2
Password:
ID_FS_USAGE=raid
ID_FS_TYPE=LVM2_member
ID_FS_VERSION=LVM2 001
ID_FS_UUID=
ID_FS_LABEL=
ID_FS_LABEL_SAFE=

```

e2label output of root partition
```

e2label /dev/sda2
root

```

lshal output
```

udi = '/org/freedesktop/Hal/devices/volume_part2_size_15578680320'
  info.udi = '/org/freedesktop/Hal/devices/volume_part2_size_15578680320'  (string)
  volume.partition.msdos_part_table_type = 131  (0x83)  (int)
  info.product = 'Volume (LVM2_member)'  (string)
  volume.size = 15578680320  (0x3a08fcc00)  (uint64)
  volume.num_blocks = 30427110  (0x1d047e6)  (int)
  volume.block_size = 512  (0x200)  (int)
  volume.partition.number = 2  (0x2)  (int)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_mounted = true  (bool)
  volume.mount_point = '/'  (string)
  volume.label = ''  (string)
  volume.uuid = ''  (string)
  volume.fsversion = 'LVM2 001'  (string)
  volume.fsusage = 'raid'  (string)
  volume.fstype = 'LVM2_member'  (string)
  storage.model = ''  (string)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS541080G9AT00_MPB4PAX6J'  (string)
  block.is_volume = true  (bool)
  block.minor = 2  (0x2)  (int)
  block.major = 8  (0x8)  (int)
  block.device = '/dev/sda2'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_1ATA_Hitachi_HTS541080G9AT00_MPB4PAX6J'  (string)
  linux.sysfs_path_device = '/sys/block/sda/sda2'  (string)
  linux.sysfs_path = '/sys/block/sda/sda2'  (string)

```
fdisk -l output
```

fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3858    30989353+   7  HPFS/NTFS
/dev/sda2            3859        5752    15213555   83  Linux
/dev/sda3            5753        5999     1984027+   5  Extended
/dev/sda4            6000        9729    29961225   83  Linux
/dev/sda5            5753        5999     1983996   82  Linux swap / Solaris

```


If anyone knows how to non-destructively fix this partition table/e2fsprogs issue, I am all ears...

Basically I want a grub statement that is not dependent on /dev nodes, as if I boot my physical Ubuntu in Windows VMware, grub will only load if I configure it as IDE. Interestingly enough, grub works fine booting Windows in Vmware from Linux...

I am such a geek for wanting to do this, but hey, it works great already booting the Physical Windows install.

---

### Post by woodgdo1 on 2007-04-02
Well, I can get everything to work if I manually configure grub to boot it, but I would eventually like to make this as dynamic as possible without destroying my / partition. I suppose I could make a dump of the filesystem, write zero's to the first 1024 bytes of the partition to ensure it is nice and clean, then run a mkfs.ext3 and restore my dump...

There are two reasons this currently doesn't work. One is the corrupt disk partition info that is sitting around. The other is the fact that I use a SATA controller in my laptop. For some reason, Vmware in Windows( and possibly Windows itself) masks the sata controller as an IDE one, thus an ide devnode when booting into vmware ubuntu. However Linux sees it as sata and assigns it a SCSI devnode. 

By the way, as a side note, to make Vmware Server's vmware-tools work in Edgy better, you need to symlink the /usr/lib/vmware-tools/configurator/XOrg/7.0/vmmouse_drv.so to /usr/lib/xorg/modules/input/. One word of caution though, do not symlink the vmware_drv.so to /usr/lib/xorg/modules/drivers/ since it seems to be incompatible with Xorg 7.1. Use the native Ubuntu video driver. 

Also, one cool thing is that when I boot into Ubuntu natively, the vmware-tools package seems to symlink /etc/X11/xorg.conf to /etc/X11/xorg.conf.BeforeVMwareToolsInstall, and when booting Ubuntu via vmware, it symlinks it to /etc/X11/xorg.conf.AfterVMwareToolsInstall. No messing around with xorg every reboot is definitely nice.

---

