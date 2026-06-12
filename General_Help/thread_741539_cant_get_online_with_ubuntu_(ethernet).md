---
title: "cant get online with ubuntu (ethernet)"
date: 2008-03-31
forum: General Help
---

### Post by HeadLikeAHole531 on 2008-03-31
i have a problem getting online on ubuntu, im not sure why it wont work. i have a compaq presario SR1603WM. a 75 gb hard drive with xp installed on it, and another 20 gb hard drive with ubuntu. i have a realtek network card, and i use a linksys wireless router (for a seperate laptop). can anyone help me get online on ubuntu? this is my lspci info:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300 Pro] (Secondary)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem

---

### Post by Rocket2DMn on 2008-03-31
From System->Administration->Network click Wired Connection and go to the Properties button.  Make sure you have "Enable roaming mode" checked.  If that doesn't get you on, please post the output of
```
ifconfig -a
```
Make sure your wired up.

---

### Post by HeadLikeAHole531 on 2008-03-31
this is what i got from ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:13:D4:EA:6B:3E  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2281 (2.2 KB)  TX bytes:5173 (5.0 KB)
          Interrupt:17 Base address:0x2000 

eth0:avah Link encap:Ethernet  HWaddr 00:13:D4:EA:6B:3E  
          inet addr:169.254.7.92  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:880 (880.0 b)  TX bytes:880 (880.0 b)

---

### Post by Rocket2DMn on 2008-03-31
You're not getting a proper IP address, it's using
inet addr:169.254.7.92
Does it allow you to connect using the applet in the toolbar?  You're using a standard patch cable right (not a crossover cable) to connect to the router, yes?
You can try
```
sudo /etc/init.d/networking restart
```
Otherwise, have you tried just rebooting the computer and resetting the router?

I don't think this will provide anything useful, but you can always post the output of
```
sudo lshw -C network
```

---

### Post by HeadLikeAHole531 on 2008-03-31
okay, ill try that first code you put it right now. yeah ive restarted the computer and the modem several times. idk what the applet is that youre talking about though, im pretty new to linux ubuntu.

---

### Post by HeadLikeAHole531 on 2008-03-31
i typed that in and it asked me for "password for dan" but when i tryed to type it in, it wouldnt let me type anything...

---

### Post by Rocket2DMn on 2008-03-31
It is accepting your password, it just doesn't show.  You need to try resetting the router, not the modem (they are normally different).  The router provides your internal IP address.
The Network Monitor applet (nm-applet) usually appears up by the clock on your top panel.  If you don't see it, right click an empty area and hit Add to Panel.  Under the System & Hardware section click Network Monitor and hit add.  You should then be able to right click it and choose to connect to the wired network.

---

### Post by HeadLikeAHole531 on 2008-03-31
well when i went to type it in, it didnt type anything on screen, and when i hit enter it said sorry try again.

---

### Post by Rocket2DMn on 2008-03-31
That means you are typing it out wrong, it just doesn't show that you're typing.  Unless you forgot your password...  Remember, linux is case sensitive.
Have you googled around for similar problems from users with your card?  Have you tried a forum search at all?  I don't have a direct answer for you.  I saw a couple of misc. problems with that card, but nothing solid, so the card probably works OK under linux, you're just missing something.
Have you checked the settings on your wired router?  You may need to file a bug report on [launchpad]("https://launchpad.net/") if you can't get the card to set an IP address.  I'll ask around and see if anybody else has any suggestions for you.

---

### Post by Het Irv on 2008-04-01
Just out of curiosity, does everything work on the XP partition.  If XP does not work, I would try plugging the modem, router and computer and then pugging in the modem first, let it come up, plug in the router, wait and then boot the computer.

If XP does work I would try to reset all of you settings and reentering them.

P.S. If he is going through a router I think that IP address would be correct.  The router will have a public IP that it uses to communicate with the rest of the net.  Its like having a firewall.

---

### Post by Rocket2DMn on 2008-04-01
Take a look here: [http://en.wikipedia.org/wiki/Private_network#Link-local_addresses_.28Zeroconf.29](http://en.wikipedia.org/wiki/Private_network#Link-local_addresses_.28Zeroconf.29)
That address range is reserved for what is technically, an invalid IP.  His linksys router should be assigning 192.168.1.[100-149] I think (with DHCP).

---

### Post by Het Irv on 2008-04-02
```
eth0:avah Link encap:Ethernet HWaddr 00:134:EA:6B:3E
inet addr:169.254.7.92 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:17 Base address:0x2000 
```

I don't know how to read ifconfig that well yet, but would the problem have to do with the subnet mask and the Bcast?
The Subnet is locking in 169.254.whatever.whatever (I think)

---

### Post by Rocket2DMn on 2008-04-02
With dhcp, you shouldn't have to worry about that stuff.  The standard subnet (at least for linksys routers) is 255.255.255.0 and the default gateway is 192.168.1.1 (the same place to you to change router settings).
I'm not sure what Bcast is exactly, it looks like the max IP range or something though.

The OP can try a static IP, but I doubt it will work unless it just happens that DHCP is disabled in the router.  There seems to be a communication problem to the router, like a bad network cable (or wrong type), or perhaps there are settings in the router preventing it from allowing the connection to be made.

---

### Post by Iowan on 2008-04-02
Can you **ping** the router?

---

