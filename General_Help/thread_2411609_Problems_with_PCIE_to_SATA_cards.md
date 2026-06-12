---
title: "Problems with PCIE to SATA cards"
date: 2019-02-01
forum: General Help
---

### Post by shag00 on 2019-02-01
Hardware:
MSI X470 Gaming Pro Carbon
Ryzon 2600X
Nvidia 1050

I have a recurring problem with my PCIE to SATA cards. Originally I thought it was a hardware problem until I replaced both cards and still have a problem. Specifically the problem is that the disks attached to one card are not detected about half the time. Now this statement needs a bit of extra information:
1. The disks are detected by BIOS at power on (they flash up on the screen)
2. They must be detected at initial system start as they are are listed in fstab (if they were missing kubuntu would not start)
3. Randomly the disks are not present in nautilus nor blkid although the controllers are listed in lshw
4. One controller with disks is always properly detected, it's always one controller that is missing

Until an ordered 8 port card arrives I am using 2 x 4 port cards.

Is there any way to force the system to correctly detect both cards/controllers/disks 100% of the time.

Following is lshw from a successful boot, the 2 SATA cards are labelled Storage-Marvell:

```
scott@scottlounge:~$ sudo lshw -short 
H/W path            Device     Class       Description
======================================================
                               system      MS-7B78 (To be filled by O.E.M.)
/0                             bus         X470 GAMING PRO CARBON (MS-7B78)
/0/0                           memory      64KiB BIOS
/0/f                           memory      8GiB System Memory
/0/f/0                         memory      2667 MHz (0.4 ns) [empty]
/0/f/1                         memory      8GiB DIMM DDR4 Synchronous Unbuffered (Unregistered) 2667 MHz (0.4 ns)
/0/f/2                         memory      2667 MHz (0.4 ns) [empty]
/0/f/3                         memory      2667 MHz (0.4 ns) [empty]
/0/11                          memory      576KiB L1 cache
/0/12                          memory      3MiB L2 cache
/0/13                          memory      16MiB L3 cache
/0/14                          processor   AMD Ryzen 5 2600X Six-Core Processor
/0/100                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/100/0.2                     generic     Advanced Micro Devices, Inc. [AMD]
/0/100/1.1                     bridge      Advanced Micro Devices, Inc. [AMD]
/0/100/1.1/0                   storage     Sandisk Corp
/0/100/1.3                     bridge      Advanced Micro Devices, Inc. [AMD]
/0/100/1.3/0                   bus         Advanced Micro Devices, Inc. [AMD]
/0/100/1.3/0/0      usb1       bus         xHCI Host Controller
/0/100/1.3/0/0/c               input       USB Receiver
/0/100/1.3/0/0/d               input       USB Receiver
/0/100/1.3/0/1      usb2       bus         xHCI Host Controller
/0/100/1.3/0.1                 storage     Advanced Micro Devices, Inc. [AMD]
/0/100/1.3/0.2                 bridge      Advanced Micro Devices, Inc. [AMD]
/0/100/1.3/0.2/0               bridge      Advanced Micro Devices, Inc. [AMD]
/0/100/1.3/0.2/1               bridge      Advanced Micro Devices, Inc. [AMD]
/0/100/1.3/0.2/1/0  enp24s0    network     I211 Gigabit Network Connection
/0/100/1.3/0.2/2               bridge      Advanced Micro Devices, Inc. [AMD]
/0/100/1.3/0.2/2/0             storage     Marvell Technology Group Ltd.
/0/100/1.3/0.2/3               bridge      Advanced Micro Devices, Inc. [AMD]
/0/100/1.3/0.2/3/0             storage     Marvell Technology Group Ltd.
/0/100/1.3/0.2/4               bridge      Advanced Micro Devices, Inc. [AMD]
/0/100/3.1                     bridge      Advanced Micro Devices, Inc. [AMD]
/0/100/3.1/0                   display     GP107 [GeForce GTX 1050]
/0/100/3.1/0.1                 multimedia  NVIDIA Corporation
/0/100/7.1                     bridge      Advanced Micro Devices, Inc. [AMD]
/0/100/7.1/0                   generic     Advanced Micro Devices, Inc. [AMD]
/0/100/7.1/0.2                 generic     Advanced Micro Devices, Inc. [AMD]
/0/100/7.1/0.3                 bus         Advanced Micro Devices, Inc. [AMD]
/0/100/7.1/0.3/0    usb3       bus         xHCI Host Controller
/0/100/7.1/0.3/1    usb4       bus         xHCI Host Controller
/0/100/8.1                     bridge      Advanced Micro Devices, Inc. [AMD]
/0/100/8.1/0                   generic     Advanced Micro Devices, Inc. [AMD]
/0/100/8.1/0.2                 storage     FCH SATA Controller [AHCI mode]
/0/100/8.1/0.3                 multimedia  Advanced Micro Devices, Inc. [AMD]
/0/100/14                      bus         FCH SMBus Controller
/0/100/14.3                    bridge      FCH LPC Bridge
/0/101                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/102                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/103                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/104                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/105                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/106                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/107                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/108                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/109                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/10a                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/10b                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/10c                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/10d                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/10e                         bridge      Advanced Micro Devices, Inc. [AMD]
/0/1                scsi0      storage     
/0/1/0.0.0          /dev/sda   disk        6001GB HGST HDN726060AL
/0/1/0.0.0/1        /dev/sda1  volume      5589GiB EXT4 volume
/0/2                scsi1      storage     
/0/2/0.0.0          /dev/sdb   disk        6001GB ST6000VN0001-1SF
/0/2/0.0.0/1        /dev/sdb1  volume      5589GiB EXT4 volume
/0/3                scsi11     storage     
/0/3/0.0.0          /dev/sdk   disk        4TB WDC WD40EZRX-00S
/0/3/0.0.0/0        /dev/sdk   disk        4TB 
/0/3/0.0.0/0/1      /dev/sdk1  volume      3726GiB EXT4 volume
/0/4                scsi12     storage     
/0/4/0.0.0          /dev/sdl   disk        4TB WDC WD40EFRX-68W
/0/4/0.0.0/0        /dev/sdl   disk        4TB 
/0/4/0.0.0/0/1      /dev/sdl1  volume      3726GiB EXT4 volume
/0/5                scsi13     storage     
/0/5/0.0.0          /dev/sdm   disk        4TB WDC WD40EZRX-22S
/0/5/0.0.0/0        /dev/sdm   disk        4TB 
/0/5/0.0.0/0/1      /dev/sdm1  volume      3726GiB EXT4 volume
/0/6                scsi15     storage     
/0/6/0.0.0          /dev/sdn   disk        6001GB HGST HDN726060AL
/0/6/0.0.0/0        /dev/sdn   disk        6001GB 
/0/6/0.0.0/0/1      /dev/sdn1  volume      5589GiB EXT4 volume
/0/7                scsi2      storage     
/0/7/0.0.0          /dev/sdc   disk        6001GB ST6000VN0041-2EL
/0/7/0.0.0/1        /dev/sdc1  volume      5589GiB EXT4 volume
/0/8                scsi3      storage     
/0/8/0.0.0          /dev/sdd   disk        6001GB HGST HDN726060AL
/0/8/0.0.0/1        /dev/sdd1  volume      5589GiB EXT4 volume
/0/9                scsi4      storage     
/0/9/0.0.0          /dev/sde   disk        4TB ST4000DM000-1F21
/0/9/0.0.0/1        /dev/sde1  volume      3726GiB EXT4 volume
/0/a                scsi5      storage     
/0/a/0.0.0          /dev/sdf   disk        4TB ST4000DM000-1F21
/0/a/0.0.0/1        /dev/sdf1  volume      3726GiB EXT4 volume
/0/b                scsi6      storage     
/0/b/0.0.0          /dev/sdg   disk        4TB WDC WD40EZRX-00S
/0/b/0.0.0/1        /dev/sdg1  volume      3726GiB EXT4 volume
/0/c                scsi7      storage     
/0/c/0.0.0          /dev/sdh   disk        6001GB ST6000DM001-1YW1
/0/c/0.0.0/1        /dev/sdh1  volume      5589GiB EXT4 volume
/0/d                scsi8      storage     
/0/d/0.0.0          /dev/sdi   disk        6001GB ST6000VN0041-2EL
/0/d/0.0.0/0        /dev/sdi   disk        6001GB 
/0/d/0.0.0/0/1      /dev/sdi1  volume      5589GiB EXT4 volume
/0/e                scsi10     storage     
/0/e/0.0.0          /dev/sdj   disk        120GB INTEL SSDSC2CW12
/0/e/0.0.0/0        /dev/sdj   disk        120GB 
/0/e/0.0.0/0/1      /dev/sdj1  volume      511MiB Windows FAT volume
/0/e/0.0.0/0/2      /dev/sdj2  volume      111GiB EXT4 volume
```

