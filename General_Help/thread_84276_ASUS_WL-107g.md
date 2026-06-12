---
title: "ASUS WL-107g"
date: 2005-10-30
forum: General Help
---

### Post by Triad on 2005-10-30
Hi,
having problems with my asus wl-107g wireless card.
It seems like it works but it can't retrive a dhcp address.
Anyone with a solution?

regrards
Rickard

---

### Post by tehwa on 2005-10-30
Hi,

This page references the following page to setup the card:

[https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo)

However, you may have already done similar to get it running.

Post the output of ```
ifconfig
iwconfig
```
And the contents of```
/etc/networking/interfaces
```This will please the mighty gods of wireless.

edit: more info

---

### Post by Triad on 2005-11-02
Hi here is the info.
I can see on the router that the computer has connected but can't get a ip address.

#ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:744 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:66107 (64.5 KiB)  TX bytes:66107 (64.5 KiB)

ra0       Link encap:Ethernet  HWaddr 00:0E:A6:A8:D4:B9
          inet6 addr: fe80::20e:a6ff:fea8:d4b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:9 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:48162 (47.0 KiB)
          Interrupt:11 Base address:0x8000


#iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"XXXXX"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0F:CB:9E:63:B2
          Bit Rate:48 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=55/100  Signal level=-82 dBm  Noise level:-195 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map wlan0

# The primary network interface
iface wlan0 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid XXXXX
        wireless-key1 XXXXXXXXXXXXXXXXXXXXXXXXXXXX
        wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXXX

auto wlan0

iface ra0 inet dhcp
wireless-essid XXXXX
wireless-key s:XXXXXXXXXXXXXXXXXXXXX

auto ra0

#lsmod | grep 2500
rt2500                175492  1


any ideas?

Regards
Rickard

---

