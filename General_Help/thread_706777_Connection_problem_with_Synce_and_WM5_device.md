---
title: "Connection problem with Synce and WM5 device"
date: 2008-02-24
forum: General Help
---

### Post by BoraTuncer on 2008-02-24
Hi Everybody,


I know there are lots of threads with this topic and I read most of them bu still could not succeded to sync my wm5 device (asus p535) with Evolution. (I'm using Ubuntu 7.10)

First I followed the link bellow to install Synce 0.11 but,
[http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)

If I invoke 'pls' command I always get the error bellow;

** (process:6703): WARNING **: No devices connected to odccm
pls: Could not find configuration at path '(Default)'


When I plug my device I can see from kernel messages

[  230.752000] usb 1-1: PocketPC PDA converter now attached to ttyUSB0
[ 3583.952000] usb 1-1: USB disconnect, address 2
[ 3583.960000] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[ 3590.564000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[ 3590.752000] usb 1-1: PocketPC PDA converter now attached to ttyUSB0


Then I run odccm on foreground (odccm -f) but I could not see any output when I plug my device.

After searching forums I learned that I need usb-rndis-lite (which is not mentioned in Synce web page). Then I downloaded , compiled the code and installed output with using commands bellow;

svn co [https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite](https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite)
cd usb-rndis-lite/
make
sudo ./clean.sh
sudo make install


But I still do not get any rndis releated message from kernel messages if I plug my device. "dmesg | grep rndis" command gives nothing !!!


By the way I added the following lines into my "/etc/firestarter/user-pre" file
$IPT -A INPUT -i rndis0 -j ACCEPT
$IPT -A OUTPUT -o rndis0 -j ACCEPT

and added following lines into "/etc/network/interfaces" file
auto rndis0 
iface rndis0 inet dhcp



I assume my problem with usb-rndis-lite because I could not get any releated info from "dmesg" if I plug my device. From that point I stucked and dont know what to do. Could anybody help me on this ?


Regards,
Bora

---

### Post by 6temes on 2008-02-26
Hi Bora,

I'm suffering the same proble as you, when I invoke **pls** this claims no devices connected to **odccm**. Even when I installed **usb-rndis-lite**.

> 6temes@6temes:~$ pls

** (process:9803): WARNING **: No devices connected to odccm
pls: Could not find configuration at path '(Default)'

It seems **dmesg** detects correctly the device:

> [15216.724000] usb 1-1: configuration #1 chosen from 1 choice
[15216.728000] ipaq 1-1:1.0: PocketPC PDA converter detected
[15216.732000] usb 1-1: PocketPC PDA converter now attached to ttyUSB0

but if I add the interface lines into "/etc/network/interfaces" the service fails when restarting. So, I think too the problem is the rndis driver that never creates the interface.

> 6temes@6temes:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                            rndis0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.rndis0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
rndis0: ERROR while getting interface flags: No such device
rndis0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up rndis0.

So, Anybody can help us?

Cheers,

6temes

---

### Post by BoraTuncer on 2008-03-03
Hi All,


Any help ?


BR,
Bora

---

### Post by ChinoxR on 2008-03-03
Hi alls
Initially I have the same problem.. but somehow I allowed to run the pls command,,,
I'm newbie on linux, I just worked on my WM5 device..

1- Try to disable the password protection of your device.
2- modify the type of USB connection, enabling advance network functionality. On "Start/Settings/Connections/USB to PC"
3- On "Start/Settings/Connections/Network Cards/Network Adapters" on the tab "My network card connects to" Selected "Work"
4- Do a soft reset of your device.

After this process I could run the pls command on Ubuntu 7.10
But right now, I'm stuck on synchronizing my device..  there is some command errors on the tutorial of OpenSync.

---

### Post by Asermar on 2008-03-11
Hi, Boys
the problem is the [15216.728000] ipaq 1-1:1.0: PocketPC PDA converter detected
This means you have this option enabled in your kernels, this options is for WM2003 and previous pda. The WM5 & WM6 devices uses the rndis protocol.

Disable this option in your kernel (usb devices / usb serial adapter)

A very good guide for compile the kernel ubuntu/debian style is [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

I've follow this guide and part of [http://ubuntuforums.org/showthread.php?t=345176](http://ubuntuforums.org/showthread.php?t=345176)

and now I can do the pls to my pda.

I hope this can help you.

---

### Post by DonQuichote on 2008-06-21
Finally I get my IPAQ to work, but the moment I connect it, my network dies. My /etc/resolv.conf gets overwritten with just comments.

The situation:
Fresh restart - I have network and can type this on the forum.
Connect my IPAQ - Notification area shows network has gone. Refresh any page in firefox also shows no network. Not even local network. /etc/resolv.conf is overwritten(!)

Pull cable to IPAQ. Network remains dead. Restarting the PC is the only way I know of to get it back. I saved some dmesg output before restarting:

```
[  267.915963] usb 3-2: new full speed USB device using uhci_hcd and address 3
[  268.091243] usb 3-2: configuration #1 chosen from 1 choice
[  268.338634] usbcore: registered new interface driver cdc_ether
[  270.077204] rndis0: register 'rndis_host' at usb-0000:00:1d.2-2, RNDIS device (SynCE patched), 00:02:b3:92:a8:c4
[  270.077243] usbcore: registered new interface driver rndis_host
[  286.388658] rndis0: no IPv6 routers present
[  711.353981] usb 3-2: USB disconnect, address 3
[  711.354827] rndis0: unregister 'rndis_host' usb-0000:00:1d.2-2, RNDIS device (SynCE patched)
[ 1050.534877] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1052.080421] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1052.080429] tg3: eth0: Flow control is on for TX and on for RX.
[ 1052.080975] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1062.283737] eth0: no IPv6 routers present
```

I followed so many howtos in trying my IPAQ to work that I do not know exactly what I did in detail anymore. Every solution led to new problems.

Can anyone see what is wrong or what relevant info did I leave out?

Edit:
I had forgotten to add
```
auto rndis0
iface rndis0 inet dhcp
```
to /etc/network/interfaces.

---

### Post by habitue01 on 2008-07-05
I had the same problem with my Tmobile Dash with WM6.  The issue was that I had a blank line in my /etc/network/interfaces file like this:

```
auto lo
iface lo inet loopback

auto rndis0
iface rndis0 inet dhcp
```


I changed it to this:
```

auto lo
iface lo inet loopback
auto rndis0
iface rndis0 inet dhcp
```

and it worked perfectly

---

