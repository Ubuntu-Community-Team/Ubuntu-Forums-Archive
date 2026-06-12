---
title: "extremely slow when USB Wireless device attached pre-boot"
date: 2007-09-29
forum: General Help
---

### Post by kiazoe on 2007-09-29
Hi all, 

Not sure what information will help but I think this should be enough:
  ubuntu 7.04 Feisty Fawn (GNOME 2.18.1)
  Athlon XP 2000+
  1024MB RAM
  Wireless adapter: belkin F5D7050uk v3001 USB Wireless G Network Adapter

Whenever I boot ubuntu without the wireless adapter attached ubuntu boots quickly and is very responsive as expected. 

However, when I boot with this adapter attached the machine boots a lot slower, and once the GUI has loaded everything is extremely slow - for example typing my username takes about 45-60 seconds to show and compute.

I have tried attaching other usb devices such as thumb drives / external hdd's and there are no issues with the speed / responsiveness.

The wireless adapter works perfectly once it has been attached after boot by the way.

Hope someone can clear this up for me - worth noting I'm a beginner with ubuntu / linux in general so go easy :) 

Any more information needed please let me know.

Thansk in advance,
Eoin.

---

### Post by kiazoe on 2007-09-29
Thought I should clarify, this is NOT a wireless connection problem - i'm assuming the topic having wireless in the title is causing it to be ignored :(

Any suggestions, however crazy, are welcome

---

### Post by dcstar on 2007-09-29
> **kiazoe said:**
> Hi all, 

Not sure what information will help but I think this should be enough:
  ubuntu 7.04 Feisty Fawn (GNOME 2.18.1)
  Athlon XP 2000+
  1024MB RAM
  Wireless adapter: belkin F5D7050uk v3001 USB Wireless G Network Adapter

Whenever I boot ubuntu without the wireless adapter attached ubuntu boots quickly and is very responsive as expected. 

However, when I boot with this adapter attached the machine boots a lot slower, and once the GUI has loaded everything is extremely slow - for example typing my username takes about 45-60 seconds to show and compute.
.............
Hope someone can clear this up for me - worth noting I'm a beginner with ubuntu / linux in general so go easy :) 

Any more information needed please let me know.

Thansk in advance,
Eoin.

Possibly it is your system trying to use the Wireless networking device for DNS lookups before it is actually functional with a working connection - and the "slowness" are the timeouts before it gives up waiting for a response.

You may be able to get around this by altering your networking configuration - a forum search may provide some answers as other people have previously reported similar things when their network connections are down.

---

### Post by kiazoe on 2007-09-30
Okay, I managed to get the machine booting normal speeds with the device attached - but at the expense of my net connection.

The wireless adapter is now seeing the router but will not connect. I'm not sure what information is required, but here's a load of stuff that I'm sure will help somebody...

/etc/hosts
> 127.0.0.1 localhost eoin-ubuntu
127.0.1.1 eoin-ubuntu

ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:40:CA:2C:45:B8
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:900 (900.0 b)  TX bytes:900 (900.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:17:3F:AD:9F:5F
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15382 (15.0 KiB)  TX bytes:1178 (1.1 KiB)

iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"dd-wrt-eoin"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:4B:D7:E8
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ndiswrapper -l
> rt73 : driver installed
        device (050D:705A) present (alternate driver: rt73usb)

I have tried to remove this and blacklist it so I'm not using the alternate driver...

/etc/modprobe.d/blacklist
> blacklist rt73usb

I changed a line in aliase:
/etc/modprobe.d/aliases
> alias net-pf-10 off

/etc/network/interfaces
> auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


Hope someone can shed some light - also, this can be moved to 'Networking & Wireless' category.

Thanks in advance, 
Eoin

---

