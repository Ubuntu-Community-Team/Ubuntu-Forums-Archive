---
title: "Internet Speed"
date: 2015-03-18
forum: General Help
---

### Post by gabmuks on 2015-03-18
Hello and good day.


I am just curious as to why the internet seems so slow with Ubuntu.

I have Windows and Ubuntu 14 on the same computer.

But the internet using Windows is at least 10 times faster than

with Ubuntu. I am not complaining at all, just curious

since in the past, Ubuntu always seemed quicker than Windows.

---

### Post by dino99 on 2015-03-18
thats a huge gap ;)
nothing logged ?

---

### Post by nerdtron on 2015-03-18
More info needed like computer specs, hardware (wifi or LAN card) model.

Also probably a speedtest result on both OS can give an idea on how much really slow is other one.

---

### Post by gabmuks on 2015-03-18
> **nerdtron said:**
> More info needed like computer specs, hardware (wifi or LAN card) model.

Also probably a speedtest result on both OS can give an idea on how much really slow is other one.

Sounds good.

How do I do the speed testing?

---

### Post by nerdtron on 2015-03-18
Internet speed right? [www.speedtest.net](www.speedtest.net)

---

### Post by gabmuks on 2015-03-18
Here is some info...

Memory 3.8 GiB
Processor intel Core2 Duo
CPU E6550 @ 2.33GHz x 2
GeForce 210
OS Type 64-bit



 *-network               
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1f:29:3d:c6:34
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=1.1-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:f3100000-f311ffff memory:f3124000-f3124fff ioport:2100(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlan0
       serial: 
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.13.0-46-generic firmware=0.29 ip=10.0.0.6 link=yes multicast=yes wireless=IEEE 802.11bgn

> **nerdtron said:**
> Internet speed right? [www.speedtest.net]("http://www.speedtest.net")

I just did the [WWW.speedtest.net](WWW.speedtest.net).

The two tests are within 1/10th Mbps of each other.

The difference in speed that I notice is that it takes
Ubuntu 10 to 12 seconds to open a webpage,
but Windows takes only 1 or 2 seconds.

---

### Post by nerdtron on 2015-03-18
All websites? which browser? Specific on techinal details not just general observations.

post the output of:
```
route -n
ifconfig
cat /etc/resolv.conf
```

Are you using DHCP or Static IP addressing?

Try to traceroute the website that loads slow from ubuntu and let's see:
```
 tracepath website.com 
```

And for the 10-12 second loading time, what does the status bar of the browser says? If it says, "Looking up google.com" that means the DNS resolution is slow, if "Waiting for google.com" it could be a slow connection or something else.

---

### Post by gabmuks on 2015-03-18
Just found a site that helped. I disabled ipv6 as instructed.

Made a big difference! Ubuntu at least as fast or faster than Windows.

But I will try your code entry anyway. And thanks for all of you suggestions.

 [http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu]("http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/")[URL="http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/"]
[/URL]

---

