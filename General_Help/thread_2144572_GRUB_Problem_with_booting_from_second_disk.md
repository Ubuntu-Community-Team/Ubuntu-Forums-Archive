---
title: "GRUB: Problem with booting from second disk"
date: 2013-05-12
forum: General Help
---

### Post by wrugowski on 2013-05-12
Hi!
I have problem with booting from second disk on my laptop.

My laptop is Lenovo SL510. Originally with Fujitsu HDD and DVD drive. I was running this setup few years, and when it become too slow, I have bought SSD drive, SATA drive bay and put HDD instead of DVD drive installing SSD drive as first disk. On HDD there is Ubuntu 12.04

Then I have instaled Ubuntu 12.10 on SSD drive and was running it few months. HDD was mounted and I have used it as backup drive. Few days ago I SSD drive started to show some errors so I wanted to boot old system on HDD and when in grub screen I select 'Ubuntu 12.04' i get

No such device ID_OF_HDD
Cannot get C/H/S valuesCan not load kernel
Error messages are not exactly like these I wrote as I have them remebered.

Status is:

* both drives are shown on POST screen during laptop startup
* bios of SL510 does not have option to boot from second HDD drive (there are only HDD0 drive, ATAPI CDROM and more USB/net)
* placing HDD as first disk does not change behavior still the same messages
* FS on HDD is of course accessible when booted from SSD
* when I'm in grub rescu comand line there are only hd0 entries (hd0), (hd0,msdos1), (hd0,msdos5) no trace of hd1...

Ideally it would be able to boot 12.04 having SSD as a first drive and HDD as second. Any ideas what is wrong?

```

$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-28-generic
Found initrd image: /boot/initrd.img-3.5.0-28-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /memtest86+.bin
Found Ubuntu 12.04.2 LTS (12.04) on /dev/sdb1
done

$ sudo fdisk -l

Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b7f25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   468860927   234179585    5  Extended
/dev/sda5          501760   468860927   234179584   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5ae75c57

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   477050174   238525056   83  Linux
/dev/sdb2       477050175   488392064     5670945    5  Extended
/dev/sdb5       477050238   488392064     5670913+  82  Linux swap / Solaris

Disk /dev/mapper/sda5_crypt: 239.8 GB, 239797796864 bytes
255 heads, 63 sectors/track, 29153 cylinders, total 468355072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-root: 231.4 GB, 231378780160 bytes
255 heads, 63 sectors/track, 28130 cylinders, total 451911680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 8417 MB, 8417968128 bytes
255 heads, 63 sectors/track, 1023 cylinders, total 16441344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table

Disk /dev/mapper/cryptswap1: 8417 MB, 8417968128 bytes
255 heads, 63 sectors/track, 1023 cylinders, total 16441344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x77675bc8

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table



$ sudo blkid 
/dev/sda1: UUID="99037957-3097-40b1-bc09-39149495ead8" TYPE="ext2" 
/dev/sda5: UUID="fa45c5e3-c83b-414c-bac6-713d377c6b79" TYPE="crypto_LUKS" 
/dev/sdb1: UUID="9c0e0ea8-2a37-4c68-8ffd-7ebf9185e120" TYPE="ext3" 
/dev/mapper/sda5_crypt: UUID="uUXYXd-tosX-2G2r-DQgD-ESoT-Fn1s-L8YNki" TYPE="LVM2_member" 
/dev/mapper/ubuntu-root: UUID="b70f1388-8137-4a73-accb-b390ffe93c88" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="296a3594-1558-46ab-ab8c-5d7ead7734db" TYPE="swap" 

$ sudo parted -l
Model: ATA GOODRAM SSD (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   240GB  240GB  extended
 5      257MB   240GB  240GB  logical


Model: ATA FUJITSU MJA2250B (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  244GB  244GB   primary   ext3         boot
 2      244GB   250GB  5807MB  extended
 5      244GB   250GB  5807MB  logical


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 8418MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  8418MB  8418MB  linux-swap(v1)


Error: /dev/mapper/ubuntu-swap_1: unrecognised disk label                 

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-root: 231GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  231GB  231GB  ext4


Error: /dev/mapper/sda5_crypt: unrecognised disk label     
```

---

### Post by oldfred on 2013-05-13
I have seen several others with the HD installed in a DVD slot and not be bootable. It must just be the BIOS does not make it bootable.
But when you put it back in as main drive it should have worked.

If you do not have a live installer, download a live install and boot it, add Boot-Repair or just download the Boot-RepairCD which is just for repairs. Post link to BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

