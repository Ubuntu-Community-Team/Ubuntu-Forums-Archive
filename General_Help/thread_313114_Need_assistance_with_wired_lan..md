---
title: "Need assistance with wired lan."
date: 2006-12-05
forum: General Help
---

### Post by travis712 on 2006-12-05
I need some assistance with setting up my home pc to get the internet working. Yes, im a noob and all that. But your help would be greatly appreciated. Im on a lan network, all wired. When I go to networking tools it says "No device found" or something similar to this. This is taken from my previous thread which has been open for a week and I figured I might as well make a new thread, that subforum has next to no traffic.

travis@ubuntuTRAVSROOM:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f1 (rev a2)
0000:02:05.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:02:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Josh1 on 2006-12-05
Hi, are you connecting through a router or direct ethernet to modem or usb modem?

---

### Post by travis712 on 2006-12-05
From my pc my lan wire goes to a Linksys " 5 port workgroup switch". This then goes to another router, which I don't the model and such. So that is the actual lan base, then it goes to the router in my room, then to my PC. I hope that made since.

---

### Post by yopnono on 2006-12-05
What do you get if running ifconfig -a in the terminal

---

### Post by travis712 on 2006-12-07
Err, are you talking linux or windows?

---

### Post by travis712 on 2006-12-07
Nvm, dumb question. Anyway:


Microsoft(R) Windows DOS
(C)Copyright Microsoft Corp 1990-2001.

C:\DOCUME~1\OWNER>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : TRAVSROOM
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : WorkGroup

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : WorkGroup
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Eth
ernet NIC
        Physical Address. . . . . . . . . : 00-0E-A6-64-CF-16
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.2.4
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.2.1
        DHCP Server . . . . . . . . . . . : 192.168.2.1
        DNS Servers . . . . . . . . . . . : 192.168.2.1
        Lease Obtained. . . . . . . . . . : Thursday, December 07, 2006 8:40:01
PM
        Lease Expires . . . . . . . . . . : Thursday, December 07, 2006 10:40:01
 PM

---

### Post by lucky_chouhan on 2006-12-08
Hi my modem is Beetel ADSL+2 Modem and my 2 pc are connected with HUB. so my modem LAN port connect to HUB and Hub to my Ubuntu and work fine.(no need any driver)

ip 192.168.0.1 (Modem)
ip 192.168.0.2 (PC)
ip 192.168.0.10 (for LAN Sharing)
ip 192.168.0.11 (My Client Machine)

Internet & Networking fine in Ubuntu & Windows 2003.

:)

---

### Post by travis712 on 2006-12-08
Yeah, I don't know why mine isn't. Pretty sure ubuntu isn't recognizing the lan on my motherboard.

---

### Post by travis712 on 2006-12-09
What else should I try?

---

### Post by hytek on 2006-12-09
travis,

boot into linux, at the console type ifconfig -a

copy that information, reboot into windows, and post the entire output in here.

---

### Post by travis712 on 2006-12-12
travis@ubuntuTRAVSROOM:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:64:CF:16
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xb800

lo        Link encap:Local Loopback
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by travis712 on 2006-12-16
Are you guys stumped or what? Where should I go for more help?

---

