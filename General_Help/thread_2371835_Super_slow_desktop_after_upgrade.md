---
title: "Super slow desktop after upgrade"
date: 2017-09-19
forum: General Help
---

### Post by simoncks1994 on 2017-09-19
Hi everyone,

After update, my Desktop slows down a lot. Linux commands and reboot now take a lot of time. Chrome is usable.

dmesg output right after reboot
[https://paste.ubuntu.com/25570962/](https://paste.ubuntu.com/25570962/)

My desktop spec is not bad actually.
```
sudo lshw -short
H/W path       Device     Class          Description====================================================
                          system         To Be Filled By O.E.M. (To Be Filled By O.E.M.)
/0                        bus            B85 Pro4
/0/0                      memory         64KiB BIOS
/0/d                      memory         256KiB L1 cache
/0/e                      processor      Intel(R) Core(TM) i7-4790 CPU @ 3.60GHz
/0/e/f                    memory         1MiB L2 cache
/0/e/10                   memory         8MiB L3 cache
/0/11                     memory         32GiB System Memory
/0/11/0                   memory         8GiB DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
/0/11/1                   memory         8GiB DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
/0/11/2                   memory         8GiB DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
/0/11/3                   memory         8GiB DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
/0/100                    bridge         4th Gen Core Processor DRAM Controller
/0/100/2                  display        Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
/0/100/3                  multimedia     Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
/0/100/14                 bus            8 Series/C220 Series Chipset Family USB xHCI
/0/100/16                 communication  8 Series/C220 Series Chipset Family MEI Controller #1
/0/100/19      eth0       network        Ethernet Connection I217-V
/0/100/1a                 bus            8 Series/C220 Series Chipset Family USB EHCI #2
/0/100/1b                 multimedia     8 Series/C220 Series Chipset High Definition Audio Controller
/0/100/1c                 bridge         8 Series/C220 Series Chipset Family PCI Express Root Port #1
/0/100/1c.2               bridge         82801 PCI Bridge
/0/100/1c.2/0             bridge         ASM1083/1085 PCIe to PCI Bridge
/0/100/1d                 bus            8 Series/C220 Series Chipset Family USB EHCI #1
/0/100/1f                 bridge         B85 Express LPC Controller
/0/100/1f.2               storage        8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
/0/100/1f.3               bus            8 Series/C220 Series Chipset Family SMBus Controller
/0/1           scsi0      storage        
/0/1/0.0.0     /dev/sda   disk           3TB ST3000DM001-1ER1
/0/1/0.0.0/1              volume         511MiB Windows FAT volume
/0/1/0.0.0/2   /dev/sda2  volume         2762GiB EXT4 volume
/0/1/0.0.0/3   /dev/sda3  volume         31GiB Linux swap volume
/0/2           scsi2      storage        
/0/2/0.0.0     /dev/sdb   disk           3TB HGST HDN724030AL
/0/2/0.0.0/1   /dev/sdb1  volume         2794GiB EXT4 volume
/0/3           scsi3      storage        
/0/3/0.0.0     /dev/sdc   volume         2794GiB HGST HDN724030AL
/1             ham0       network        Ethernet interface

```

RAM and CPU usage looks fine according to [htop]("https://ibb.co/iWhTZQ").

Is there any indication why it is so slow?

Thanks in advance.

Simon

---

