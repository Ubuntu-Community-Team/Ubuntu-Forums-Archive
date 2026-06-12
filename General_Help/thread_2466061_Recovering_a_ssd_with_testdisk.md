---
title: "Recovering a ssd with testdisk"
date: 2021-08-18
forum: General Help
---

### Post by Thibaud74 on 2021-08-18
Hi!

I am trying to use testdisk to recover my ubuntu session on my internal disk (mbr, swap and linux partition).
Before my disk crashed, I copied my internal ssd (laptop) to an external ssd and I was able to recreate the main partition with tesdisk, so I have good access to my data. But this time, I would like to recover on my internal ssd the three partitions, so my complete session, not only my main partition.
But the results of testdisk seem to me D. Is it possible to do this? Here is the result of testdisk after a full analysis.
```
TestDisk 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
https://www.cgsecurity.org

Disk /dev/nvme0n1 - 512 GB / 476 GiB - CHS 488386 64 32
     Partition               Start        End    Size in sectors
>D Linux                  513   0  1 488385  63 32  999163904
 D Linux Swap             649   0  1  2696  63 32    4194304
 D HPFS - NTFS          81134   0  8 140024  63 32  120608761
 D HPFS - NTFS          83922   0  1 84421  63 32    1024000
 D HPFS - NTFS          84420   0  1 84919  63 32    1024000
 D HPFS - NTFS          84429   0  1 143319  63 32  120608768
 D Linux                264133   0  1 294565  63 32   62326784
 D Linux                269761   0  1 300193  63 32   62326784
 D Linux                273838   0  1 304270  63 32   62326784
 D Linux                276651   0  1 307083  63 32   62326784
 D Linux                276906   0  1 307338  63 32   62326784
 D Linux                278952   0  1 309384  63 32   62326784
 D Linux                279207   0  1 309639  63 32   62326784
 D Linux                279462   0  1 309894  63 32   62326784
 D Linux Swap           279689   0  1 280663  63 32    1996800
 D Linux                279690   0  1 310122  63 32   62326784
 D Linux                279717   0  1 310149  63 32   62326784
 D Linux                279972   0  1 310404  63 32   62326784
 D Linux                280428   1  1 310861  63 32   62328800
 D Linux                282485   0  1 312917  63 32   62326784
 D Linux                284159   2  1 314592   1 32   62326784
 D Linux                286251   1  1 316684  63 32   62328800
 D Linux                286253   0  1 316685  63 32   62326784
 D Linux                286255   2  1 316688   1 32   62326784
 D Linux                286279   2  1 316712   1 32   62326784
 D Linux                286294   1  1 316727  63 32   62328800
 D Linux                288856   1  1 319289  63 32   62328800
 D Linux                288863   2  1 319296   1 32   62326784
 D Linux                288923   2  1 319356   1 32   62326784
 D Linux                288925   2  1 319358   1 32   62326784
 D Linux                288996   0  1 319428  63 32   62326784
 D Linux                289108   2  1 319541   1 32   62326784
 D Linux                356561   0  1 375559  63 32   38909952 [boot2docker-data]
 D Linux                372176   0  1 391174  63 32   38909952 [boot2docker-data]

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ext4 blocksize=4096 Large_file Sparse_SB, 511 GB / 476 GiB

```
Another solution would be to recreate a single partition like on my external disk, then reinstall the mbr and swap. For the swap I can use gparted with my ubuntu on usb key, but how to recreate the bootable mbr ? With a chroot ?
Finally, since hdparm told me that the internal disk was healthy, I suspect a connection problem with the NVME disk at the hardware level. I did a test with Dell at startup, here are the errors I get: [https://photos.app.goo.gl/NcUKBGw5dQt6DkkE8](https://photos.app.goo.gl/NcUKBGw5dQt6DkkE8)

---

### Post by TheFu on 2021-08-18
SSDs aren't HDDs.  There are completely different risks and issues.  If an SSD is losing data, it is going to fail.  Could be now or in a few months. Now is more likely.  The more abuse the SSD gets .... like running test disk ... the more likely it is to fail.

So, if you are willing for the SSD to fail and already have all the data you need off it, I'd say do whatever you like and may be get a few months months of use.

---

### Post by HermanAB on 2021-08-19
In terms of time wasted, it is always easier and quicker to reinstall a fresh copy of Linux and then copy your data from backup.  As for the SSD failing - they usually fail instantly and catastrophically - so you are lucky..,

---

### Post by oldfred on 2021-08-19
If installing again, I suggest using gpt partitioning whether UEFI or BIOS boot.
The only time you need MBR, now, is if installing Windows in old BIOS boot mode.

If using gpt with BIOS create a 1MB bios_grub partition with no format. If UEFI system, you need an ESP - efi system partition (FAT32 with esp,boot flags)
 Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or if drive is blank or you want to erase it.
sudo parted /dev/sda mklabel gpt

Changing a MBR drive to gpt will erase it, so if you have any data, be sure it is backed up.
You can use gdisk to convert a drive, but UUIDs all change, so then reinstall of grub & edit of fstab at minimum is required. Often better to just do new install. Conversion works better on data only drives.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by TheFu on 2021-08-19
+1 on always using GPT, unless your system doesn't support it. 

I know that the installer creates an MBR/MSDOS partition table for 20.04 and earlier by default, if we choose LVM or LUKS+LVM, so that's still an issue for many people.  21.04 appears to use gpt for those situations finally, but I can't be certain, since I've started manually partitioning outside the installer to get exactly what I desire.

---

