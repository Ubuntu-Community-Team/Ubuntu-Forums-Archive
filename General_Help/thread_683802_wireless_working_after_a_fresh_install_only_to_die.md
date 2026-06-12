---
title: "wireless working after a fresh install only to die after a day or two."
date: 2008-01-31
forum: General Help
---

### Post by midnex on 2008-01-31
wireless working after a fresh install only to die after a day or two. how to fix?

---

### Post by faulkes on 2008-01-31
> **midnex said:**
> wireless working after a fresh install only to die after a day or two. how to fix?

Could you provide additional details:

1. Type of wireless card (model/version/driver)

2. Output of "lspci"

3. Output of "iwconfig"

4. Output of "sudo iwlist ethX scan"
 - where ethX is your wireless card device (usually eth1)

Also, could you be more descriptive of what you mean by "die"? does it simply stop working? do any errors occur? check /var/log/messages or dmesg 
Faulkes

---

### Post by midnex on 2008-01-31
> **faulkes said:**
> Could you provide additional details:

1. Type of wireless card (model/version/driver)

2. Output of "lspci"

3. Output of "iwconfig"

4. Output of "sudo iwlist ethX scan"
 - where ethX is your wireless card device (usually eth1)

Also, could you be more descriptive of what you mean by "die"? does it simply stop working? do any errors occur? check /var/log/messages or dmesg 
Faulkes

Matau buvo panasi tema bet inai man nepadejo taigi galit padet puslapiu neuzkrauna ir kitu bet kai pinginu tai atsako :/ ir skype veikia kas ce galetu but ? D:

"ip a"
1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
inet 127.0.0.1/8 scope host lo
inet6 ::1/128 scope host 
valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
link/ether 00:13:d3:9a:16:cd brd ff:ff:ff:ff:ff:ff
inet6 fe80::213:d3ff:fe9a:16cd/64 scope link 
valid_lft forever preferred_lft forever
5: ppp0: <POINTOPOINT,MULTICAST,NOARP,UP,10000> mtu 1492 qdisc pfifo_fast qlen 3
link/ppp 
inet 78.56.207.119 peer 213.190.60.229/32 scope global ppp0

"ip r"
213.190.60.229 dev ppp0 proto kernel scope link src 78.56.207.119 
default dev ppp0 scope link 

"cat /etc/resolv.conf"
nameserver 212.59.0.1
nameserver 212.59.0.2


"wget --no-proxy takas.lt"
--20:35:31-- [http://takas.lt/](http://takas.lt/)
=> `index.html'
Resolving takas.lt...

---

### Post by donn29 on 2008-01-31
I too am having an issue, I installed the fireware for my broadcom 43xx in my HP

```
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
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

The last command doesn't show anything, for the eth1 that seems to have disappeared. or lo or eth0.  
The wireless does still work in windows(ugh) however.

I get: from dmesg.  If I CRTL+ALT+F8, i get the same thing that is constantly scrolling with the first number changing.  
```
[ 1467.740000] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
```

---

### Post by faulkes on 2008-01-31
ok, well, the pci bridge knows about the wireless card.

Lets see if the driver is actually loaded and running

/sbin/lsmod | grep 43

or (I think)

/sbin/lsmod | grep bcm 

That should let us see the kernel module if it's loaded.

---

### Post by midnex on 2008-02-01
> **faulkes said:**
> ok, well, the pci bridge knows about the wireless card.

Lets see if the driver is actually loaded and running

/sbin/lsmod | grep 43

or (I think)

/sbin/lsmod | grep bcm 

That should let us see the kernel module if it's loaded.

       
nls_cp437               6784  1 
snd_timer              24324  2 snd_pcm,snd_seq
thermal                14344  0

---

### Post by faulkes on 2008-02-01
Ok, so it looks like the broadcomm kernel driver isn't loaded.  Which may mean you are using the ndiswrapper based driver.

Try

```

/sbin/lsmod | grep ndis

```

and let me know what if anything it returns.

Faulkes

---

### Post by midnex on 2008-02-01
> **faulkes said:**
> Ok, so it looks like the broadcomm kernel driver isn't loaded.  Which may mean you are using the ndiswrapper based driver.

Try

```

/sbin/lsmod | grep ndis

```

and let me know what if anything it returns.

Faulkes

anything returns :(

---

### Post by faulkes on 2008-02-01
Interesting, so it would seem that there is no driver loaded for the wireless card (that I can tell).

Lets start at the beginning, so to speak.  You say that wireless was working after a fresh install but dies after a day or two.

When was the last time wireless was working and when was the last time you rebooted?

Go to System->Administration->Restricted Driver Manager, there should be a listing there for the broadcomm 43xx wireless chipset.  Don't change anything there, just let me know if it's enabled or not.

Faulkes

---

### Post by midnex on 2008-02-01
> **faulkes said:**
> Interesting, so it would seem that there is no driver loaded for the wireless card (that I can tell).

Lets start at the beginning, so to speak.  You say that wireless was working after a fresh install but dies after a day or two.

When was the last time wireless was working and when was the last time you rebooted?

Go to System->Administration->Restricted Driver Manager, there should be a listing there for the broadcomm 43xx wireless chipset.  Don't change anything there, just let me know if it's enabled or not.

Faulkes

ther nodrivers restricted. btw is lie disapear 1-2days maybe ny modem problem D:?
ok i have instaled ubuntu abaut 6days ago and i'm seting sudo pppoeconf its vorked perfectly loads sites and etc. but next day dont load sites...skype is vorking maybe u have skype its will be faster becose i'm tired to rebot my pc :/

---

### Post by faulkes on 2008-02-01
Ok, lets start even more basic

output of:
```

uname -a

and

cat /etc/issue

```

When you installed, did you install the desktop or server edition? 32bit or 64bit? 

Basicly right now, I don't see any drivers installed which would enable your wireless card to work - the above information will (and anything else you can think of) will let me help you better.

I do however have to go to sleep, so hopefully someone else can help pick this up, if not, I will follow the thread when I get up.  I do understand that it can be frustrating, I don't have a mic for skype so I havent installed the application.

Faulkes

---