---

### Post by TheFu on 2019-02-01
**sudo lshw -C storage**
would be more helpful.  Thank for using code tags.

I have a Ryzen 2600 w/ Asus B450-F MB and have been having problems with SATA controllers working with eSATA and SATA optical devices.  The onboard and addon card both having issues with the optical drives. ;(

I have Marvell Technology Group using the driver=ahci, deviceid 1b4b:9215 from lspci -vnn output. It was a $20 4-port SATA controller.  Thinking I should have gotten a $90 LSI 2-port SAS JBOD controller instead. ;(

Post #3 here: [https://ubuntuforums.org/showthread.php?t=2293626](https://ubuntuforums.org/showthread.php?t=2293626) might be helpful.  I need to test that myself, soon.  I'd hoped to use IOMMU to passthru the disk controller and extra NIC to a VM. Oh well.

---

### Post by shag00 on 2019-02-01
My feeling is that spending more money on a new controller may not be the solution, my reason will become clearer with disclosure of the full history of this issue. First off most of the controllers use the same Marvell chip which has been around for donkey's years. The recent history of my system is that my server died about a month ago, as it built in 2013 it had a motherboard with 10 SATA ports and was an Intel system, requiring only 1 additional 4 port controller. The problem was the motherboard.

My first step in building the new system was to use the old controller which failed, by fail I mean the HDDs were either not visible to the file explorer or when accessed became invisible to the file explorer. As I had previously had early failures of these cards I kept 2 spares and in addition I had, through a purchasing mistake, 2 additional controllers. So in total I started the new build with 5 controllers, 4 new and 1 carry over from the old system. During the build process I purchased yet another controller so total 6. It was not until I had binned most of them that I started to pay attention, you know, they are cheap and I had stock etc. So at this current stage I have 2 brand new controllers installed and still 1 does not work properly (or more correctly, all the time). Being realistic, I feel the chances of buying so many controllers over an extended period of time from different sources and have so many fail due to the controllers being faulty is close to zero.

This is why I think the problem is either in the BIOS/UEFI or Ubuntu.

I am also receiving an error message at boot which I am also investigating that does not stop the system from booting either with all disks or half. Maybe this is connected somehow.

---

### Post by TheFu on 2019-02-02
Good to know, but the specific device numbers still matter.  Did that suggested work-around help?  I plan to test it here in a few hours after weekly patching, while still in the allowed maintenance window.

---

### Post by shag00 on 2019-02-03
Not directly, although it was part of the path to overcoming the problem. It appears there is a problem with the 4.15 kernel that operates to obviate the BIOS selection of, disable secure boot (various names from different manufacturers). This also affects the NVIDIA graphics driver, which it did in my case. The problem with the video driver though is it not completely fixed. So what I did was install version 4.19 of the kernel (latest release), the bug was fixed in 4.18. It's very easy to do, just download the deb files from [https://kernel.ubuntu.com](https://kernel.ubuntu.com)  [https://kernel.ubuntu.com/%7Ekernel-ppa/mainline/](https://kernel.ubuntu.com/%7Ekernel-ppa/mainline/)

Scroll to the bottom and select the kernel you want, click on it and then download these 4 files:

linux-headers-4.19.0-041900_4.19.0-041900.201810221809_all.deb
linux-headers-4.19.0-041900-generic_4.19.0-041900.201810221809_amd64.deb
linux-image-unsigned-4.19.0-041900-generic_4.19.0-041900.201810221809_amd64.deb
linux-modules-4.19.0-041900-generic_4.19.0-041900.201810221809_amd64.deb

then cd to your Downloads folder and 
```
sudo dpkg -i *.deb
```

So far I have managed about 2 dozen successful logins.

---

### Post by TheFu on 2019-02-03
When you install a package directly with dpkg, you changed to manual updates for that package going forward.  I would move back to the normal repo version as soon as practical.  Package management is one of the main reasons we love Linux over the other options.

---

