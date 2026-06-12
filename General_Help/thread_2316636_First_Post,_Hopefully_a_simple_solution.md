---
title: "First Post, Hopefully a simple solution"
date: 2016-03-09
forum: General Help
---

### Post by nick_h2 on 2016-03-09
Hello all, first post here, i just installed ubuntu server 14.04 on one machine and moved the install over to another, now when it boots there in no internet connection, i have to run sudo dhclient eth0 everytime i reboot to get internet access.. is there something i missed or a better way to connect ethernet than this? im running headless atm. this is messing with my SMB shares also, so im having to reboot, run dhclient, restart samba just to keep my server going.. not exactly what i was hoping for when i decided to repurpose a system for a NAS. any assistance would be greatly appreciated, thank you.

---

### Post by 1clue on 2016-03-09
Why did you install on one machine and boot from the other?

There are lots of possible reasons for the system not initializing network.  The first that comes to mind is that you have a different brand/model of network card on the two machines and the driver for your current system is not installed.  The second thing is that you might  have more than one card on one of the boxes.

Open a terminal window and post the output of 'lspci' on the current headless server.

---

### Post by nick_h2 on 2016-03-09
i understand it wasnt the way to go and already regret it but im all setup and running good now, until this problem surfaced after needing to reboot. the older hardware had boot from USB bugs and i have no CD drive so i installed to a hard drive via usb on a newer desktop then moved the system drive to the new NAS PC. thanks in advance.

```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)




```

---

### Post by 1clue on 2016-03-09
Reboot and without setting up networking, login and type: [B]lsmod | grep r8169

[/B]Also helpful (I should have said it before) would be **lspci -k** before you have the network.

Then again after you have network.

Thanks.

---

### Post by nick_h2 on 2016-03-09
thank you

lsmod command returned r8169 both in red both before and after dhclient eth0


```

r8169                    81920 0
mii                       16384 1 r8169

```

and [B]lspci -k gave the same before and after running sudo dhclient eth0

[/B]```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)        Subsystem: Gigabyte Technology Co., Ltd Device 5000
        Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
        Subsystem: Gigabyte Technology Co., Ltd Device d000
        Kernel driver in use: i915
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
        Subsystem: Gigabyte Technology Co., Ltd GA-D525TUD (Realtek ALC887)
        Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
        Kernel driver in use: pcieport
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
        Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
        Subsystem: Gigabyte Technology Co., Ltd GA-D525TUD
        Kernel driver in use: uhci_hcd
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
        Subsystem: Gigabyte Technology Co., Ltd GA-D525TUD
        Kernel driver in use: uhci_hcd
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
        Subsystem: Gigabyte Technology Co., Ltd GA-D525TUD
        Kernel driver in use: uhci_hcd
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
        Subsystem: Gigabyte Technology Co., Ltd GA-D525TUD
        Kernel driver in use: uhci_hcd
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
        Subsystem: Gigabyte Technology Co., Ltd GA-D525TUD
        Kernel driver in use: ehci-pci
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: Gigabyte Technology Co., Ltd Device 5001
        Kernel driver in use: lpc_ich
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
        Subsystem: Gigabyte Technology Co., Ltd Device b002
        Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
        Subsystem: Gigabyte Technology Co., Ltd GA-8I945PG-RH/GA-D525TUD Mainboard
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
        Subsystem: Gigabyte Technology Co., Ltd Motherboard
        Kernel driver in use: r8169



```

ok digging on my own here /etc/network/interfaces only contains lo information, i added auto eth0    iface eth0 inet dhcp   , going to reboot and test outcome.. brb

---

### Post by nick_h2 on 2016-03-09
Ok, i fixed er up, thanks again for the help and sorry to fill the forum with useless stuff, im pretty linux rusty.. last time i installed a distro i think it was Slackware 4 at least 15, maybe 20 years ago now.

---

