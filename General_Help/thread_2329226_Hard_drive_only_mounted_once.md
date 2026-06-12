---
title: "Hard drive only mounted once"
date: 2016-06-29
forum: General Help
---

### Post by Jos_Miguel on 2016-06-29
Hello! I have a problem with ubuntu 16.04 unity (it's not a hardware problem because i don't have problems in windows), when i connect a external HDD, ubuntu detects and mounts the HDD and i can access to the files without problems, but when i disconnect and reconnect the HDD, it doesn't appears in nautilus or in gparted, but when i put "lsusb" shows the HDD:

```
Bus 002 Device 004: ID 0939:0b15 Lumberg, Inc. Toshiba Stor.E Alu 2
```

But not if i put "sudo fdisk -l" 
```

Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x939fdda0

Disposit.  Inicio      Start      Final   Sectores   Size Id Tipo
/dev/sda1               2048  327682047  327680000 156,3G  7 HPFS/NTFS/exFAT
/dev/sda2  *       327682048  532482047  204800000  97,7G 83 Linux
/dev/sda3          532482048 1949331455 1416849408 675,6G  7 HPFS/NTFS/exFAT
/dev/sda4         1949331456 1953523711    4192256     2G 82 Linux swap / Solaris
```

When i connect the external HDD at first time and i do "dmesg | tail -n 20" , this appears:

```
[  699.503613] usb 2-3: new high-speed USB device number 4 using xhci_hcd
[  699.707218] usb 2-3: New USB device found, idVendor=0939, idProduct=0b15
[  699.707227] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  699.707232] usb 2-3: Product: StorE HDD
[  699.707236] usb 2-3: Manufacturer: Toshiba
[  699.707239] usb 2-3: SerialNumber: 201209251F55
[  700.269697] usb-storage 2-3:1.0: USB Mass Storage device detected
[  700.269921] scsi host4: usb-storage 2-3:1.0
[  700.270246] usbcore: registered new interface driver usb-storage
[  700.293244] usbcore: registered new interface driver uas
[  701.979626] scsi 4:0:0:0: Direct-Access     Toshiba  StorE HDD        0000 PQ: 0 ANSI: 4
[  701.981584] sd 4:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/466 GiB)
[  701.982835] sd 4:0:0:0: Attached scsi generic sg1 type 0
[  701.988462] sd 4:0:0:0: [sdb] Write Protect is off
[  701.988477] sd 4:0:0:0: [sdb] Mode Sense: 38 00 00 00
[  701.996156] sd 4:0:0:0: [sdb] No Caching mode page found
[  701.996166] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  702.024603]  sdb: sdb1
[  702.044796] sd 4:0:0:0: [sdb] Attached SCSI disk

```

If i connect the external HDD at second time, this appears:

```

[  745.629158] usb 2-1: new high-speed USB device number 6 using xhci_hcd
[  745.832552] usb 2-1: New USB device found, idVendor=0939, idProduct=0b15
[  745.832561] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  745.832565] usb 2-1: Product: StorE HDD
[  745.832569] usb 2-1: Manufacturer: Toshiba
[  745.832572] usb 2-1: SerialNumber: 201209251F55
[  745.834966] usb-storage 2-1:1.0: USB Mass Storage device detected
[  745.835183] scsi host4: usb-storage 2-1:1.0
[  768.135287] usb 2-1: reset high-speed USB device number 6 using xhci_hcd
```

Quite different than the first time

Can someone help me?

---

### Post by Bashing-om on 2016-06-29
Jos_Miguel; Hello;

I have to ask;
Are you UN-mounting the external hard drive prior to unplugging it ?

[INDENT][INDENT]it is a thing
[INDENT][INDENT][INDENT]that needs to be done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jos_Miguel on 2016-06-29
Logically, from nautilus

[IMG]http://i67.tinypic.com/5xjztz.png[/IMG]

And strangely, when i connect the HDD, a notifications saying that i have new updates appears on the screen, even if i have all updated (sometimes).

Also, i have a chromebook (which os uses the linux kernel) and i don't have this problem

Edit: What? :confused: i tried again to disconnect and connect the HDD several times and nautilus shows the HDD without problems, i am confused, since i installed ubuntu (about a week) i experienced this problem but now it's fixed (by the face???), i am surprised :???:

Edit2: It looks like that the "change boot order" option from BIOS is causing this problem, if i put "HDD/SDD" at first, i have this problem, but if i put "HDD/SDD" second and "USB" first, i can disconnect and connect the hard drive without problems

---

### Post by Liam_Murphy on 2016-06-29
Type "Disks" in Unity search

On the left, go down to your HDD, and then you can select on the individual partitions.

You should see a "play" button to mount them, and a square "stop" button to unmount. 

Do those work?

---

### Post by Bashing-om on 2016-06-29
Liam_Murphy; All to the good .

Sometimes 'buntu is magic ! It can heal it's self .

Just keep in mind to UNmount that external hard drive when you mount it .

[INDENT][INDENT]'buntu
[INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jos_Miguel on 2016-06-29
I fixed it, in boot order, if i put the HDD first, ubuntu only detect the HDD one time but when i put HDD/SDD second and USB first, i don't have this problem, it's a incompatibility with ubuntu because this doesn't happen in windows.

---

### Post by Liam_Murphy on 2016-06-29
Nice, glad you fixed it. :)

---

### Post by Bashing-om on 2016-06-30
Jos_Miguel; Hey;

As we have:
> 
when i put HDD/SDD second and USB first, i don't have this problem

I would question that the boot code is correct on the hard drive .
Booted into the install;
What returns:
```

sudo parted -l
sudo blkid -c /dev/null -o list
cat /etc/fstab
cat /boot/grub/grub.cfg

```

