---
title: "Some sort of error in booting"
date: 2019-04-23
forum: General Help
---

### Post by matiazz on 2019-04-23
Hi!

I have a dell inspiron 7460, that had windows, and some time ago i install ubuntu. Today i format the machine and put kubuntu 18.04. The thing is that always, when i reboot there are errors(before with ubuntu 16 also). Looking to log, i think there are like this. What is it? 
I have install kubuntu in a SSD, and put /home in a HDD. May be some sort of bad configuration?


    22/4/19 21:50   kernel  pcieport 0000:00:1c.4: AER: Corrected error received: 0000:00:1c.4
    22/4/19 21:50   kernel  pcieport 0000:00:1c.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
    22/4/19 21:50   kernel  pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00000001/00002000
    22/4/19 21:50   kernel  pcieport 0000:00:1c.4:    [ 0] Receiver Error         (First)


I add info of /etc/fstab




     <file system> <mount point>   <type>  <options>       <dump>  <pass>
     / was on /dev/sdb3 during installation UUID=8abf8883-368a-4541-83f7-0aef21c1a153 /               ext4    errors=remount-ro 0       1
     /boot/efi was on /dev/sdb1 during installation UUID=D63C-01C3  /boot/efi       vfat    umask=0077      0       1
     /home was on /dev/sda1 during installation UUID=e086fc54-edc2-486d-bb3a-0bf9da5aab78 /home           ext4    defaults        0       2
     swap was on /dev/sdb2 during installation UUID=75f51894-ad0f-415e-85d0-bf0938a4e52a none            swap    sw              0       0




I add some information extra of the comand lspci -nn


    00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers [8086:5904] (rev 02)
    00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 620 [8086:5916] (rev 02)
    00:04.0 Signal processing controller [1180]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [8086:1903] (rev 02)
    00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21)
    00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal subsystem [8086:9d31] (rev 21)
    00:15.0 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 [8086:9d60] (rev 21)
    00:15.1 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 [8086:9d61] (rev 21)
    00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI #1 [8086:9d3a] (rev 21)
    00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] [8086:9d03] (rev 21)
    00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 [8086:9d10] (rev f1)
    00:1c.4 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 [8086:9d14] (rev f1)
    00:1c.5 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 [8086:9d15] (rev f1)
    00:1f.0 ISA bridge [0601]: Intel Corporation Sunrise Point-LP LPC Controller [8086:9d58] (rev 21)
    00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (rev 21)
    00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d71] (rev 21)
    00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
    01:00.0 3D controller [0302]: NVIDIA Corporation GM108M [GeForce 940MX] [10de:134d] (rev a2)
    03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)








any clue? What is this error? I try to read about but at least for now, noone explain what is it, only how to stop seeing the problem (not solving it). Also i feel it to slow to boot, its has a Ssd and 16Gb of RAM, its take a "lot" of time.


thx

---

### Post by Rubi1200 on 2019-04-24
Hi,

Best thing would be to post the summary of the boot info (see link in my signature). Do not repair anything, just post the report here. Please use code tags for easier reading Go Advanced >> look for # symbol and insert text.

Thanks.

---

### Post by oldfred on 2019-04-24
Does system otherwise run ok?
Those look more like warnings and say corrected.

---

