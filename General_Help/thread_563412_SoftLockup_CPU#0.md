---
title: "SoftLockup CPU#0"
date: 2007-09-29
forum: General Help
---

### Post by jimmy2975 on 2007-09-29
Hi ,
I have been using Ubuntu(Feisty) on my ACER 5570z. I have been getting soft lockup onCPU#0 for the past 3 days. It lock while trying to load manual drivers. Under recovery mode it is clear that it is ndiswrapper. My wireless is ATHEROS.  The lockup is very random and happens on both the kernels that I have. Here are some more details

lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

  tail -f /var/log/messages
Sep 29 20:07:50 acer-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Sep 29 20:07:50 acer-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Sep 29 20:07:50 acer-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Sep 29 20:27:11 acer-laptop -- MARK --
Sep 29 20:47:12 acer-laptop -- MARK --
Sep 29 21:07:12 acer-laptop -- MARK --
Sep 29 21:27:12 acer-laptop -- MARK --
Sep 29 21:47:12 acer-laptop -- MARK --
Sep 29 22:07:12 acer-laptop -- MARK --
Sep 29 22:27:13 acer-laptop -- MARK --

My wireless works. I always talk high and mighty about linux and my system cannot boot under both the kernels when everyone is waiting for me to start the presentation. I had to borrow someones laptop fromthe audience. Please help. I dont know where to start. Is this a BUG in the kernel

Thanks
Regards
Jimmy

---

### Post by jimmy2975 on 2007-10-01
I fixed the boot time soft lock on CPU by using Ndiswrapper 1.48. But now the system all of a sudden freezes when on battery(does not freeze with on adapter). Fom reading around looks like kernel 386 is rock solid. My kernel is 2.6.20-16-generic #2 SMP i686. 

HOW DO I DOWNGRADE TO i386. I have pentium dual core laptop. Will i386 reduce my performance and use only one CPU? 

Any commetns are appreciated.

Thanks
Jimmy

---

### Post by jimmy2975 on 2007-10-01
can someone tell how to downgrade ?????????????

---

