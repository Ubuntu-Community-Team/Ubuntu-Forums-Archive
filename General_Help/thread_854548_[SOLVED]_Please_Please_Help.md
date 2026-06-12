---
title: "[SOLVED] Please Please Help"
date: 2008-07-09
forum: General Help
---

### Post by r3a7amd on 2008-07-09
Hi there,

I'm a newbie and would like to explore the Linux world, but before doing that i need to install Ubuntu and to do that i got to solve these issues, which i have no idea as what to do, so i came here to seek help from experts and experienced users.

1st issue: I can install the Ubuntu perfectly and everything working like a charm except one thing! My wireless connection.

2nd issue: I installed it on VMWare ver. 6.x and this time wireless connection works but when i open a new application such as Firefox the mouse disappears behind the application and wont respond at all.

My Computer:
Dell XPS M1530
Intel Core 2 Duo Processor T8300 (2.4GHz/800MHzFSB, 3M L2 Cache)
Windows Vista 32bit
256MB NVIDIA GeForce 8600M GT
Dell Wireless 1505 Wireless-N Mini-card

Thanks in advance.

---

### Post by chalewa on 2008-07-09
> **r3a7amd said:**
> Hi there,

I'm a newbie and would like to explore the Linux world, but before doing that i need to install Ubuntu and to do that i got to solve these issues, which i have no idea as what to do, so i came here to seek help from experts and experienced users.

1st issue: I can install the Ubuntu perfectly and everything working like a charm except one thing! My wireless connection.

2nd issue: I installed it on VMWare ver. 6.x and this time wireless connection works but when i open a new application such as Firefox the mouse disappears behind the application and wont respond at all.

My Computer:
Dell XPS M1530
Intel Core 2 Duo Processor T8300 (2.4GHz/800MHzFSB, 3M L2 Cache)
Windows Vista 32bit
256MB NVIDIA GeForce 8600M GT
Dell Wireless 1505 Wireless-N Mini-card

Thanks in advance.

can you give the output of 

```
lspci
```

```
lsusb
```

---

### Post by r3a7amd on 2008-07-09
lspci command:
> ahmad@ahmad-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
ahmad@ahmad-laptop:~$ 


lsusb command:
> ahmad@ahmad-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 005 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 005 Device 003: ID 413c:8126 Dell Computer Corp. 
Bus 005 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 045e:071f Microsoft Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 0000:0000  
ahmad@ahmad-laptop:~$ 


---

### Post by Gunman1982 on 2008-07-09
Maybe this can help [http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4]("http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4")

---

### Post by Taxman415a on 2008-07-09
That Broadcom 4328 wireless card is going to require ndiswrapper to get working. Broadcom is famously bad at providing the specs and so forth that developers need to write opensource drivers for their consumer level chips.

The Macbook SantaRosa has the same chip, so you can follow the instructions here to get the wireless working:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by r3a7amd on 2008-07-09
> **Gunman1982 said:**
> Maybe this can help [http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4]("http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4")

Gunman: thanks but this did not work for me. that was for Ubuntu version 7, mine is 8.04

---

### Post by Gunman1982 on 2008-07-09
> **r3a7amd said:**
> Gunman: thanks but this did not work for me. that was for Ubuntu version 7, mine is 8.04

Did you try it or did you already quit just because of the different version? If you tried: what didn't work?

---

### Post by r3a7amd on 2008-07-09
> **Gunman1982 said:**
> Did you try it or did you already quit just because of the different version? If you tried: what didn't work?
yes i did try it, i finished all the steps and still  i dont see anything, here is a pictures.

Taxman, that did not work either.

[IMG]http://i37.tinypic.com/15oh2eh.png[/IMG]

---

### Post by r3a7amd on 2008-07-09
Should I just give up with linux and go back to windows?

---

### Post by Taxman415a on 2008-07-09
> **r3a7amd said:**
> yes i did try it, i finished all the steps and still  i dont see anything, here is a pictures.

Taxman, that did not work either.


I didn't reallize he had posted basically the same steps. But we can't really help you unless you give us more information about the output of the commands those guides had you try. Did any of them give you errors? What is the output of 
sudo ndiswrapper -l

after you do the other steps? How about 
ifconfig -a

---

### Post by r3a7amd on 2008-07-10
> **Taxman415a said:**
> I didn't reallize he had posted basically the same steps. But we can't really help you unless you give us more information about the output of the commands those guides had you try. Did any of them give you errors? What is the output of 
sudo ndiswrapper -l

after you do the other steps? How about 
ifconfig -a

Ok, let me try those commands, i'll be back with those soon.

---

### Post by r3a7amd on 2008-07-10
Here are the results of both those commands you gave me:
> ed@ed-laptop:~$ sudo ndiswrapper -l
[sudo] password for ed: 
bcmwl5 : driver installed
	device (14E4:4328) present
ed@ed-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:09:4f:9f:80  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe4f:9f80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:831 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1421785 (1.3 MB)  TX bytes:90351 (88.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2903 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:146459 (143.0 KB)  TX bytes:146459 (143.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:a1:9c:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f9efc000-f9f00000 

ed@ed-laptop:~$ 


note: now i connected to internet using a wired connection.

---

### Post by Taxman415a on 2008-07-10
Ok, I just tried it with my laptop and it works fine and I see from your output above that ndiswrapper installs the driver just fine. I'm not sure what program you're bringing up in your screenshot to see the wireless networks, but just try the icon in between the sound icon and the battery icon. That's the network status applet. Right click on that and you should see the available wireless networks. Click on an open one and it should auto configure it for you. That applet lets you switch easily between wired and wireless networks.

Incidentally I have no idea about the vmware issue. You'll probably want to list that as a separate question with a good descriptive subject and include all the details you can.

---

### Post by r3a7amd on 2008-07-11
hey man guess what happened?

i been trying since last night to find another solution because when you said click on the icon between sound and batter i did but i still couldnt see the wireless connections. so this morning i took some screen shot to put here and show you, all of sudden i look at the top and i see that i connected to internet wireless. how awesome is that?!

anyways thank for your help, now i dont have to go back to windows.:lolflag:

---

