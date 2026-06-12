---
title: "/boot full?"
date: 2017-09-05
forum: General Help
---

### Post by rufuslucky on 2017-09-05
Lately I have had to do a series of reinstalls because I have been getting update errors say that my /boot extension was full. This last install I designated 50mg on my M2 SSD as /boot. When I check properties on that drive and the /boot file extension on that drive it tells me it still has 41.5 GB of free space left. However, when I use the disk usage analyze it's telling me that the drive I designated during installation as /boot is not the same thing as my /boot file extension, and it is telling me that my /boot file extension is full with a measly 461.8mb in it. Anybody got an idea what is going  on here and why my /boot file extension thinks it's limited to such a paltry volume? Is there a way for me to designate more space to that /boot file extension without reinstalling ubuntu? Also if I am not using the correct terminology let me know I'll try and be more specific. 

Thanks Rufus

---

### Post by oldos2er on 2017-09-05
It should be called /boot partition,  or just /boot.

Can you post the output of ```
df -h 
```

---

### Post by oldfred on 2017-09-05
Please post these, so we can be clear on which partition is which:
sudo parted -l
cat /etc/fstab
df -h

What brand/model system?
UEFI or BIOS install. UEFI has an ESP - efi system partition which has a boot flag (with gparted) but is not otherwise an Ubuntu boot partition.
Most desktop installs do not have a separate /boot partition, but servers & LVM or LVM with full drive encryption may have a /boot partition.

---

### Post by rufuslucky on 2017-09-05
```
:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                          16G     0   16G   0% /dev
tmpfs                        3.2G  9.7M  3.2G   1% /run
/dev/mapper/ubuntu--vg-root  203G  9.1G  184G   5% /
tmpfs                         16G   35M   16G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                         16G     0   16G   0% /sys/fs/cgroup
/dev/sdd1                    472M  443M  4.6M  99% /boot
tmpfs                        3.2G   96K  3.2G   1% /run/user/1000
/dev/sdc2                     46G  4.7G   39G  11% /media/rufuslucky/cffac0cc-cd4e-4aa4-93d6-2b5c89d8d7be
/dev/sdc3                    356G   67M  338G   1% /media/rufuslucky/3fb10142-5fd5-4ff6-aa95-ca4b8566759e
```

```
:~$ sudo parted -l
Error: /dev/sda: unrecognised disk label
Model: ATA WDC WD3000HLHX-6 (scsi)                                        
Disk /dev/sda: 300GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Model: ATA WDC WD1002F9YZ-0 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  512MB   511MB   primary                boot
 2      513MB   1000GB  1000GB  extended
 5      513MB   1000GB  1000GB  logical


Model: ATA Crucial_CT525MX3 (scsi)
Disk /dev/sdc: 525GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  37.0GB  37.0GB  linux-swap(v1)
 2      37.0GB  87.0GB  50.0GB  ext4
 3      87.0GB  475GB   388GB   ext4


Model: ATA SAMSUNG MZHPV256 (scsi)
Disk /dev/sdd: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  512MB  511MB  primary   ext2         boot
 2      513MB   256GB  256GB  extended
 5      513MB   256GB  256GB  logical


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 221GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  221GB  221GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 34.2GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  34.2GB  34.2GB  linux-swap(v1)


Error: /dev/mapper/sda5_crypt: unrecognised disk label
Model: Linux device-mapper (crypt) (dm)                                   
Disk /dev/mapper/sda5_crypt: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown

```
cat/etc/fstab? I don't get any output from that command. 

```
description: Motherboard
       product: Z170-E
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev 1.xx
       serial: 151158031301244
       slot: Default string
description: Motherboard
       product: Z170-E
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev 1.xx
       serial: 151158031301244
       slot: Default string
 configuration: cores=4 enabledcores=4 threads=4
     *-pci
          description: Host bridge
          product: Sky Lake Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0

```
I'm posting this here, I'll read through it while you do, but it looks like when I partitioned my drives, I may not have been doing what I thought I was doing. This is the first time I've tried to set up a multi drive system with SSDs.

---

### Post by rufuslucky on 2017-09-05
I honestly don't see where I created the 50 gb logical drive that has by /boot file extension in it. It has been about 4 months since I did the reinstall though. Maybe what I need to do start from scratch on the reinstall, but I'm not terribly good at partitioning... apparently. Any idea why the system is creating this tiny little 512 boot ext? 


```
Number Start End Size Type File system Flags
1 1049kB 512MB 511MB primary boot
2 513MB 1000GB 1000GB extended
5 513MB 1000GB 1000GB logical
```

---

### Post by oldfred on 2017-09-05
It used to be 256MB and there have been many posts on users with full /boot partitions. What compounded the issue is multiple versions of kernel signed (for UEFI secure boot) & standard.

Sounds like a desktop. Do you really need full drive encryption which uses the advanced LVM logical volumes inside one standard partition that is full drive (except /boot & /EFI).
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm) 

If you need encryption you also then need to learn about LVM.

It looks like you have a new UEFI system but have three drives with the now 35 year old MBR(msdos) partitioning which is standard with the 35 year old BIOS boot. One is newer gpt.
With new UEFI systems, you can install in either UEFI or BIOS as hardware is backwards compatible if you have older drives or just want the old BIOS/MBR configuration.

If only installing Ubuntu onto a drive, you can use gpt with BIOS or UEFI boot. With BIOS you need a tiny 1MB unformatted partition flagged bios_grub and with UEFI you need the ESP - efi system partition which is FAT32 with boot flag. I normally partition all drives gpt and make ESP, bios_grub as first two partitions, even larger flash drives. And I include them on all data drives, so later I can add an install. But actually prefer to have a working install on all drives.

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by deadflowr on 2017-09-05
> cat/etc/fstab? I don't get any output from that command. 

Should be cat /etc/fstab.
space it between cat and /etc

---

