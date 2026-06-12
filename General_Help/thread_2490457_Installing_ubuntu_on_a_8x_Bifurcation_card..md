---
title: "Installing ubuntu on a 8x Bifurcation card."
date: 2023-09-04
forum: General Help
---

### Post by josephchrzempiec on 2023-09-04
Hello, I have a supermicro intel motherboard x11sdv-4c-tln2f. It was haves a 8x pcie slot which I can boot from using a pcie to nvme drive. I would like to have a mirror drive on the 8x slot. I do have a dual nvme to 8x pcie card that uses bifurcation. I honestlty don't know If I can raid the card in mirror somehow and load ubuntu server or not. This is the motherboard [https://www.supermicro.com/en/products/motherboard/x11sdv-4c-tln2f](https://www.supermicro.com/en/products/motherboard/x11sdv-4c-tln2f). 

I'm asking the community if it's possible to use the bifurcation card to do this? Sense I'm already using all the sataports up with drives and the Oculink port that will be for a cash drive. I'm sorry this is all new to me. please bare with me if I don't understand it.

Joseph

---

### Post by josephchrzempiec on 2023-09-04
Just an update. The motherboard does support Bifurcation. I'm looking how to set that up. I just don't know if I can raid them while installing ubuntu.

---

### Post by MAFoElffen on 2023-09-06
I just finished upgrading two of my servers. One, was to retire my SuperMicro Server Board. I replaced both server boards with a gaming boards, as I liked how the bus and posts split out, and the speeds for them (One is Gen4, and the other is PCI Gen5 & Gen4). Yes, I looked at boards that support bifurcation and opted out.

For motherboards that do support bifuration, first it was about $250-$350 more, just for that feature. Then it was how they split the bus out between NVMe and SATA (like you are facing now). I couldn't see giving up SATA ports to use NVMe drives and vice versa, and with some, it cuts the speeds and lanes down in a way that doesn't make it worth it yet. I think the technology is still new and they will figure that out, and the prices will go down.

Read you motherboard manual very carefully, because of what I brought up in the previous paragraph. See which NVMe posts get disabled when all the SATA ports are being used. Each manufacturer seems to be different with that, even with the same manufacturer and different models of boards. Example, one of my MB's has 7 SATA ports and 5 NVMe ports... But if one NVme port is used in a sprcic slot, it disables a specific SATA port. I didn't see that until I read the manual. But for what it was, it was okay by me.

In the meanwhile, I have two PCIex16 x M.2 Quad cards. Both cards have onboard bifurcation, as my server's motherboards do not support bifurcation on the motherboards. I have one in each of my servers... I have the drives on each raided.

They show up in the installer as just more NVMe drives. Although, I use the Ubuntu Server Edition Live Installer disk, I don't use the installer on it, as all my rigs are ZFS-On-Root. But I do testing on the daily Installer ISO images. The Server Edition Live Installer will install RAID with mdadm, easily. I come up with some fairly complex installs in my test suite.

I can should you a few example if you would like... This is one of my servers showing the quad card, and SATA SSD drives:
```

mafoelffen@Mikes-B460M:~$ sudo zpool status -v kpool datapool
  pool: datapool
 state: ONLINE
  scan: scrub in progress since Tue Sep  5 21:18:09 2023
    1.73T scanned at 2.73G/s, 1.15T issued at 1.81G/s, 1.73T total
    0B repaired, 66.44% done, 00:05:27 to go
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors

  pool: kpool
 state: ONLINE
  scan: scrub repaired 0B in 00:07:43 with 0 errors on Sun Aug 13 00:31:45 2023
config:

    NAME                                 STATE     READ WRITE CKSUM
    kpool                                ONLINE       0     0     0
      raidz2-0                           ONLINE       0     0     0
        nvme-eui.0025385a2140bd61-part1  ONLINE       0     0     0
        nvme-eui.0025385a21418769-part1  ONLINE       0     0     0
        nvme-eui.0025385a2141f4fc-part1  ONLINE       0     0     0
        nvme-eui.0025385b21407ef0-part1  ONLINE       0     0     0

errors: No known data errors

```
Next post are examples of more traditional RAID installs with the Server Edition Live Installer...

---

### Post by MAFoElffen on 2023-09-06
This is LVM2 RAID, which uses mdadm with it's own extensions. The LVM RAID was created in the CLI prompt, then switched back to the partitioner, which is filesystem and file manager aware. So you make the mounts, then continue the install. I think I posted a terminal log in a post on this forum to show someone how to do that. Use the forum search function.

