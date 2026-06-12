---
title: "Laptop battery drain on suspend"
date: 2019-11-17
forum: General Help
---

### Post by leoneiva on 2019-11-17
My laptop battery drain fast on suspend mode.
It drains about 30% each 12 hours.


No USB connected.

> 
/sys/power/mem_sleep

s2idle [deep]


> [FONT=monospace][COLOR=#000000]sudo journalctl | grep "PM: suspend" | tail[/COLOR]
[/FONT]# [FONT=monospace][COLOR=#000000]kernel: PM: suspend entry (deep)[/COLOR]

[/FONT]

> Caminho do hardware  Dispositivo  Classe         Descrição============================================================
                                  system         81FE (LENOVO_MT_81FE_BU_idea_FM_ideapad 330-15IKB)
/0                                bus            LNVNB161216
/0/0                              memory         128KiB BIOS
/0/4                              processor      Intel(R) Core(TM) i5-8250U CPU @ 1.60GHz
/0/4/5                            memory         256KiB L1 cache
/0/4/6                            memory         1MiB L2 cache
/0/4/7                            memory         6MiB L3 cache
/0/25                             memory         8GiB Memória do sistema
/0/25/0                           memory         4GiB SODIMM DDR4 Síncrono Unbuffered (Unregistered) 2133 MHz (0,5 ns)
/0/25/1                           memory         4GiB SODIMM DDR4 Síncrono Unbuffered (Unregistered) 2133 MHz (0,5 ns)
/0/100                            bridge         Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
/0/100/2                          display        UHD Graphics 620
/0/100/14                         bus            Sunrise Point-LP USB 3.0 xHCI Controller
/0/100/14/0          usb1         bus            xHCI Host Controller
/0/100/14/0/1                     input          2.4G Receiver
/0/100/14/0/7                     communication  Interface sem fio bluetooth
/0/100/14/0/8                     multimedia     EasyCamera
/0/100/14/1          usb2         bus            xHCI Host Controller
/0/100/14.2                       generic        Sunrise Point-LP Thermal subsystem
/0/100/15                         generic        Sunrise Point-LP Serial IO I2C Controller #0
/0/100/16                         communication  Sunrise Point-LP CSME HECI #1
/0/100/17            scsi0        storage        Sunrise Point-LP SATA Controller [AHCI mode]
/0/100/17/0.0.0      /dev/sda     disk           1TB WDC WD10SPZX-24Z
/0/100/17/0.0.0/1                 volume         259MiB Windows FAT volume
/0/100/17/0.0.0/2    /dev/sda2    volume         223GiB volume EXT4
/0/100/17/0.0.0/3    /dev/sda3    volume         15GiB Linux swap volume
/0/100/17/0.0.0/4    /dev/sda4    volume         263GiB Windows NTFS volume
/0/100/17/0.0.0/5    /dev/sda5    volume         397GiB Windows NTFS volume
/0/100/17/0.0.0/6    /dev/sda6    volume         32GiB volume EXT4
/0/100/1c                         bridge         Sunrise Point-LP PCI Express Root Port #5
/0/100/1c/0          enp1s0       network        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/1c.5                       bridge         Sunrise Point-LP PCI Express Root Port #6
/0/100/1c.5/0        wlp2s0       network        QCA9377 802.11ac Wireless Network Adapter
/0/100/1f                         bridge         Sunrise Point LPC Controller/eSPI Controller
/0/100/1f.2                       memory         Memory controller
/0/100/1f.3                       multimedia     Sunrise Point-LP HD Audio
/0/100/1f.4                       bus            Sunrise Point-LP SMBus
/0/1                              system         PnP device PNP0c02
/0/2                              system         PnP device PNP0c02
/0/3                              system         PnP device PNP0c02
/0/5                              system         PnP device PNP0b00
/0/6                              generic        PnP device INT3f0d
/0/7                              input          PnP device PNP0303
/0/8                              system         PnP device PNP0c02
/0/9                              system         PnP device PNP0c02
/1                                power          CRB Battery 0
/2                                power          OEM Define 5



Thanks

---

