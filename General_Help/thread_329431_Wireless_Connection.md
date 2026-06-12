---
title: "Wireless Connection"
date: 2007-01-01
forum: General Help
---

### Post by NGEvo on 2007-01-01
](*,) 

Hi, this is the 4th time I've attempted to go with linux, I chose Ubuntu, its looking AWESOME. But...

I have a problem, I have configured my Laptops WiFi card accordingly, and Network Monitor is indicating 95% signal, but, no internet, nada, I tried loading my Router, nothing, Google, Nothing, pinging doesn't work either, it says "Unknown Host" for everything......

Help please!

NG

---

### Post by EnterDaMatrix on 2007-01-01
What kind of card? How did you configure it? Specs? Etc?

---

### Post by NGEvo on 2007-01-01
Its a Intel Intergrated card, I didn't have to do anything, I put in my SSID and WEP, and i'm connected (apparently) but I can't do anything, net-wise, not even ping..

:(

---

### Post by EnterDaMatrix on 2007-01-01
Try to disable the LAN connection. Some people have trouble with it also enabled. Do you know the card chipset?

---

### Post by NGEvo on 2007-01-01
Aha, I think Network Monitor is takin the p*ss, its says that, but My Router is telling me only my Windows machine is connected, nothing else....???

What do I do?

---

### Post by NGEvo on 2007-01-01
I'm not sure, something like a 2200 BG, but I can't be sure, it worked with Kubuntu before (Dapper) now I'm usung Ubuntu (Edgy) and not doing too good...

---

### Post by NGEvo on 2007-01-01
disabled LAN, no differance, and I'm monitoring eth1, just for you to know....

---

### Post by EnterDaMatrix on 2007-01-01
The WM3B2200BG Intel chipset is listed as compatible. The default configuration utilities aren't so great, you may want to try installing netapplet or network-manager to aide with selected networks. Also are you trying to connect to an encrypted network or an open one?

---

### Post by EnterDaMatrix on 2007-01-01
> **NGEvo said:**
> disabled LAN, no differance, and I'm monitoring eth1, just for you to know....

eth1 is the LAN card. The wifi card should show up as wlan0, not eth1. Is this the case or did I misunderstand?

---

### Post by NGEvo on 2007-01-01
Encrypted, and I'm not sure, wlan0,1 and 2 indicate as non-existant, so eth1 must be it...

---

### Post by NGEvo on 2007-01-01
and I can't install anything without the net..

---

### Post by EnterDaMatrix on 2007-01-01
Please give the output of:

```
lscpi -n
```

---

### Post by EnterDaMatrix on 2007-01-01
Oh! It would be a very good idea to temporarily plug the laptop into the router and update the entire system. It's very likely that your problem has been solved in a newer kernel or update. I would always do this first.

---

### Post by NGEvo on 2007-01-01
doesnt work... command not found.

(terminal, right?)

---

### Post by vigleik on 2007-01-01
That should be lspci, not lscpi.

---

### Post by phossal on 2007-01-01
Try issuing the following where wlan0 is the appropriate interface:
```

sudo dhclient wlan0 

```

If you're unsuccessful, post the output. In addition, post the output from:
```

sudo iwconfig 

```

When dealing with network connections, I recommend disabling wep/wpa on wireless routers, and avoiding the gui tools. Definitely review the man pages for the following commands: 
ifconfig, iwconfig, ifup, ifdown, dhclient, dmesg. They're extremely helpful, if not necessary,  once your hardware is properly installed.

---

### Post by NGEvo on 2007-01-02
OK, I connected it to LAN, but I couldn't load ANY site unless I pinged it first... :confused: 

Help!

:-k

---

### Post by NGEvo on 2007-01-02
Here the output you wanted...

lspci -n

```

ubuntu@ubuntu-laptop:~$ lspci -n
00:00.0 0600: 1002:5830 (rev 02)
00:01.0 0604: 1002:5838
00:13.0 0c03: 1002:4347 (rev 01)
00:13.1 0c03: 1002:4348 (rev 01)
00:13.2 0c03: 1002:4345 (rev 01)
00:14.0 0c05: 1002:4353 (rev 18)
00:14.1 0101: 1002:4349
00:14.3 0601: 1002:434c
00:14.4 0604: 1002:4342
00:14.5 0401: 1002:4341
00:14.6 0703: 1002:434d (rev 01)
01:05.0 0300: 1002:5835
02:05.0 0607: 1180:0476 (rev ac)
02:05.1 0607: 1180:0476 (rev ac)
02:05.2 0c00: 1180:0552 (rev 04)
02:06.0 0200: 10ec:8139 (rev 10)
02:07.0 0280: 8086:4220 (rev 05)


```

iwconfig

```

ubuntu@ubuntu-laptop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:"SCALPER"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:9A:12:D5:16   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=93/100  Signal level=-34 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:75560  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:97   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.



```

dhclient eth1

```

ubuntu@ubuntu-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0e:35:81:96:50
Sending on   LPF/eth1/00:0e:35:81:96:50
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

I need this workin! Ubuntu!

NG

---

### Post by phossal on 2007-01-02
NG, I put [edited] in this case because I can't begin to put boundaries on the problem. In fact, after reading your post (that follows this), I'm discouraged from even making suggestions. I much prefer to let those with a strong hunch guide you than to offer random suggestions. Sorry.

---

### Post by NGEvo on 2007-01-02
Edited?

Anyway, I have a problem now, if I ping 2 Places at the same time, if I go to one ([www.ubuntu.com](www.ubuntu.com)) It will load another... ([www.google.com](www.google.com)) and If I search something, it goes to 404 Not Found, at Ubuntu.org :confused: 

Anyway, this is really getting to me, what the heck is going on??? All I want is the internet...

:-k 
:( 

NG

---

### Post by NGEvo on 2007-01-02
Woohoo!

Internet Browsing : Solved!

Listen up, it seemed to be a SEVERE case of the IPv6 problem, instead of slow, nothing whatsoever, I can now browse ANY site, connected to LAN!

OK, lets return to the subject in hand, Wirelessness....

And oh, I'm doing a full system upgrade, all sorts, OO.org, Kernal Headers, Mono and more...

If that doesn't clear thinks up, I'll install WiFi Radar, if that has no help, it'll be something more advanced..

Good plan?? :neutral: 

NG

---

### Post by NGEvo on 2007-01-02
Synaptic did its thing, but when it finished, froze GNOME completely....

I executed

```

shutdown -P 1

```

I hope I did the right thing... :-k 

Is there a GNOME refresh / reboot combo?

NG

---

### Post by NGEvo on 2007-01-02
> **NGEvo said:**
> Synaptic did its thing, but when it finished, froze GNOME completely....

I executed

```

shutdown -P 1

```

I hope I did the right thing... :-k 

Is there a GNOME refresh / reboot combo?

NG

It's alright (phew) and booted without a problem. (Now theres something you don't see everyday with Windows! :D )

Anyway, the Laptop is on Charge, then I'm gonna unplug, bring to the Router, and get the other Wi Fi tools...

Any suggestions?

---

### Post by NGEvo on 2007-01-02
:( 
](*,) 

WHY!?!?!!?!??!?

It say's its connected, BUT IT JUST ISN'T! I've used Wi-Fi Assistant (on Gnome i'm sure if thats wise) that says connection failed??? and Wifi Radar is just plain USELESS....

What can I do? (The network is open too)

Help PLEASE!

NG

---

### Post by NGEvo on 2007-01-02
Hello?????

Anyway,  I followed this guide :-

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

and theres good news, I am connected to the network....... the 4.2.2.2 ping was successfull, but I can't access, erm, anything else... help? (Anyone there?)

NG

---

### Post by nutz on 2007-07-07
> **NGEvo said:**
> Hello?????

Anyway,  I followed this guide :-

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

and theres good news, I am connected to the network....... the 4.2.2.2 ping was successfull, but I can't access, erm, anything else... help? (Anyone there?)

NG


LOL, this is the funniest ending to a thread ever.

I will be working with this card later tonight and I will share myresults.

---