This is a RAID1 Root, which a RAID6 Home...
```

mafoelffen@lvm-raid-test-01:~$ sudo lvs -a -o name,segtype,devices
  LV                 Type   Devices                                                                                            
  lv-home            raid6  lv-home_rimage_0(0),lv-home_rimage_1(0),lv-home_rimage_2(0),lv-home_rimage_3(0),lv-home_rimage_4(0)
  [lv-home_rimage_0] linear /dev/sdd1(1)                                                                                       
  [lv-home_rimage_1] linear /dev/sde1(1)                                                                                       
  [lv-home_rimage_2] linear /dev/sdf1(1)                                                                                       
  [lv-home_rimage_3] linear /dev/sdg1(1)                                                                                       
  [lv-home_rimage_4] linear /dev/sdh1(1)                                                                                       
  [lv-home_rmeta_0]  linear /dev/sdd1(0)                                                                                       
  [lv-home_rmeta_1]  linear /dev/sde1(0)                                                                                       
  [lv-home_rmeta_2]  linear /dev/sdf1(0)                                                                                       
  [lv-home_rmeta_3]  linear /dev/sdg1(0)                                                                                       
  [lv-home_rmeta_4]  linear /dev/sdh1(0)                                                                                       
  lv-root            raid1  lv-root_rimage_0(0),lv-root_rimage_1(0)                                                            
  [lv-root_rimage_0] linear /dev/sdb1(1)                                                                                       
  [lv-root_rimage_1] linear /dev/sdc1(1)                                                                                       
  [lv-root_rmeta_0]  linear /dev/sdb1(0)                                                                                       
  [lv-root_rmeta_1]  linear /dev/sdc1(0)                                                                                       
  lv-swap            linear /dev/sda3(0)                                                                                       
mafoelffen@lvm-raid-test-01:~$ lsblk -e7 -o name,label,size,fstype,mountpoint,model
NAME                           LABEL                           SIZE FSTYPE      MOUNTPOINT MODEL
sda                                                             10G                        QEMU HARDDISK
&#9500;&#9472;sda1                         EFI                           749.6M vfat        /boot/efi  
&#9500;&#9472;sda2                                                           2G ext4        /boot      
&#9492;&#9472;sda3                                                         7.3G LVM2_member            
  &#9492;&#9472;vg--swap-lv--swap                                            4G swap        [SWAP]     
sdb                                                             20G                        QEMU HARDDISK
&#9492;&#9472;sdb1                                                          20G LVM2_member            
  &#9500;&#9472;vg--root-lv--root_rmeta_0                                    4M                        
  &#9474; &#9492;&#9472;vg--root-lv--root                                         18G ext4        /          
  &#9492;&#9472;vg--root-lv--root_rimage_0                                  18G                        
    &#9492;&#9472;vg--root-lv--root                                         18G ext4        /          
sdc                                                             20G                        QEMU HARDDISK
&#9492;&#9472;sdc1                                                          20G LVM2_member            
  &#9500;&#9472;vg--root-lv--root_rmeta_1                                    4M                        
  &#9474; &#9492;&#9472;vg--root-lv--root                                         18G ext4        /          
  &#9492;&#9472;vg--root-lv--root_rimage_1                                  18G                        
    &#9492;&#9472;vg--root-lv--root                                         18G ext4        /          
sdd                                                             10G                        QEMU HARDDISK
&#9492;&#9472;sdd1                                                          10G LVM2_member            
  &#9500;&#9472;vg--home-lv--home_rmeta_0                                    4M                        
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home      
  &#9492;&#9472;vg--home-lv--home_rimage_0                                 6.7G                        
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home      
sde                                                             10G                        QEMU HARDDISK
&#9492;&#9472;sde1                                                          10G LVM2_member            
  &#9500;&#9472;vg--home-lv--home_rmeta_1                                    4M                        
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home      
  &#9492;&#9472;vg--home-lv--home_rimage_1                                 6.7G                        
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home      
sdf                                                             10G                        QEMU HARDDISK
&#9492;&#9472;sdf1                                                          10G LVM2_member            
  &#9500;&#9472;vg--home-lv--home_rmeta_2                                    4M                        
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home      
  &#9492;&#9472;vg--home-lv--home_rimage_2                                 6.7G                        
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home      
sdg                                                             10G                        QEMU HARDDISK
&#9492;&#9472;sdg1                                                          10G LVM2_member            
  &#9500;&#9472;vg--home-lv--home_rmeta_3                                    4M                        
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home      
  &#9492;&#9472;vg--home-lv--home_rimage_3                                 6.7G                        
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home      
sdh                                                             10G                        QEMU HARDDISK
&#9492;&#9472;sdh1                                                          10G LVM2_member            
  &#9500;&#9472;vg--home-lv--home_rmeta_4                                    4M                        
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home      
  &#9492;&#9472;vg--home-lv--home_rimage_4                                 6.7G                        
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home      
sdi                                                             10G                        QEMU HARDDISK
&#9492;&#9472;sdi1                                                          10G LVM2_member            
sdj                                                             10G                        QEMU HARDDISK
&#9492;&#9472;sdj1                                                          10G LVM2_member            
sr0                            Ubuntu-Server 22.04 LTS amd64   1.4G iso9660                QEMU DVD-ROM

```