[INDENT][INDENT]booting is a process
[INDENT][INDENT][INDENT]has to be a reason
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jos_Miguel on 2016-06-30
I need to put those command with the external HDD connected or not?

---

### Post by Bashing-om on 2016-06-30
Jos_Miguel; Hey ;

Might proof instructional to run the commands both with and with out the external hard drive connected.

To see what grub has set for booting:
```

sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
sudo lshw -C Disk -short

```

As I do look at this as a 
[INDENT][INDENT]failure to communicate
[/INDENT][/INDENT]

---

### Post by Jos_Miguel on 2016-07-04
**Without external hardrive connected:**
sudo debconf-show grub-pc

>   grub-pc/install_devices_disks_changed:
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/install_devices_empty: false
  grub2/linux_cmdline_default: quiet splash
  grub2/kfreebsd_cmdline:
  grub-pc/timeout: 10
  grub-pc/chainload_from_menu.lst: true
  grub2/device_map_regenerated:
  grub-pc/partition_description:
  grub-pc/disk_description:
  grub2/force_efi_extra_removable: false
  grub2/linux_cmdline:
  grub-pc/kopt_extracted: false
  grub-pc/postrm_purge_boot_grub: false
* grub-pc/install_devices: /dev/disk/by-id/ata-TOSHIBA_HDWJ110_36NVTNH3T
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/hidden_timeout: true
  grub-pc/install_devices_failed: false


sudo grub-probe -t device /boot/grub

> /dev/sda2

sudo lshw -C Disk -short

> ruta H/W       Dispositivo  Clase          Descripción
=======================================================
/0/1/0.0.0     /dev/sda     disk           1TB TOSHIBA HDWJ110

** With external hardrive connected**

sudo debconf-show grub-pc
> 
  grub-pc/partition_description:
  grub-pc/disk_description:
  grub-pc/timeout: 10
  grub-pc/install_devices_empty: false
  grub-pc/kopt_extracted: false
  grub-pc/install_devices_failed: false
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_disks_changed:
  grub-pc/mixed_legacy_and_grub2: true
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
  grub2/linux_cmdline:
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/hidden_timeout: true
  grub-pc/chainload_from_menu.lst: true
  grub2/force_efi_extra_removable: false
* grub-pc/install_devices: /dev/disk/by-id/ata-TOSHIBA_HDWJ110_36NVTNH3T
  grub2/linux_cmdline_default: quiet splash
  grub-pc/install_devices_failed_upgrade: true

sudo grub-probe -t device /boot/grub

> /dev/sda2

sudo lshw -C Disk -short

> ruta H/W               Dispositivo  Clase          Descripción
===============================================================
/0/100/14/0/2/0.0.0    /dev/sdb     disk           500GB SCSI Disk
/0/1/0.0.0             /dev/sda     disk           1TB TOSHIBA HDWJ110

---

### Post by Bashing-om on 2016-07-04
Jos_Miguel; Hummm ...

In both cases above, you are booting from the Toshiba drive:
> 
* grub-pc/install_devices: /dev/disk/by-id/ata-TOSHIBA_HDWJ110_36NVTNH3T


What is the result when setting the boot priority as 1st choice of the internal hard drive (sdb in this instance, that is subject to change) AND removing the external drive ? Where the external drive is presently identified as ' sda' .

In  this condition show:
```

cat /etc/fstab
sudo blkid -c /dev/null
sudo fdisk -lu

```

As I still suspect we want to update the boot code on the internal hard drive .. maybe Windows is messing with it ???
Maybe the File System TABle is not always in a consistent state, depending on what has been set .

we will see
[INDENT][INDENT]what tale now gets told
[/INDENT][/INDENT]

---

### Post by Jos_Miguel on 2016-07-07
No, sda is the internal hard drive and sdb the external hardrive

This appears:
cat /etc/fstab

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=cb56c243-c6bd-4cc6-b98c-45fe7ec2e327 /               ext4    errors=remount-ro 0       1
# /media/datos was on /dev/sda3 during installation
UUID=133C3AE67DAA3CAF /media/datos    ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda4 during installation
UUID=99bed62d-7551-4878-b389-75b0a878a945 none            swap    sw              0       0



sudo blkid -c /dev/null

> /dev/sda1: LABEL="Windows" UUID="1E0271FE50F7B8DB" TYPE="ntfs" PARTUUID="939fdda0-01"
/dev/sda2: UUID="cb56c243-c6bd-4cc6-b98c-45fe7ec2e327" TYPE="ext4" PARTUUID="939fdda0-02"
/dev/sda3: LABEL="Datos" UUID="133C3AE67DAA3CAF" TYPE="ntfs" PARTUUID="939fdda0-03"
/dev/sda4: UUID="99bed62d-7551-4878-b389-75b0a878a945" TYPE="swap" PARTUUID="939fdda0-04"



sudo fdisk -lu

> Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x939fdda0

Disposit.  Inicio      Start      Final   Sectores   Size Id Tipo
/dev/sda1               2048  327682047  327680000 156,3G  7 HPFS/NTFS/exFAT
/dev/sda2  *       327682048  532482047  204800000  97,7G 83 Linux
/dev/sda3          532482048 1949331455 1416849408 675,6G  7 HPFS/NTFS/exFAT
/dev/sda4         1949331456 1953523711    4192256     2G 82 Linux swap / Solaris

Other mayor problem i have is that when i boot windows doing a reboot before in ubuntu, windows doesn't detect nothing USB (pendrive's, hdd's, mouse's...) and i need to reboot the computer without booting ubuntu first

---

