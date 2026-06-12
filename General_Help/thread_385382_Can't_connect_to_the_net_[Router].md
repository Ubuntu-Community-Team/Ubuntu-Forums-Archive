---
title: "Can't connect to the net [Router]"
date: 2007-03-15
forum: General Help
---

### Post by Moe70 on 2007-03-15
I installed Ubuntu yesterday and im a Linux newbie. I thought it would just pick it up ssince its Ethernet... but it doesn't work what do i need to do

I got a dlink router btw

---

### Post by peabody on 2007-03-15
Under the Administration menu there should be a control panel to configure your network interfaces.  Take a look at it and see if you need to set your network card to dhcp.

---

### Post by jenhsun on 2007-03-15
STEP1: Check your hardware. 

Please go to Device Manager in System/Administration/Device Manager
and find out the network card, what is your network.interface is
in general it is eth0

STEP2:
Go to the terminal, then type
nano /etc/network/interfaces to bring out the page and edit

auto lo
iface lo inet loopback

auto eth0                   <------if you have static IP
iface eth0 inet static
address 192.168.0.??
netmask 255.255.255.0
gateway 192.168.0.?

auto eth0
iface eth0 inet dhcp  <------ if you want your router assign you IP

STEP3: restart network
/etc/init.d/networking restart

By the way, make sure your router setup just fine.

---

### Post by Moe70 on 2007-03-15
Everything seems to be working. i pinged 192.168.1.1. worked...

went to device manager on the side it says ethernet card....but on status it says 'status' and under device type it says unknown


could it be that the network card needs a driver or something. or is that irrelevant on linux

---

### Post by peabody on 2007-03-15
If you can actually ping 192.168.1.1 then there should be no reason that you can't see it from a web browser.

Could you type "ifconfig" into a terminal and copy and paste the output of the command here?

---

### Post by Moe70 on 2007-03-15
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:D0:CB:F0
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fed0:cbf0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1598 (1.5 KiB)  TX bytes:1818 (1.7 KiB)
          Interrupt:193 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)


[[IMG]http://img407.imageshack.us/img407/7725/screenshotsko8.th.jpg[/IMG]](http://img407.imageshack.us/my.php?image=screenshotsko8.jpg)

---

### Post by TheWizzard on 2007-03-15
maybe the domain name servers are not set.

---

### Post by Moe70 on 2007-03-15
no i dont think it is.

what is it? what should i set it to

---

### Post by peabody on 2007-03-15
So, if you type "192.168.1.1" into a browser, you can't see the control panel of the router correct?

---

### Post by Moe70 on 2007-03-15
yes i can

---

### Post by arthur_kalm on 2007-03-15
But you can't get onto the Internet? Can you get onto the Internet from another Operating System on the same computer? It seems strange that you can't since you were given an IP address and therefore should be on the network (and able to access the Internet).

---

### Post by peabody on 2007-03-16
> **Moe70 said:**
> yes i can

what's the output of the "route" command on a terminal say?  Copy paste output here.

---

### Post by Moe70 on 2007-03-16
> **arthur_kalm said:**
> But you can't get onto the Internet? Can you get onto the Internet from another Operating System on the same computer? It seems strange that you can't since you were given an IP address and therefore should be on the network (and able to access the Internet).
Yes i can access the internet from xp. i thought it might be just firefox on lunix that wasnt working but even the email manager and gaim...dont work

> **peabody said:**
> what's the output of the "route" command on a terminal say?  Copy paste output here.


```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         mygateway.ar7   0.0.0.0         UG    0      0        0 eth0

```

---

### Post by Moe70 on 2007-03-16
bump

---

### Post by peabody on 2007-03-16
What does mygateway.ar7 resolve to?  What happens when you try to ping it?

---

### Post by mrmonday on 2007-03-16
In firefox type about:config. In the filter box type ipv6. Double click the only value there. Can you get on to the internet now? If so I will post what to do next.

---

### Post by Moe70 on 2007-03-16
double post

---

### Post by Moe70 on 2007-03-16
> **mrmonday said:**
> In firefox type about:config. In the filter box type ipv6. Double click the only value there. Can you get on to the internet now? If so I will post what to do next.

that worked :). everything else stil not working

---

### Post by mrmonday on 2007-03-16
Try this link:

[http://ubuntuforums.org/showthread.php?t=358749#post2226758](http://ubuntuforums.org/showthread.php?t=358749#post2226758)

Let me know how it goes:D

---

### Post by Moe70 on 2007-03-16
> **mrmonday said:**
> Try this link:

[http://ubuntuforums.org/showthread.php?t=358749#post2226758](http://ubuntuforums.org/showthread.php?t=358749#post2226758)

Let me know how it goes:D

Brilliant!! :) worked. thanks very much

---

### Post by mrmonday on 2007-03-17
Excellent :D

---

