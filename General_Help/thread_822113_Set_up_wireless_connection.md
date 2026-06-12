---
title: "Set up wireless connection"
date: 2008-06-07
forum: General Help
---

### Post by rated_emman on 2008-06-07
HI guys! i have a HP pavilion dv2000 that is currently running Windows Vista and Linux 8.04 hardy heron...

I just need help on how to make my wireless internet work :(

thanks in advance guys!

---

### Post by tramir on 2008-06-07
We need more information: what network adapter do you have? do you have a secure connection (WEP/WAP)?

---

### Post by avtolle on 2008-06-07
Go to the terminal (Applications>>Accessories>>Terminal) and after signing in with your name and password (which will not show), enter```
lspci
``` and post the results so we may determine which wireless card is in your box.

---

### Post by rated_emman on 2008-06-07
i have a secure WEP connection on my wireless

[PHP]emmanuel@emmanuel-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:f2:1c:d0  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fef2:1cd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4950677 (4.7 MB)  TX bytes:369048 (360.3 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9228 (9.0 KB)  TX bytes:9228 (9.0 KB[/PHP]

[PHP]emmanuel@emmanuel-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

emmanuel@emmanuel-laptop:~$ 
[/PHP]

and im not so sure how to know what kind of wireless adapter i have

---

### Post by rated_emman on 2008-06-07
> **avtolle said:**
> Go to the terminal (Applications>>Accessories>>Terminal) and after signing in with your name and password (which will not show), enter```
lspci
``` and post the results so we may determine which wireless card is in your box.

ok i did what u said and here's the result:

[PHP]emmanuel@emmanuel-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
emmanuel@emmanuel-laptop:~$ 

[/PHP]

thanks

---

### Post by lp42860 on 2008-06-07
Not sure if I'm in the right place, but I need don't have wirelessfix.sh in my filesystem. I just installed Xubuntu Hardy and was following a guide to get ndiswrapper running when told to edit this filed. I don't have it on my system. Please help. I'm new to the forum, so please excuse my lack of knowledge about how it works.

---

### Post by rated_emman on 2008-06-08
> **avtolle said:**
> Go to the terminal (Applications>>Accessories>>Terminal) and after signing in with your name and password (which will not show), enter```
lspci
``` and post the results so we may determine which wireless card is in your box.

i did what you said.. here's the result:

```
emmanuel@emmanuel-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
emmanuel@emmanuel-laptop:~$  
```

---

### Post by rated_emman on 2008-06-10
> **rated_emman said:**
> i did what you said.. here's the result:

```
emmanuel@emmanuel-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
emmanuel@emmanuel-laptop:~$  
```

anybody wanna help me plzz? thanks you guys!
thanks for all the help but pretty plz i need help with this one :-s

---

### Post by Kinnza on 2008-06-10
ok can i see:

```

sudo lshw -C network

```

---

### Post by rated_emman on 2008-06-10
> **Kinnza said:**
> ok can i see:

```

sudo lshw -C network

```

this is what i get:

```
emman@emmanuel-laptop:~$ sudo lshw -C network
[sudo] password for emman: 
PCI (sysfs)  


```

thanks

---

### Post by slayer^_^ on 2008-06-11
> 01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

you can find almost everything in google!

First install the package "b43-fwcutter" from Synaptic package manager or

```
sudo apt-get install b43-fwcutter
```

then take a look here:

[http://ubuntuforums.org/showpost.php?p=4017142&postcount=6](http://ubuntuforums.org/showpost.php?p=4017142&postcount=6)

Best regards ;)

---

### Post by crazyness003 on 2008-06-13
Hey man. I have the EXACT card as you, with an hp pavilion tx1000 series.

You gotta tel me what version of ubuntu you're using and the kernel
go to the terminal (menu->Accessories->Terminal) and type this in

```

uname -a

```

This will give some useful info about your kernel. If it says something like 2.6.24-19, they you are very close to getting it working.

---

### Post by soccerush10 on 2008-07-06
What happens after you get this information?  How does knowing the kernel help in this cenario?

---

### Post by soccerush10 on 2008-07-06
> **crazyness003 said:**
> Hey man. I have the EXACT card as you, with an hp pavilion tx1000 series.

You gotta tel me what version of ubuntu you're using and the kernel
go to the terminal (menu->Accessories->Terminal) and type this in

```

uname -a

```

This will give some useful info about your kernel. If it says something like 2.6.24-19, they you are very close to getting it working.
What happens after you get this information? How does knowing the kernel help in this cenario?

---

### Post by chetan.89 on 2008-07-06
I'm new to Ubuntu as well and managed to set up my wireless connection.

Go to System-->Help and Support and there must be a way given to connect to your wireless network. Just refer it and follow the steps. That should do, unless your wireless network is too complicated :).

---

### Post by crazyness003 on 2008-07-06
> **soccerush10 said:**
> What happens after you get this information? How does knowing the kernel help in this cenario?

The kernel version is important since, 2.6.24-19 fixed the BCM4311 bug and so the devs integrated it into the kernel. That means if you have that particular wi-fi card that the OP has, and you have the newest released kernel version (2.6.24-19), all you need to do is go to the restricted drivers and enable it. 

Wi-fi out of the box ;)

If you need help with your wifi, I highly recommend going to this thread
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
There are some very dedicated people waiting to help you, or just post some info here. im no expert, but i'll try to help

---

