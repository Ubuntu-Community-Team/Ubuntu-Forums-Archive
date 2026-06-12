---
title: "Problem finding server"
date: 2015-01-20
forum: General Help
---

### Post by seagiant on 2015-01-20
Hi,
      I have Ubuntu 14.04 on an HP 15 laptop. I was using a Comcast cable for internet and then a few days ago the computer kept giving me the message"no server found".

 I have checked modem,cable everything I can do to no avail! I have access to wireless in another location and it works and I get the Internet.

 I usually use Mozilla but downloaded Google Chrome to see if that was the problem but no difference?

 Wondering if anyone has any ideas as I have nothing else to try! Thanks!

---

### Post by steeldriver on 2015-01-20
What kind of "server" are we talking about here? are you getting this message in your browser when visiting certain pages? any page? Or are you referring to a remote file server or other remote service?

---

### Post by seagiant on 2015-01-20
Hi,
     Thanks, I guess the server is who I'm getting the Internet connection from (Comcast)

  No, I get no pages what so ever. I get a small message that I am connected but then  the message "server not found" and then no internet. I am now using a wi fi to get on and try to fix the cable problem.

 I'm assuming something happened with Ubuntu as others running Windows have no problem???

---

### Post by mooreted on 2015-01-20
The first thing to always check is your cables. Make sure they are plugged in securely. If you have an extra cable, plug it in and see if it works.

If you open a terminal and enter "ping www.google.com" do you get a response?

---

### Post by seagiant on 2015-01-20
Hi,
     Cable is good. When I ping I get "Unknown Host"

---

### Post by mooreted on 2015-01-20
Could you please open a terminal and post the output of the command "ifconfig"?

In the upper right-hand corner of the screen is the Network Manager icon. On mine it looks like two arrows. Click that, then click "Edit Connections". You should see something like "Wired Connection 1". Select that and click Edit. From here you should be able to see your IP address, default gateway, netmask and DNS servers.

---

### Post by seagiant on 2015-01-20
Hi,
      Thanks!

  RX packets:33427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3109289 (3.1 MB)  TX bytes:234985 (234.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:39386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3870731 (3.8 MB)  TX bytes:3870731 (3.8 MB)

wlan0     Link encap:Ethernet  HWaddr 18:cf:5e:08:1b:a0  
          inet addr:10.0.0.85  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1acf:5eff:fe08:1ba0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:255303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240533 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:245062263 (245.0 MB)  TX bytes:41346174 (41.3 MB)

!

---

### Post by mooreted on 2015-01-20
I see, that is not showing your Ethernet connection. You should be seeing something like this:

eth0      Link encap:Ethernet  HWaddr d4:3d:7e:96:5b:63  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0

What is the output of the command "lspci"?

---

### Post by seagiant on 2015-01-20
[AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1580
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1581
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1582
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1583
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1584
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1585
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
greg@greg-HP-15-Notebook-PC:~$

---

### Post by steeldriver on 2015-01-20
... is it possible the eth0 output from ifconfig simple scrolled off the screen and wasn't copied? try limiting it to just

```

ifconfig eth0

```

---

### Post by mooreted on 2015-01-21
I agree, it shows up in lspci, so your Ethernet card is detected.

Did you check the settings in Network Manager for Ethernet?

---

### Post by seagiant on 2015-01-21
greg@greg-HP-15-Notebook-PC:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr f8:a9:63:92:bd:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:33570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1595 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3128920 (3.1 MB)  TX bytes:259730 (259.7 KB)

greg@greg-HP-15-Notebook-PC:~$

---

### Post by mooreted on 2015-01-21
Yeah, you are not getting an IP address. You need to check Network Manager and your router's settings. Maybe you aren't getting DHCP addresses or something.

---

