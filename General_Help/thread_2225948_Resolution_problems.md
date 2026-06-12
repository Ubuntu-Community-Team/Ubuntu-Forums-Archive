---
title: "Resolution problems?"
date: 2014-05-24
forum: General Help
---

### Post by themanofboxes on 2014-05-24
I'm very new to linux, and I've installed xubuntu on two systems. One of them I installed alongside windows XP, the other I installed to a hard drive that once had windows vista. The one that had vista has a pretty unusual screen, 1440x900 resolution, so some things won't work with it. After installing xubuntu, it worked fine, but I was having problems with the wired connection(extremely slow page loading[except for google...]) which I may delve into later, but for now, I can't see the screen. After booting up xubuntu, the screen goes black then grey, and I can see a very small section of the taskbar at the top. Occasionally after booting it will flash as well as only show the small section of the taskbar. I tried finding commands I could put into a command line (so I wouldn't have to see what I was doing really) but the only ones I found you had to copy paste something, and I cant do that....
Any help? Thanks.

---

### Post by TheFu on 2014-05-24
If you cannot copy/paste, then start typing.

In order to get better help, you'll need to provide more and specific information about many things.
* which ubuntu release?
* which laptop
* which video card

Often a google for "ubuntu video {insert-your-laptop-model-here}" will find a solution.

---

### Post by themanofboxes on 2014-05-24
Ok, so I figured out it wasn't the monitor's problem, but I started it in recovery mode and changed the resolution. It works fine now.
Except for my other problem, I'll bring that up here.
I have a wired connection going to the computer(desktop), which works for the other computers on the network, and worked with windows vista. When I try opening web pages, it connects but loads EXTREMELY slowly. Google.com and searches work fine(I suspect because they don't use a large amount of html or css) but I can't get anything very complex to load. I tried some opendns tutorial, but it didn't help. (I'm using Firefox for this, but I doubt a different browser would help)

---

### Post by TheFu on 2014-05-24
Please post the output of
* route
* ifconfig
here.
It would also help to know of DHCP is used, the IP of the router and which DNS settings are being used too. [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

---

### Post by TheFu on 2014-05-24
Please post the output of
* route
* ifconfig
here.
It would also help to know of DHCP is used, the IP of the router and which DNS settings are being used too. [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

---

### Post by themanofboxes on 2014-05-24
[COLOR=#000000]when I tried [/COLOR][COLOR=#000000]dmesg |grep eth[0-9][/COLOR][COLOR=#000000][FONT=bitstream vera sans mono], [FONT=arial]there was a big result and at the end it said "no ipv6 routers present(as I expected). I tried to set ipv6 to "ignore" in the network settings I think, but it didn't change anything. also, in firefox I set a thing "disable ipv6" as true or something and nothing happened...[/FONT][/FONT][/COLOR]
[COLOR=#63FF00][FONT=bitstream vera sans mono][/FONT][/COLOR]
[COLOR=#000000](here's the results for ifconfig)
 eth0 Link encap:Ethernet HWaddr 00:1c:25:4d:fd:8f[/COLOR]
[COLOR=#000000] inet addr:192.168.1.102 Bcast:192.168.1.255 Mask:255.255.255.0[/COLOR]
[COLOR=#000000] inet6 addr: fe80::21c:25ff:fe4d:fd8f/64 Scope:Link[/COLOR]
[COLOR=#000000] UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/COLOR]
[COLOR=#000000]  RX packets:11200 errors:467 dropped:0 overruns:0 frame:467[/COLOR]
[COLOR=#000000] TX packets:7595 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=#000000] collisions:0 txqueuelen:1000[/COLOR]
[COLOR=#000000] RX bytes:10707322 (10.7 MB) TX bytes:981629 (981.6 KB)[/COLOR]
[COLOR=#000000] Interrupt:19 Base address:0xdead[/COLOR]
[COLOR=#000000]lo Link encap:Local Loopback[/COLOR]
[COLOR=#000000] inet addr:127.0.0.1 Mask:255.0.0.0[/COLOR]
[COLOR=#000000] inet6 addr: ::1/128 Scope:Host[/COLOR]
[COLOR=#000000] UP LOOPBACK RUNNING MTU:16436 Metric:1[/COLOR]
[COLOR=#000000] RX packets:436 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
[COLOR=#000000] TX packets:436 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=#000000] collisions:0 txqueuelen:0[/COLOR]
[COLOR=#000000] RX bytes:39921 (39.9 KB) TX bytes:39921 (39.9 KB)[/COLOR]

---

