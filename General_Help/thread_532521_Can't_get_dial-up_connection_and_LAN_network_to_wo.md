---
title: "Can't get dial-up connection and LAN network to work simultaneously"
date: 2007-08-22
forum: General Help
---

### Post by Aya Dream on 2007-08-22
I don't know what's going on! I got dial-up access to the internet working but my LAN wasn't working. Changed some settings in network manager and the LAN worked but the dial-up access to the net didn't work! Played around a bit more and got both working....hurray. Shut down for what was left of the night and re-booted the next morning and nothing worked; neither the dial-up or the LAN!

I've got two PC's; a desktop (host) and laptop (client), both originally with WindowsXP SP2 on their C drives. The desktop has 4 hard drives 2x PATA (C: & D and 2x SATA (R: & S. Laptop was/is networked to desktop via Windows ICS. My access to the net is via a winsoft dial-up modem in the desktop and my HP printer is attached to the desktop via USB connection. Under WinXP all file & printer sharing and internet access works perfectly on both machines.

Now, I've installed Ubuntu Linux Feisty Fawn 2.6.20-16 Generic. I downloaded free HSFModem driver (from Linuxant), Gnome-PPP and Samba. I get internet access via gnome-ppp ok (this thread being written in Firefox on Feisty).

The only way I seem to be able to get access to the laptop is if I use static addresses in the 'wired connection' properties of network manager.

If I use DHCP I can't see the laptop (which is using a static IP address 192.168.0.230) If I use static IP's assigning 192.168.0.1 to the Linux running on the desktop then the dial-up modem connects to the ISP but doesn't communicate with it. That may sound a bit of a tautology but I can ping the ISP but not their corresponding DNS's or any other IP address for that matter.

Here's the ifconfig as of now:

t# ifconfig
eth0 Link encap:Ethernet HWaddr 00:18:F3:14:A8A
inet6 addr: fe80::218:f3ff:fe14:a8da/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:107 errors:0 dropped:0 overruns:0 frame:0
TX packets:247 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:10094 (9.8 KiB) TX bytes:41075 (40.1 KiB)
Interrupt:19 Base address:0xc400

eth0:avah Link encap:Ethernet HWaddr 00:18:F3:14:A8A
inet addr:169.254.9.29 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:19 Base address:0xc400

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:203 errors:0 dropped:0 overruns:0 frame:0
TX packets:203 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:21440 (20.9 KiB) TX bytes:21440 (20.9 KiB)

ppp0 Link encap:Point-to-Point Protocol
inet addr:210.5.88.150 P-t-P:210.213.255.6 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1500 Metric:1
RX packets:3414 errors:0 dropped:0 overruns:0 frame:0
TX packets:3789 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:3
RX bytes:2032509 (1.9 MiB) TX bytes:411045 (401.4 KiB)

How do I get the linux desktop to see the laptop and vica versa and how do I get the laptop to access the net and print through the desktop? I must be doing something insanely stupid. Apologies for having to bother you guys; as I said I thought I had it cracked only for all my hard work to be wiped out on the shutdown and re-boot.

---

### Post by Aya Dream on 2007-08-23
When I click on Network Monitor I get the following message:  "Could not find information on interface 'eth0:avahi' in /proc/net/dev". But in Network Manager I'm using 'Static IP address" ???

Can anybody point me in the right direction to resolve this issue

Thx

---

