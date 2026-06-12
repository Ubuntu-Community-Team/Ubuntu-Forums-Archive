---
title: "[SOLVED] Installed Ubuntu Server by accident, now cannot boot to USB or CD"
date: 2015-03-15
forum: General Help
---

### Post by art_freak48 on 2015-03-15
I had clicked the Download menu on the main site and thought I clicked the link to the Desktop version, but instead it was the Server. So since I assumed I had clicked the right one I didn't bother to double-check the big letters saying "Ubuntu (version) *Server*" and went straight for the download button. I didn't do a dual boot because I wanted only one whole partition. Now I'm stuck with the Server and it won't let my try to boot either from my usb nor my CD with Mint 16, even after changing it through BIOS. I read somewhere that an upgrade or update of the grub usually helped most with booting problems but it didn't work for me. Any help would be greatly appreciated.

---

### Post by Bucky Ball on 2015-03-16
Weldome. When you have booted into the system, you will be at a command prompt. (If this doesn't happen, try [Boot Repair.]("https://help.ubuntu.com/community/Boot-Repair")) If you login and type:

```
sudo apt-get install ubuntu-desktop
```

... and reboot, you should get a regular login GUI and you should have a regular Ubuntu install, plus server apps. 

If it's not letting you change the boot device via grub, try hitting F12 instead of whatever key you hit to get to BIOS and choose the boot device there. That has worked for me when BIOS hasn't.

---

### Post by art_freak48 on 2015-03-16
Ok, tried that, and looked promising, until I got a bunch of "Failed to Fetch ___". And I mean a bunch. Got a few "Out of range comd" too.

---

### Post by Bucky Ball on 2015-03-16
Could you try these commands, one after another with return in between, in a terminal, please:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Report any and all errors. If you get none, try:

```
sudo apt-get install ubuntu-desktop
```

... again.

---

### Post by art_freak48 on 2015-03-17
Autoremove worked, but got a lot of errors for update:
Err [http://sercurity.ubuntu.com](http://sercurity.ubuntu.com) trusty-security InRelease
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg Could not resolve
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg "
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-update Relase.gpg "
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports.gpg "

Followed by:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease)
W:" [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)
W:" [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease)
W:" [http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease)
W:" [http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg) Could not resolve
W:" [http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg) "
W:" [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg) "
W:" [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg) "
W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Bashing-om on 2015-03-17
art_freak48; Hello ;

No internet connection ?
What returns:
```

ping -c3 ubuntu.com
ping -c3 8.8.8.8

```

Gotta start trouble shooting some where;
[INDENT][INDENT]looks like a good place to me
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-03-17
Please use [code] tags for terminal output. See the last link in my signature for how.

---

### Post by art_freak48 on 2015-03-18
```
Err [http://sercurity.ubuntu.com](http://sercurity.ubuntu.com) trusty-security InRelease
```
```
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease
```
```
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease
```
```
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg Could not resolve 'security.ubuntu.com'
```
```
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg Could not resolve 'us.archive.ubuntu.com'
```
```
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-update Relase.gpg Could not resolve 'us.archive.ubuntu.com'
```
```
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports.gpg Could not resolve 'us.archive.ubuntu.com'
```

```
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...usty/InRelease]("http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease")
```
```
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...ates/InRelease]("http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease")
```
```
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...orts/InRelease]("http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease")
```
```
W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...rity/InRelease]("http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease")
```
```
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...ty/Release.gpg]("http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg") Could not resolve 'us.archive.ubuntu.com'
```
```
W: Failed to fetch http://security.ubuntu.com/ubuntu/di...ty/Release.gpg Could not resolve 'security.ubuntu.com'
```
```
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg]("http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg") Could not resolve 'us.archive.ubuntu.com'
```
```
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...ts/Release.gpg]("http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg") Could not resolve 'us.archive.ubuntu.com'
```
```
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by art_freak48 on 2015-03-18
First  code:
```
ping: unknown host ubuntu.com
```

Second code:
```
connect: Network is unreachable
```

---

### Post by Bashing-om on 2015-03-18
art_freak48l Hey;

That confirms you have no networking capability.
Is this a wired (cable) or Wireless (WIFI) connection ?

For starters:
. network card detected ?
```

sudo lshw -C network
lspci | grep Ethernet

```
2. IP address assigned ?
```

ifconfig eth0 (or whichever the network is,eth1)

```
 -no address returned ?
```

sudo ip link show eth0
ip route list

```
3. Check /etc/network/interfaces
```

cat /etc/network/interfaces

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And let's see where we go from here.

[INDENT][INDENT]it too is a process
[/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-03-19
When I downloaded the server, I did so via WiFi, because I didn't have a cable. I know somebody who might have one laying around, so I'll get a hold of them.

---

### Post by art_freak48 on 2015-03-21
Found a cable if I need to use it. I decided to use the codes you provided without it first.

```
sudo lshw -C network
*-network DISABLED
    description: Wireless interface
    product: QCA9565/AR9565 Wireless Network Adapter
    vendor: Qualcomm Atheros
    physical id: 0
    bus info: pci@0000:01:00.0
    logical name: wlan0
    version: 01
    serial: a4:db:30:76:6c:b0
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list rom ehternet physical wireless
    configuration: broadcast=yes driver=ath9k driverversion=3.16.0-30-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
    resources: irq:32 memory:f0a00000-f0a7ffff memory:f0a80000-f0a8ffff
*-network DISABLED
    description: Ethernet interface
    product: NetLink BCM57780 Gigabit Ethernet PCIe
    vendor: Broadcom Corporation
    physical id: 0
    bus info: pci@0000:03:00.0
    logical name: eth0
    version: 01
    serial: 54:be:f7:6f:13:8d
    capacity: 1Gbit/s
    width: 64 bits
    clock: 33MHz
    capabilities: pm mis pciexpress bus_master cap_list ethernet physical tp mii 10bt-fd 100-fd 1000-fd autonegotiation
    configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=sb latency=0 link=no multicast=yes port=MII
    resources: irq:40 memory:f0800000-f080ffff
```

```
ifconfig eth0
eth0    Link encap:Ethernet HWaddr 54:be:f7:6f:13:8d
    BROADCAST MULTICAST MTU:1500 Metric:1
    RX packets:0 errors:0 dropped:0 overruns:0 frame:0
    TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000
    RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
    Interrupt:40
```

```
sudo ip link show eth0
2: eth0: <BROADCAST, MULTICAST> mtu 1500qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 54:be:f7:6f:13:8d brd ff:ff:ff:ff:ff
```

Was unsure what to do after i put in
```
ip route list
```

---

### Post by Bashing-om on 2015-03-21
art_freak48; Welp;

Shows no networking .
Does the system find any networking hardware ?
We look with the terminal commands:
```

lspci | grep Ethernet
ls -al /sys/class/net

```

Upfront, wireless is not my forte. But We can work to get the cable connection up, and once this wired connection is up, install the drivers for the wireless connection.

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-03-22
Here's what I got:

```

lspci | grep Ethernet
03.00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
```

```
ls -al /sys/class/net
total 0
drwxr-xr-x 2 root root 0 Mar 21 19:52 .
drwxr-xr-x 56 root root 0 Mar 21 19:49 . .
lrwxrwxrwx 1 root root 0 Mar 21 19:49 eth0 -> ../../devices/pci0000:00/0000:02.5/0000:03:00.0/net/eth0
lrwxrwxrwx 1 root root 0 Mar 21 19:49 lo -> ../../devices/virtual/net/lo
lwrxwrxwrx 1 root root 0 Mar 21 19:52 wlan0 -> ../../devices/pci0000:00/0000:00:02.3/0000:01:00.0/net/wlan0
```

If WiFi ends up not working, but the cable does, I'd be fine with that. I don't take my laptop out and about (it's a behemoth).

---

### Post by Bashing-om on 2015-03-23
art_freak48; Well ......

The good news is, that is all good news.
The wired connection 'eth0' is recognized as well as the hardware and the PCI interface.
Same same for the wireless connection . It is all there also.

The bad news is that we still do not know the why of a failure to communicate.
Are you on a router ?
What returns:
```

ip route list
lspci -nnk | grep -iA2 net

```

Are we good in-house, such that the problem is outside of the operating system ? What returns:
```

ping -c3 127.0.0.1

```

Depending on what returns, is where we look to next.

[INDENT][INDENT]stepping through a process
[/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-03-24
I have a wireless g router from Linksys.

```
01.00.0 Network controller [0280]: Qualcomm Atheros QCA9565/AR9565 Wireless Network Adapter [168c:0036] (rev 01)
Subsystem: Lite-on Communications Inc Device [11ad:0632]
Kernal driver in use: ath9k


--
03:00.0 Ethernet controller [0200]: Broadcomm Corporation NetLink BCM57780 Gigabit Ethernet PCIe [4e4:1692] (rev 01)
Subysystem: Acer Incorporated [ALI] Device [1025:0782]
Kernel driver in use: tg3
```

```
PING 127.0.0.1 (127.0.0.1) 56 (84) bytes of data
64 bytes from  127.0.0.1: icmp_seq=1 ttl=64 time=0.065 ms

64 bytes from  127.0.0.1: icmp_seq=2 ttl=64 time= 0.051 ms

64 bytes from  127.0.0.1: icmp_seq=3 ttl=64 time= 0.083 ms


---127.0.0.1 ping statistics---
3 packets transmitted, 3 recieved, 0% packet loss, time 2003 ms
rtt min/avg/max/mdev= 0.051/0.66/0.083/0.014 ms
```

I don't know if I'm doing something wrong or not, but the ip route list code never shows anything. No words, letters, numbers, nothing saying that it doesn't reconize the code, no error. Nothing. I hit enter and it awaits the next code. Is that what it's supposed to do?

---

### Post by Bashing-om on 2015-03-24
art_freak48; Shucks;

Not sure what to make of the situation:
My output; what you should have similar on the wired connection:
```

sysop@1404mini:~$ ip route list
default via 192.168.0.1 dev eth1 
192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.102 
sysop@1404mini:~$

```

We know the card is good, as the loopback (127.0.0.1) is good.

Got a thought; has this router ever worked with this box ? Or is this all a new set up ? When I set this system up with a new router at that time, In the router set up I had to "clone" for the MAC for my ISP to accept the connection.

What returns:
```

ifconfig eth0 up

```

[INDENT][INDENT]gotta find a way to talk to the router
[/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-03-25
I fiddled with the cable a bit to make sure it was working. Moved it to another port on router, and for some reason that worked. ip route list finally showed up.

```
default via 192.168.1.1 dev eth0
192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.105
```

---

### Post by Bashing-om on 2015-03-25
art_freak48; Well;

Wonder of Wonders !

We got networking now ?
```

ping -c3 192.168.1.1
ping -c3 8.8.8.8
ping -c3 ubuntu.com

```

Maybe YES
[INDENT][INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-03-25
Decided on a whim to try and install desktop again. It actually did something! It acted like it was installing, but then I did get a few errors towards the end:
```

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_101.1.3-0ubuntu0.3_amd64.deb 404 Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgbm1_10.1.3-0ubuntu0.3_amd64.deb 404 Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libegl1-mesa_10.1.3-0ubuntu0.3_amd64.deb 404 Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libglapi-mesa_10.1.3-0ubuntu0.3_amd64.deb 404 Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libopenvg1-mesa_10.1.3_0ubuntu0.3_amd64.deb 404 Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libwayland-egl1-mesa_10.1.3_0ubuntu0.3_amd64.deb 404 Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libegl1-mesa-drivers_10.1.3_0ubuntu0.3_amd64.deb 404 Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-glx_10.1.3_0ubuntu0.3_amd64.deb 404 Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups-filters/libcupsfilters1_1.0.52-0ubuntu1.2_amd64.deb 404 Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups-filters/libfontembed1_1.0.52-0ubuntu1.2_amd64.deb404 Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgles2-mesa_10.1.3-0ubuntu0.3_amd64.deb 404 Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libxatracker2_10.1.3-0ubuntu0.3_amd64.deb 404 Not Found [IP: 91.189.91.24 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libx/libxfont/libxfont1_1.4.7-1ubuntu0.1_amd64.deb 404 Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/lightdm/lightdm_1.10.4-0ubuntu2_amd64.deb 404 Not Found [IP: 91.189.91.23 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups-filters/cups-filters-core-drivers_1.0.52-0ubuntu1.2_amd64.deb 404 Not Found [IP: 91.189.91.24 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups-filters/cups-filters_1.0.52-0ubuntu1.2_amd64.deb 404 Not Found [IP: 91.189.91.24 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/r/requests/python3-requests_2.2.1-1ubuntu0_all.deb 404 Not Found [IP: 91.189.88.149 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups-filters/cups-browsed_1.0.52-oubuntu1.2_amd64.deb 404 Not Found [IP: 91.189.91.24 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevdocument3-4_3.10.3-0ubuntu10.1_amd64.deb 404 Not Found [IP: 91.189.91.24 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevview3.3.10.3-0ubuntu10.1_amd64.deb 404 Not Found [IP: 91.189.91.24 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince-common_3.10.3-0ubuntu10.1_all.deb 404 Not Found [IP: 91.189.91.24 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_3.10.3-ubuntu10.1_amd64.deb 404 Not Found [IP: 91.189.91.24 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_36.0.1+build2-0ubuntu0.14.04.1_amd64.deb 404 Not Found [91.819.92.200 80]
E: Failed to fetch http://us.archive.ubuntu.com/pool/main/l/ligthdm/liblightdm/-gobject-1-0_1.10.4-0ubuntu2_amd64.deb 404 Not Found [IP: 91.189.91.24 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.13.0-46.79_amd64.deb 404 Not Found [IP: 91.189.92.201 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/r/requests/python-requests_2.2.1-1ubuntu0.1_all.deb 404 Not Found [91.189.91.13 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by Bashing-om on 2015-03-25
art_freak48;

Still no certainty of networking .
Now what returns:
```

ping -c3 192.168.1.1
ping -c3 8.8.8.8
ping -c3 ubuntu.com

```
Where we check :
you are getting out of the machine
you are able to access the internet
Domain Name Server is working

Then we look at the package management system.

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-03-25
Just saw your recent post. Here are the pings:

```
Usage: ping [aAbBdDfhLnOqrRUvV] [-c count] [-i interval] [-I interface]
[-m mark] [-M pmtudisc-option] [-l preload] [-p pattern] [-Q tos]
[-s packetsize] [-S sndbuf] [-t ttl] [-T timestamp_option]
[-w deadline] [-W timeout] [hop1 ...] destination
```

```
PING 8.8.8.8 (8.8.8.8) 56 (84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=57 time=46.1 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=57 time=45.1 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=57 time=45.1 ms

---8.8.8.8 ping statistics---
3 packets transmitted, 3 recieved, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 45.117/45.484/46.175/0.488 ms

```

```
PING ubuntu.com (91.189.94.40) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=54 time=155 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=54 time=154 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=54 time=155 ms

---ubuntu.com ping statistics---
3 packets transmitted, 3 recieved, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 154.786/155.474/155.892/0.490 ms
```

---

### Post by Bashing-om on 2015-03-25
art_freak48; Yeyah !

We do have networking !

OK, package management system:
post back:
```

sudo apt-get update
sudo apt-get upgrade
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
See if we can spot the failure.

[INDENT][INDENT]meanwhile;
[INDENT][INDENT][INDENT]back at the ranch
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-03-27
Update came back with errors:
```

Err http://us.archive.ubuntu.com trusty InRelease
Err http://security.ubuntu.com trusty-security InRelease
Err http://us.archive.ubuntu.com trusty-updates InRelease
Err http://us.archive.ubuntu.com trusty-backports In Release
Err http://security.ubuntu.com trusty-security Release.gpg
could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com trusty Release.gpg
Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com trusty-updates Release.gpg
Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com trusty-backports Release.gpg
Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease
W: Failed to fetch http://security.ubuntu.com/ubuntu.com/ubuntu/dists/trusty-security/InRelease
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg Could not resolve 'security.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg Could not resolve 'us.archive.ubuntu.com'
W: Some indesx files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by Bucky Ball on 2015-03-28
You're either not online, the us.archive is down by the looks, which would be odd, or there might be some syntax mishap in your software sources. Have you tried another mirror? Try changing the mirror in 'Software & Updates' (could be called Software Sources in Ubuntu, not sure).

---

### Post by art_freak48 on 2015-03-28
Not familiar with mirrors, so I did a quick search and even tried one using Nano text editor:

```
http://mirror.us.leaseweb.net/ubuntu
```

Still got the same errors.

---

### Post by Bashing-om on 2015-03-28
art_freak48; Humm ...

As around and round we go.

What is your world location ? The mirror I use:
[http://ftp.utexas.edu/ubuntu](http://ftp.utexas.edu/ubuntu)
You can change your mirror site in software sources - >
On the Ubuntu Software tab, select the drop down for "Download From"
Select Other
Choose your country then click on Choose best server....This will ping all the mirror sites for the best ping and then it will select the better server.
I do this all the time when version upgrade time comes....it makes an unbelievable difference.
Once you do this, In Synaptic Package manager ( if you have this utility installed), click reload to get the updated info from your new mirror.

Hwy
[INDENT][INDENT][INDENT]worth a shot
[/INDENT][/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-03-30
On a hunch I went back and tried the ip route list code again. Sure enough, it's unresponsive now, and I had not moved the cable since thinking I found a port that worked. I'm going to try and find another cable and see if that makes a difference. Moved the cable around again to different ports, and nothing.

It just seems to me that once I found a port that supposedly worked, all the new codes you gave me should have worked. I have a blue ray player in one port on the router and it works fine, so hopefully (oh please hopefully) it's a hardware malfunction with the cable.

I will get back with my findings as soon as I can (withing the next 2 or 3 days), and hopefully we can go from there.

---

### Post by Bashing-om on 2015-03-30
art_freak48; HoKAy ;

I sorta had that suspicion, glad to see your trouble shooting skills are improving.
Check your pins on the cable ends and on the card it's self. A while back a bent pin was the cause to drive me nuts for a couple of days ! 
My 1st step is always, "can I ping the router ?" .
When you have that cable spared off ( or verified on a different machine) .. we continue this little odyssey.

[INDENT][INDENT]quitters never win ( or learn better )
[/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-04-02
Looked at cable. Nothing looked bent or crooked at either end. Checked port on computer, nothing obstructing connection, nothing looked crooked in there either. Looked clean, almost new even . Confiscated my mom's laptop and plugged the cable to it, and it worked fine. Likely there's an issue with the port on my laptop. Resisting urge to place sad emoticon.

---

### Post by Bashing-om on 2015-04-02
art_freak48; Humm ....

Power cycle the router, see if there is a positive result .
Watch the LEDs on the network card .
Generally - depending on what the manufacturer set - a return to "green" should be good.
orange is UNgood.

Check you are good in house:
```

ping -c3 127.0.0.1

```
then see if you can ping your router -> get the adrress :
```

route -n

```
under the 'gateway' heading is the IP ( say 192.168.0.1);
Ping the router to see if ya getting out of the machine:
```

ping -c3 192.168.0.1

```

[INDENT][INDENT]depending on what results, is the direction
[INDENT][INDENT][INDENT]we take to next
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-04-05
Well, after power cycling, I get an orange flashing light next to port on laptop.

```
PING 127.0.0.1 (127.0.0.1) 56 (84) bytes of data.
64 bytes from 127.0.01 icmp_seq=1 ttl=64 time-0.070 ms
64 bytes from 127.0.01 icmp_seq=2 ttl=64 time-0.077 ms
64 bytes from 127.0.0 icmp_seq=3 ttl=64 time-0.089 ms

---127.0.0.1 ping statistics---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rt min/avg/max/mdev = 0.070/0.077/0.089/0.012 ms
```

```
Kernal IP routing table
Desination    Gateway    Genmask    flags Metric Ref    Use Iface
```

Nothing comes up to ping under Gateway. Tried pinging anyway and get "Network is unreachable."

This thing's more stubborn than a mule.

---

### Post by Bashing-om on 2015-04-05
art_freak48; Yuk;

Still with a failure to communicate. Looks like you can not talk to the router.
What returns:
```

ip route
ifconfig
sudo dhclient eth0

```
See if we can find the address of the router, and be able to talk to it.

[INDENT][INDENT]search'n every which way
[/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-04-06
Nothing returns for ip route

```

lo     Link ecap:Local Loopback
       inet addr:127.0.0.1 Mask:255.0.0.0
       inet6 addr:  ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:65536 Metric:1
       RX packets:32 errors:0 dropped:0 overruns:0 frames:0
       TX packets:32 errors:0 dropped:0 overruns:0 frames:0
       collisions:0 txqueuelen:0
       RX bytes:2480 (2.4 KB)    TX bytes:2480 (2.4 KB)
```

First time I put in sudo dhclient eth0 nothing came up. Typed it in a second time and it did come up with:
```
RTNETLINK answers: File exists
```

Not sure why the first time didn't take.

---

### Post by Bashing-om on 2015-04-06
art_freak48; 

A thought: networking; laptop -> wireless available ... humm ..

one can only have 1 network active at a given time .. make sure that wireless is disabled/turned off.
Now can you enable the wired (eth0 ??) connection in Network Manager ?

[INDENT][INDENT]sometime I do wonder
[INDENT][INDENT][INDENT][INDENT]sometimes else I wander
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-04-10
Tried a few things. Laptop doesn't have a switch so I had to try a few commands:

sudo ifconfig wlan0 up/down doesn't work. 

iwconfig wlan0 essid name key password (changing 'name' to the name of actual network, no key password to put in):
```
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on decie wlan0 ; Operation not permitted.
```

sudo service network-manager restart:
```
network-manager: unrecognized service
```

Can't use rfkill commands. It's not installed, and well, can't install it for obvious reasons, lol.

I don't know if this means anything, but i noticed sometimes after I've logged in shortly after start up I see something that says 'There are _ zombie processes' Sometimes it's 1 or 4 or 5 or it never comes up at all. I don't know if it's involved with my issue or not.

---

### Post by Bashing-om on 2015-04-10
art_freak48; Strange;

As we know wired networking did work once (post #18).
Let's lay our ears back and try and determine why wired networking in not available now.
We have:
product: NetLink BCM57780 Gigabit Ethernet PCIe
driver=tg3 driverversion=3.137

Let's see what the system sees; what returns:
```

lsmod
rfkill list all

```
confirm that 'tg3' is still seen in that output and that WIFI is disabled .

Now let's bring up the wired connection:
```

sudo modprobe tg3
ifconfig eth0 up
ip route

```
[INDENT][INDENT]worth a shot, see what errors we get
[INDENT][INDENT][INDENT]take it from there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-04-12
lsmod:
```

Moduel                                        Size             Used by
nls_iso8859_1                            12713             1
acer_wmi                                  32522             0
sparse_keymap                          13948             1 acer_wmi
amd_freq_sensitivity                   12615             0
radeon                                 14112941             1   
kvm                                        452043             0
crct10dif_pclmul                         14307             0
crc32_pclmul                             13133              0
ghash_clmulni_intel                     13230              0
aesni_intel                               152552              1
aes_x86_64                               17131              1 aesni_intel
lrw                                           13286              1 aesni_intel
gf128mul                                   14951              1 lrw
glue_helper                                13990              1 aesni_intel
ablk_helper                                13957              1 aesni_intel
cryptd                                      20359               3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                                      17393               0
serio_raw                                  13483               0
edac_core                                 56549               0
k10temp                                    13144               0
fam15h_power                            13142               0
edac_mce_amd                           22578               0
ath3k                                        13331               0
arc4                                          12608               2
rtsx_pci_ms                                18168               0
i2c_piix4                                    22166                0
btusb                                        32497                0
memstick                                   16966                1 rtsx_pci_ms
uvcvideo                                   81073                 0
bluetooth                                 446409                 3 ath3k,btusb
videobuf2_vmalloc                       13216                 1 uvcvideo
videobuf2_memops                      13362                 1 videobuf2_vmalloc
videobuf2_core                           59104                 1 uvcvideo
ath9k                                      137283                 0
v412_common                             15681                1 videwobuf2_core
6lowpan_iphc                              18702                1 bluetooth
ath9k_common                            25638                1 ath9k
videodev                                   153793                3 uvcvideo,v412_common,videobuf2_core
ath9k_hw                                  446521                2 ath9k_common,ath9k
snd_hda_codec_realtek                 77467                1   
media                                         21903                2 uvcvideo,videodev
snd_hda_codec_generic                 68937                1 snd_hda_codec_realtek
ath                                            29006                 3 ath9k_common,ath9k,ath9k_hw
snd_hda_codec_hdmi                    47548                 1
mac80211                                 652718                 1 ath9k
snd_hda_intel                              30469                 0
snd_hda_controller                       31056                 1 snd_hda_intel
snd_hda_codec                          139682                 5 [SIZE=1]snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_intel,snd_hda_controller [/SIZE]
cfg80211                                   494362                 4 ath,ath9k_common,ath9k,mac80211
snd_hwdep                                  17698                 1 snd_hda_codec
ttm                                            93588                 1 radeon
snd_pcm                                    104112                 4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
drm_kms_helper                            61574                 1 radeon
snd_timer                                    29562                 1 sbd_pcm
drm                                          311018                  4 ttm,drm_kms_helper,radeon
snd                                            79468                  8 [SIZE=1]snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel[/SIZE]
shpchp                                        37047                 0
soundcore                                    15047                 2 snd,snd_hda_codec
i2c_algo_bit                                  13413                 1 radeon
wmi                                             19193                 1 acer_wmi
video                                           20128                 1 acer_wmi
mac_hid                                       13227                 0
lp                                                17759                 0
parport                                         42348                1 lp
broadcom                                      13184                0
rtsx_pci_sdmmc                              23043                0
[COLOR=#ff0000]tg3                                             166618                0[/COLOR]
psmouse                                      106561                0
ahci                                              34062                3
ptp                                               19395                1 tg3
sdhci_pci                                       23301                0
sdhci                                             43685                1 sdhci_pci
libahci                                            32424               1 ahci
rtsx_pci                                          46259               2 rtsx_pci_ms,rtsx_pci_sdmmc
pps_core                                        19382               1 ptp
```

Sorry, first code box is a mess.

Looks like tg3 is a no.

rfkill was not installed and oddly the first time I tried to install it it didn't work. Tried it again and it was successful. Huh?
rfkill list all:
```

0: acer-wireless: Wireless LAN
            Soft blocked: no
            Hard blocked: no
1: acer-bluetooth: Bluetooth
            Soft blocked: no
            Hard blocked: no
2: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no
3: hci0: Bluetooth
            Soft blocked: no
            Hard blocked: no
```
Cannot use rfkill block <# of block>. I get ```
Can't open RFKILL control device: Permission denied
```

ifconfig comes up with: ```
SIOSIFFLAGS: Operation not permitted
```

---

### Post by Bashing-om on 2015-04-12
art_freak48l yeah, for sure ->

HUH ?
> 
rfkill was not installed and oddly the first time I tried to install it it didn't work. Tried it again and it was successful. Huh?

an intermittent wired connection ????????? I would feel better about this if we know that WIFI was not a factor ( that it is disabled).

Let's see if the logs can tell us what is going on with this intermittent wired connection:
```

grep Network /var/log/dmesg
grep tg3 /var/log/dmesg
grep eth0 /var/log/dmesg

```

[INDENT][INDENT]when all else fails
[INDENT][INDENT][INDENT]read the instructions[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-04-17
I am VERY sorry it took me so long to reply. I've been preoccupied.

I know, right? This is the second time it's acted like it was connected. I read about rfkill through search before it was suggested here and tried it. My comp said it wasn't installed. That was when I tried the first time to install it and it got errors, and I thought "Duh, why'd I bother I need a connection to begin with." I didn't bother writing the errors cuz I thought it was a silly attempt. So when you suggested it I figured I'd try again in some vain hope it would work this time. This thing is such a tease.

Here's what I get with the codes you gave me:
```

[    11.798205] audit: type=1400 audit(1429318921.262:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=402 comm="apparmor_parser"
[    11.798241] audit: type=1400 audit(1429318921.262:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=408 comm="apparmor_parser"
[    11.798273] audit: type=1400 audit(1429318921.262:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=449 comm="apparmor_parser"
[    11.798888] audit: type=1400 audit(1429318921.262:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="usr/lib/NetworkManager/nm-dhcp-client.action" pid=402 comm=:apparmor_parser"
[    18.523756] audit: type=1400 audit(1429318921.986:21): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="usr/lib/NetworkManager/nm-dhcp-client.action" pid=875 comm="apparmor_parser"
[    18.524440] audit: type=1400 audit(1429318921.986:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="usr/lib/NetworkManager/nm-dhcp-client.action" pid=875 comm="apparmor_parser"

```

```

[    2.145842] tg3.c:v3.137 (May 11, 2014)
[    2.182553] libphy: tg3 mdio bus: probed
[    2.259158] tg3 0000.03.00.0 eth0: Tigon3 [partno(BCM57780) rev 57780001] (PCI Express) MAC address 54:be:f7:6f:13:8d
[    2.261555] tg3 0000.03.00.0 eth0: attached PHY driver [Broadcom BCM57780] (mii_bus:phy_addr=300.01)
[    2.263919] tg3 0000.03.00.0 eth0: RXcsums[1] LinkChgREG[0]  MIirq[0] TSOcap[1]
[    2.266249] tg3 0000.03.00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]

```

```

[    2.259158] tg3 0000:0300.0 eth0: Tigon [partno(bcm57780) rev 57780001] (PCI Express) MAC address 54:be:f7:6f:13:8d
[    2.261555] tg3 0000:0300.0 eth0: attached PHY driver [Broadcom BCM57780] (mii_bus:phy_addr=300.01)
[    2.263919] tg3 0000:0300.0 eth0: RXcsums[1] LinkChgREG[0]  MIirq[0] TSOcap[1]
[    2.266249] tg3 0000:0300.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]

```

---

### Post by Bashing-om on 2015-04-20
art_freak48; Sheesshh ...

Sorry to say, I do not know why the network link is not activated.
I do not run my system with ' NetworkManager ' so I am unable to make any comparisons or tests.

All I can think of to try is to edit the connection in NetworkManager's utility and make up a new connection and see what results.
Not great, but I know of nothing else to try at this point.

[INDENT][INDENT]a lack of knowledge on my part
[/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-04-20
Well then, I suppose this is as far as we go. I will begin looking up just how to go about editing, as I'm unfamiliar on the subject. Anything I can't find I'll be back on these forums.

A tip of the hat to you sir, for going this far! I had NO idea what to do. I'm at least keeping my head above water now, and I'm even beginning to swim (albeit I'm on the shallow end of the pool...with trainers haha).

Thanks again for getting me this far, and for your patience.

Have an awesome day! :)

---

### Post by Bashing-om on 2015-04-20
art_freak48; Hey !

If I come up with another thought, I will be here !
I just do not comprehend why:
```

sysop@1404mini:~$ grep eth1 /var/log/dmesg
[    9.538111] 8139too 0000:01:09.0 eth1: link up, 100Mbps, full-duplex, lpa 0xC5E1

```
does not happen in your case.

[INDENT][INDENT]I'm just stuck is all
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-04-21
art_freak48; Hey !

Not forgotten, and still on my mind.
IF you can live without wireless on this box; and do not mind doing a bit of editing to system files.
I do have a thought in mind to proceed.
How about we tell the system not to use ' Network Manager ", that you will manage the network.

Like I have advised, I do not have experience with wireless ( my router handles all my wireless needs ); nor do I know how Network Manager works;No one else is jumping in here on this thread to our rescue;  but, if you want you and I can play with a "manually managed" network setup.

What is presently set up ?
```

cat /etc/NetworkManager/NetworkManager.conf

```
Here we can direct the system to go 'manual'.

Then we edit the file:
```

cat /etc/network/interfaces

```
and make an edit to it so that you control the interface.

Now let;s see if we can bring eth0 on-line !

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-04-21
Oh sure thing! I'm willing to give that a try. I'll post my findings as soon as I can. Thanks for sticking around.

---

### Post by art_freak48 on 2015-04-22
Hmmm, here's what I get with the first code:
```
cat: /etc/NetworkManager/NetworkManager.conf: No such file or directory
```

Second code seems alright:
```
# This file describes the network interfaces available on your system
# and how to activate them. for more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

---

### Post by Bashing-om on 2015-04-22
art_freak48; Hummm .. is right !

Double check that " /etc/NetworkManager/NetworkManager.conf " does not exist. It should on a standard ubuntu install .

IF not we still proceed. Else we still have to edit that file such that you manage networking .

Edit " /etc/network/interfaces "
Make a backup 1st .. just for what ever ..and make it like so:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
Rather then re-starting networking, reboot the system; just because I like to clear memory.

After the reboot, does networking now work ?
terminal commands:
```

ping -c3 8.8.8.8
ping -c3 ubuntu.com

```

[INDENT][INDENT][INDENT]I want to hear
[INDENT][INDENT][INDENT]YES
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-04-24
```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8 icmp _seq=1 ttl=57 time=25.4 ms
64 bytes from 8.8.8.8 icmp_seq=2 ttl=57 time=25.7 ms
64 bytes from 8.8.8.8 icmp_seq=3 ttl=57 time=25.5 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 25.435/25.572/25.753/0.186 ms
```

```
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=54 time=167 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=54 time=166 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=54 time=166 ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002 ms
rtt min/avg/max/mdev = 166.599/166.801/167.156/0.256 ms
```

---

### Post by Bashing-om on 2015-04-24
art_freak48; Hey, Outstanding !

We are back in business where we were 'bout 2 weeks past.

OK, NOW .. let's get a system package management status:
```

sudo apt-get update
sudo apt-get upgrade

```

See where we go from here.

[INDENT][INDENT]who said it could not be done 
[/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-04-27
Update success.
Upgrade success.
No errors!

---

### Post by Bashing-om on 2015-04-27
art_freak48;Outstanding !

So now that you have a functioning s t a b l e system (server).
What now do you want to get done .

[INDENT][INDENT][INDENT]we aim to please
[/INDENT][/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-04-27
My initial goal was to get the Ubuntu desktop, not the server. I thought about going ahead and installing, but I didn't want to get too excited or ahead of myself in case I jinx it. Happy and nervous now, it seems so close.

---

### Post by Bashing-om on 2015-04-27
art_freak48; Welp ..

At this point, you have multiple choices/options for the (D)esktop (E)nvironment you want ... it does not have to be unity/ubuntu. A bit of thought now might be a real good thing.
I am prejudiced in that I really like xfce . But, there are literally scores available.

They are all just
[INDENT][INDENT]a terminal command away
[/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-04-28
Believe it or not, I did manage to get Mint 16 (Cinnamon Petra) via CD on an old Dell Optiplex about a year ago. I then decided to try Ubuntu on another desktop I have (from what I gather Mint and Ubuntu are pretty much the same, but I wanted to try the different environments of desktop), which was also successfully done via thumbdrive. 

My problem arose when I wanted to add Ubuntu to my laptop, but no matter what I tried, the Windows 8 on it wouldn't allow me, so I went to the site to make a CD. I was distracted that day and erroneously clicked for the server instead of the desktop. Even though I'm a greenhorn at this stuff, it's still kinda embarrassing that I goofed up THAT bad. I've not had the chance yet to really dip my toes in the terminal, well, until now lol. I had mulled over Xubuntu at one time, but I figured my laptop had plenty of juice for Ubuntu.

---

### Post by Bashing-om on 2015-04-29
art_freak48; Hey, hey ....


If you are happy happy with ubuntu and unity as the DE;
This should be all there is to it:
```

sudo apt-get install ubuntu-desktop

```

Where the primary use of your machine is as a "desktop" and NOT as a server > As a server one gets into security issues and conflicts running a desk top on it .

reboot, and now where do we stand ? As I am not 100% sure if a (D)isplay (M)anager for login purposes is also automagically installed.


[INDENT][INDENT]look'n better allah the time
[/INDENT][/INDENT]

---

### Post by art_freak48 on 2015-04-29
It's been a long time coming, but I finally have the desktop! Virtual confetti everywhere! Everything seems to be in working order, and if I choose so later, I can tinker with getting WiFi, but for now, it's good as gold.

Many many many thanks for sticking this through, your patience was much appreciated. I can now enjoy using Ubuntu for general purposes, as well as tinkering.

A hearty handshake to you sir, many thanks again!

---

### Post by Bashing-om on 2015-04-29
art_freak48; Hey !

Makes my day too ! Up and running 'buntu ; Way to go .

weren't nothing to it, just took some time to get there.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]tweak'n alla the way home
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

