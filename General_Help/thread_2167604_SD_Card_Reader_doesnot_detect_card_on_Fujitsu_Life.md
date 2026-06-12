---
title: "SD Card Reader doesnot detect card on Fujitsu Lifebook S752"
date: 2013-08-14
forum: General Help
---

### Post by gore-amit on 2013-08-14
Hi,

I am not able to use my SD card reader as it is not detecting cards. My laptop is Fujitsu Lifebook S Series Model Number 752  (ie S752).
I tried few things which were on the forums but somehow could not suceed.
Here are the command out put for some of the commands that would be help people to guide me, get this working.

maverake@maverick:~$ sudo fdisk -l 
sudo: unable to resolve host maverick

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6ae8a843

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   183028544    91513248+   7  HPFS/NTFS/exFAT
/dev/sda2       183029760   420337663   118653952    7  HPFS/NTFS/exFAT
/dev/sda3       420339710   625141759   102401025    5  Extended
/dev/sda5       420339712   453267455    16463872   82  Linux swap / Solaris
/dev/sda6       453269504   461266943     3998720   83  Linux
/dev/sda7       461268992   625141759    81936384   83  Linux
maverake@maverick:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.7 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
0a:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
0b:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)
maverake@maverick:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 001 Device 007: ID 0489:e052 Foxconn / Hon Hai 
Bus 001 Device 005: ID 04f2:b302 Chicony Electronics Co., Ltd 
Bus 001 Device 006: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 003 Device 002: ID 0461:4d81 Primax Electronics, Ltd

---

