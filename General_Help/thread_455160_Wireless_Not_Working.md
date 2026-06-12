---
title: "Wireless Not Working"
date: 2007-05-26
forum: General Help
---

### Post by theaverageidiot on 2007-05-26
I have a Dell XPS laptop. In Ubuntu 6.10, it never even recognized my wireless card at all. Well, I just installed 7.04 and I had to plug it in (it's a very big hassle because of the location of my plug-in), because I can't connect to any wireless networks. In 7.04 at least it recognizes I have a wireless network but it acts like there's no access points near to connect to and I'm 100% that I'm in range and all.

Can someone help me?

---

### Post by nemarasu on 2007-05-26
does your WAP use encryption, or is it wide open?  make sure you matching the settings of your WAP?

---

### Post by ugm6hr on 2007-05-26
> **theaverageidiot said:**
> I have a Dell XPS laptop. In Ubuntu 6.10, it never even recognized my wireless card at all. Well, I just installed 7.04 and I had to plug it in (it's a very big hassle because of the location of my plug-in), because I can't connect to any wireless networks. In 7.04 at least it recognizes I have a wireless network but it acts like there's no access points near to connect to and I'm 100% that I'm in range and all.

Can someone help me?

Probably :)  But I'm a beginner myself...

Couple of things to try / ask:

How do you know it recognises a wireless network?

Try "enable roaming mode" and the enable Network Manager networking and wireless facilities.

If above doesn't work - in Terminal:
*lspci* (to look for what type of Wireless card you have - look for Ethernet or Network controller)
*ifconfig* (to look for network setup)
*iwconfig* (to look for wireless setup)

And then post the results here - I may be able to help (but it might prompt someone else).

---

### Post by theaverageidiot on 2007-05-26
The network is simply called linksys. It has WEP encyprtion.

```
josh@josh-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

```
josh@josh-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:**:**:**  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: ****::***:****:****:****/** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17917 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23720809 (22.6 MiB)  TX bytes:1499615 (1.4 MiB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71952 (70.2 KiB)  TX bytes:71952 (70.2 KiB)
```

```
josh@josh-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by ugm6hr on 2007-05-26
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

That's the wireless card.  I know there are loads of threads devoted to getting broadcom cards to work with Feisty - just search in this forum for broadcom 4306.

---

### Post by theaverageidiot on 2007-05-26
In case anyone else has my problem, I used this guide here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)
And now it works perfectly.

Thank you people who posted here, or I wouldn't have found that guide ;).

---

