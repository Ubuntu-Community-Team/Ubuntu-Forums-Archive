---
title: "Recover GRUB in case of luks encrypted LVM partitions"
date: 2015-02-24
forum: General Help
---

### Post by BankwinG on 2015-02-24
So I trying to install Windows 7 on my laptop after that it wrote over my grub. 
If you installed Windows before Ubuntu, it will work, but if you installed Windows after Ubuntu, Windows is going to overwrite the MBR of your hard disk , and GRUB is going to disappear&#8230;
All my works are on this laptop I needed to get it up and running. For anyone who in the same situation the following steps might help you to fixed it.


Insert Ubuntu live cd and select "Run Ubuntu Without Install" then start "console" by press CTRL+ALT+T or search in Dash Home


1.GET Disk information
```
#fdisk -l


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2ec136ab


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1050623      524288   83  Linux    <--------------- BOOT PARTITION
/dev/sda2         1050624   625142447   312045912   83  Linux    <--------------- CRYPT PARTITION

```

2.Create Dir to mount system
```
#mkdir /mnt/system

```

3.Decrypt Crypt Partition
```
#cryptsetup luksOpen /dev/sda2 encrypted-volume
Enter passphrase for /dev/sda2:

```

4.SCAN for VG
```
# vgscan
Reading all physical volumes. This may take a while&#8230;
Found volume group &#8220;ubuntu&#8221; using metadata type lvm2

```

5.ACTIVATE VG
```
# vgchange -ay
2 logical volume(s) in volume group &#8220;ubuntu&#8221; now active

```

6.Scan for LV
```
#lvscan
  ACTIVE            '/dev/ubuntu/swap' [7.73 GiB] inherit
  ACTIVE            '/dev/ubuntu/root' [289.86 GiB] inherit
  
  
#ls /dev/mapper/
control encrypted-volume ubuntu-root  ubuntu-swap

```


7.mount LV and the other necessary things as well (/dev/sda1 is my BOOT Partition)
```

# mount /dev/mapper/ubuntu-root /mnt/system/
# mount /dev/sda1 /mnt/system/boot/                        
# mount -o bind /dev/ /mnt/system/dev/
# mount -o bind /proc/ /mnt/system/proc/

```



8.Chroot into this system:
```
#chroot /mnt/system

```

9.Install GRUB into MBR:
```
# grub-install /dev/sda
Installation finished. No error reported.

```

10.Update grub:
```
# update-grub
Generating grub.cfg &#8230;
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /memtest86+.bin
Cannot find list of partitions!
done

```

11.Reboot
```
#reboot

```

---

### Post by th6045 on 2015-08-07
Thanks! Nearly got my boot partition back, still having issue with being dumped to initramfs prompt but this method has at least let me recover some data :p

---

### Post by richieb-3 on 2016-07-01
This worked well, thank you for posting it!
[IMG]https://cdn.meme.am/images/300x/10057088.jpg[/IMG]

---

### Post by oldos2er on 2016-07-01
Old thread closed.

---