---

### Post by MAFoElffen on 2023-09-06
This test case was installed completely from the menu's within the Server Edition Live Installer. The root & home arrays are both RAID5:
```

mafoelffen@u-server-raid5-01:~$ lsblk -e7 -o name,label,size,fstype,mountpoint,model
NAME          LABEL                     SIZE FSTYPE            MOUNTPOINT MODEL
sr0           Ubuntu 20.04.3 LTS amd64  2.9G iso9660                      QEMU_DVD-ROM
vda                                      40G                              
&#9500;&#9472;vda1                                  512M vfat              /boot/efi  
&#9500;&#9472;vda2        ubuntu-server:root         20G linux_raid_member            
&#9474; &#9492;&#9472;md126                                40G                              
&#9474;   &#9500;&#9472;md126p1                            31G ext4              /          
&#9474;   &#9492;&#9472;md126p2                             9G swap              [SWAP]     
&#9492;&#9472;vda3        ubuntu-server:home       19.5G linux_raid_member            
  &#9492;&#9472;md127                                39G                              
    &#9492;&#9472;md127p1                            39G ext4              /home      
vdb                                      40G                              
&#9500;&#9472;vdb1                                  512M vfat                         
&#9500;&#9472;vdb2        ubuntu-server:root         20G linux_raid_member            
&#9474; &#9492;&#9472;md126                                40G                              
&#9474;   &#9500;&#9472;md126p1                            31G ext4              /          
&#9474;   &#9492;&#9472;md126p2                             9G swap              [SWAP]     
&#9492;&#9472;vdb3        ubuntu-server:home       19.5G linux_raid_member            
  &#9492;&#9472;md127                                39G                              
    &#9492;&#9472;md127p1                            39G ext4              /home      
vdc                                      40G                              
&#9500;&#9472;vdc1                                  512M vfat                         
&#9500;&#9472;vdc2        ubuntu-server:root         20G linux_raid_member            
&#9474; &#9492;&#9472;md126                                40G                              
&#9474;   &#9500;&#9472;md126p1                            31G ext4              /          
&#9474;   &#9492;&#9472;md126p2                             9G swap              [SWAP]     
&#9492;&#9472;vdc3        ubuntu-server:home       19.5G linux_raid_member            
  &#9492;&#9472;md127                                39G                              
    &#9492;&#9472;md127p1                            39G ext4              /home      
mafoelffen@u-server-raid5-01:~$ sudo mdadm -D /dev/md* 2> /dev/null
[sudo] password for mafoelffen: 
/dev/md126:
           Version : 1.2
     Creation Time : Tue Jan 25 06:59:28 2022
        Raid Level : raid5
        Array Size : 41908224 (39.97 GiB 42.91 GB)
     Used Dev Size : 20954112 (19.98 GiB 21.46 GB)
      Raid Devices : 3
     Total Devices : 3
       Persistence : Superblock is persistent

       Update Time : Wed Sep  6 05:35:35 2023
             State : active 
    Active Devices : 3
   Working Devices : 3
    Failed Devices : 0
     Spare Devices : 0

            Layout : left-symmetric
        Chunk Size : 512K

Consistency Policy : resync

              Name : ubuntu-server:root
              UUID : fb9d7067:6a3c8160:76fc06b6:913b54ce
            Events : 98

    Number   Major   Minor   RaidDevice State
       0     252        2        0      active sync   /dev/vda2
       1     252       18        1      active sync   /dev/vdb2
       3     252       34        2      active sync   /dev/vdc2
/dev/md126p1:
           Version : 1.2
     Creation Time : Tue Jan 25 06:59:28 2022
        Raid Level : raid5
        Array Size : 32505856 (31.00 GiB 33.29 GB)
     Used Dev Size : 20954112 (19.98 GiB 21.46 GB)
      Raid Devices : 3
     Total Devices : 3
       Persistence : Superblock is persistent

       Update Time : Wed Sep  6 05:35:35 2023
             State : active 
    Active Devices : 3
   Working Devices : 3
    Failed Devices : 0
     Spare Devices : 0

            Layout : left-symmetric
        Chunk Size : 512K

Consistency Policy : resync

              Name : ubuntu-server:root
              UUID : fb9d7067:6a3c8160:76fc06b6:913b54ce
            Events : 98

    Number   Major   Minor   RaidDevice State
       0     252        2        0      active sync   /dev/vda2
       1     252       18        1      active sync   /dev/vdb2
       3     252       34        2      active sync   /dev/vdc2
/dev/md126p2:
           Version : 1.2
     Creation Time : Tue Jan 25 06:59:28 2022
        Raid Level : raid5
        Array Size : 9398272 (8.96 GiB 9.62 GB)
     Used Dev Size : 20954112 (19.98 GiB 21.46 GB)
      Raid Devices : 3
     Total Devices : 3
       Persistence : Superblock is persistent

       Update Time : Wed Sep  6 05:35:35 2023
             State : active 
    Active Devices : 3
   Working Devices : 3
    Failed Devices : 0
     Spare Devices : 0

            Layout : left-symmetric
        Chunk Size : 512K

Consistency Policy : resync

              Name : ubuntu-server:root
              UUID : fb9d7067:6a3c8160:76fc06b6:913b54ce
            Events : 98

    Number   Major   Minor   RaidDevice State
       0     252        2        0      active sync   /dev/vda2
       1     252       18        1      active sync   /dev/vdb2
       3     252       34        2      active sync   /dev/vdc2
/dev/md127:
           Version : 1.2
     Creation Time : Tue Jan 25 06:59:47 2022
        Raid Level : raid5
        Array Size : 40855552 (38.96 GiB 41.84 GB)
     Used Dev Size : 20427776 (19.48 GiB 20.92 GB)
      Raid Devices : 3
     Total Devices : 3
       Persistence : Superblock is persistent

       Update Time : Wed Sep  6 05:35:03 2023
             State : clean 
    Active Devices : 3
   Working Devices : 3
    Failed Devices : 0
     Spare Devices : 0

            Layout : left-symmetric
        Chunk Size : 512K

Consistency Policy : resync

              Name : ubuntu-server:home
              UUID : a9182c26:15cf3e22:0a6809a9:dc958684
            Events : 193

    Number   Major   Minor   RaidDevice State
       0     252        3        0      active sync   /dev/vda3
       1     252       19        1      active sync   /dev/vdb3
       3     252       35        2      active sync   /dev/vdc3
/dev/md127p1:
           Version : 1.2
     Creation Time : Tue Jan 25 06:59:47 2022
        Raid Level : raid5
        Array Size : 40851456 (38.96 GiB 41.83 GB)
     Used Dev Size : 20427776 (19.48 GiB 20.92 GB)
      Raid Devices : 3
     Total Devices : 3
       Persistence : Superblock is persistent

       Update Time : Wed Sep  6 05:35:03 2023
             State : clean 
    Active Devices : 3
   Working Devices : 3
    Failed Devices : 0
     Spare Devices : 0

            Layout : left-symmetric
        Chunk Size : 512K

Consistency Policy : resync

              Name : ubuntu-server:home
              UUID : a9182c26:15cf3e22:0a6809a9:dc958684
            Events : 193

    Number   Major   Minor   RaidDevice State
       0     252        3        0      active sync   /dev/vda3
       1     252       19        1      active sync   /dev/vdb3
       3     252       35        2      active sync   /dev/vdc3

```
I also have others... Some are RAID10, RAID50, and RAID60, that were created from the command line, then toggled into the partitioner, and continued the install. Some are BTRFS RAID.

So yes, "it is possible". The installer sees the drives on a PCIe to M.2 card just like any other drive, assigned by bus, slot, etc. It is also file manager aware. On "how", it depends on what you want to do, how detailed, and how much work you want to do. Just that some are more work than others.

---

### Post by josephchrzempiec on 2023-09-13
Hello, Just an update. I couldn't get Bifurcation to work. So i broke down and called supermicro. It looks like that the bios I have is very old. I had a 1.0b and it turns out there is a 1.09. Once I upgraded and I still didn't see in the bios the drives. I called them back and they told me that is normal. They told me go to into liunx and search for the drives. I did that and sure enough there they are. all drives shown now. 

Thank you all for the help and support. This community once again is awesome.

Joseph

---

