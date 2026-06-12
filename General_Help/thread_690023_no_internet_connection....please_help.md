---
title: "no internet connection....please help"
date: 2008-02-07
forum: General Help
---

### Post by fouadk on 2008-02-07
hi everyone....


this is the third time i post here and get no help , not even a reply so please help me...

my problem is that i installed ubuntu 7.10 on my hp laptop dv6000 and i have no internet connection...

the laptop is wired to a d-link router which takes care of connecting to the internet.....

the router is configured with DHCP....

my problem is that when i plug the cable to the laptop i get no internet connection and i cant even pin the router....works smoothly with vista....why ?????????????

please help and thanks in advance...

---

### Post by apetresc on 2008-02-07
What is the output of ```
sudo dhclient
```?

---

### Post by fouadk on 2008-02-07
thanks for your reply....i will try that as soon as i get home....

btw is the output of this command will be the same on livecd coz i have uninstalled ubuntu due to non functionning intenet...so if it works i will install it again....

will get back to you as soon as i try it

thanks in advance

---

### Post by fouadk on 2008-02-07
hey adrian this is the output of the sudo dhclient

```

Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:00:00:1a:73:c7
Sending on   LPF/eth1/00:00:00:1a:73:c7
Listening on LPF/eth3/00:00:6c:2d:f6:a9
Sending on   LPF/eth3/00:00:6c:2d:f6:a9
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
send_packet: Network is down
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

i noticed the subnet 255.255.255.255,,, my router is configured with 255.255.255.0...i dunno if its relevant but please help me....

thanks  in advance

---

### Post by bwtranch on 2008-02-07
If you un-installed Ubuntu, we're not going to have anything to go on. The output of that last file didn't mean much. The network is down (we already knew that). Please post the output of ifconfig and , well that's enough. There is a driver that is not loading at startup and/or no DHCP client listing.

---

### Post by bwtranch on 2008-02-07
i noticed the subnet 255.255.255.255,,, my router is configured with 255.255.255.0...i dunno if its relevant but please help me....

That is the correct subnet mask 255.255.255.0

---

### Post by fouadk on 2008-02-08
the output of ifconfig is the following

```

eth8   Link encap:Ethernet  HWaddr 00:00:6C:D2:C0:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

i have noticed something that every time i restart ubuntu the numbering of eth add up so now you see that it is eth8 but when i first installed ubuntu it was eth0 and every time i restart it add 1 as if ubuntu is considering it a new network card and i also noticed that every time i restart the physical address changes and it is also different from the one windows shows(the correct one).....

please help

thanks in advance

---

### Post by BLTicklemonster on 2008-02-12
I installed 7.10 last night, and even using the live cd, I have no internet. I installed XP back to the box because there's some mapping and scripting to do that I can't do in linux, so I put XP in first, then ubuntu, but ubuntu just does not want to have internet connection at all. But XP connects just fine. Never had a problem with ubuntu connecting til now...

I was using an older copy from when gutsy first came out, so I've downloaded the .iso last night, and will burn it and try to see if maybe there was something wrong with the old copy.

---

### Post by ugm6hr on 2008-02-12
In general, Ubuntu should have no problems with wired ethernet.

Potential issues:

1. Unsupported LAN chipset.
The output from this command will identify your chipset:
```
lspci
```
This will give your driver:
```
lshw -C network
```

2. Dual-boot with Windows using network "power save" function.
[http://ubuntuforums.org/showpost.php?p=4077372&postcount=14](http://ubuntuforums.org/showpost.php?p=4077372&postcount=14)

3. ipv6
Don't know much about this, but it apparently makes a mess of networking on some systems.

---

### Post by BLTicklemonster on 2008-02-12
This just figures. I go to all the trouble of getting ready, I plug my laptop in to the network to make sure I have the dns and all settings correct, and start the live cd. 

At which point I have internet.

I install.

I reboot. 

I get to the desktop.

I have a connection to the internet.

Go figure.

Good luck getting yours going!

---

