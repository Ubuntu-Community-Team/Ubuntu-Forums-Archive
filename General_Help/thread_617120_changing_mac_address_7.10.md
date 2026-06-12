---
title: "changing mac address 7.10"
date: 2007-11-19
forum: General Help
---

### Post by superbob666 on 2007-11-19
hi guys

i am trying to change my mac address, but i get an error with /etc/network/interfaces 


[B]auto eth0
iface eth0 inet dhcp
hwaddress ether 00:60:08:ad:c1:61[/B]


$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                        
  SIOCSIFHWADDR: Device or resource busy

Failed to bring up eth0.

---

### Post by komputes on 2007-11-19
I'm interested in learning to do this as well. I started searching google and found the following. Let me know if any of these answers work for you. Some people say certain ethernet cards don't let you override mac, but I don't think that's true, because it's simply a logical override. It may be disabled in this release, but why would they do that?

========
Solution 1
========

Bring down eth0 alone is not enough. You need to bring the whole networking module down, change your MAC and bring it up again.

Take down the networking module
```
/etc/init.d/networking stop
```

Edit the interfaces file.
```
sudo gedit /etc/network/interfaces
```

Manually overrive Hardware address (MAC):
```
    auto eth0
    iface eth0 inet dhcp
           hwaddress ether 69:69:69:69:69:69
```

Restart networking module
```
sudo /etc/init.d/networking restart
```

You will need to restart networking or reboot to take effect.

========
Solution 2
========
Found it on Guegole, this guy got the same error as you and this seemed to work for him.

```
oscar:~# ifconfig eth0 hw ether 10:10:10:10:10:10
SIOCSIFHWADDR: Device or resource busy
oscar:~# ifconfig eth0 down
oscar:~# ifconfig eth0 hw ether 10:10:10:10:10:10
oscar:~# ifconfig eth0 up
oscar:~# ifconfig eth0
eth0 Link encap:Ethernet HWaddr 10:10:10:10:10:10
inet addr:10.0.0.1 Bcast:10.0.0.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:19415294 errors:0 dropped:0 overruns:0 frame:0
TX packets:7756772 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:2589085448 (2.4 GiB) TX bytes:531912672 (507.2 MiB)
Interrupt:9 Base address:0x1800

```


========
Solution 3
========
Use macchanger
[http://www.debianadmin.com/change-your-network-card-mac-media-access-control-address.html]("http://www.debianadmin.com/change-your-network-card-mac-media-access-control-address.html")

*I would also recommend that after all of these, that you go into your router's control panel and check you DHCP log to see if the router has picked up on the spoof*

---

### Post by bigken on 2007-11-19
why would you want to change the mac address :confused:

---

### Post by louieb on 2007-11-19
> **bigken said:**
> why would you want to change the mac address :confused:
Hello bigken, Ever get that ladies PC fixed? From what I understand some DSL providers only allow access from a certain MAC address. At least that what my router guide says. My router allows  me to change  its MAC address for that reason.

---

### Post by teryowen on 2007-11-19
There is also something called MAC filtering on routers which means it lets in certain MAC address in but not others or denys cetrain ones, for this reason one might exploit a wireless network by spoofing their MAC address, it can also be used to test the networks security.

Solution 2 worked on my machine. but not solution 1.

---

### Post by bigken on 2007-11-19
i must have setup over a hundred routers for people of all makes and models and never had this sort of problem 

what a pain it must be

I would be looking to change my service provider and router for one that
does not implement these rules

---

### Post by IamAcoconut on 2007-12-05
> **bigken said:**
> i must have setup over a hundred routers for people of all makes and models and never had this sort of problem 

what a pain it must be

I would be looking to change my service provider and router for one that
does not implement these rules
1. How would such router know what [static] IP to give you, was it not assigned to a hardware address.
2. Mac-filtering makes sense in wireless networks.
3. Nobody said they can't just call their ISP and say they've changed an NIC. But it's not always possible all the time, so it's good to know how to avoid having to wait until monday with getting your network online. Sometimes 'customer-service' don't know what you're talking about. Some ISPs have a facist policy towards dividing the bandwidth you pay for between the computers you own. Sometimes you don't want to expose your original MAC in a public hot-spot. And so on.

---

### Post by bigken on 2007-12-05
> **louieb said:**
> Hello bigken, Ever get that ladies PC fixed? From what I understand some DSL providers only allow access from a certain MAC address. At least that what my router guide says. My router allows  me to change  its MAC address for that reason.


yo louieb ye I fixed it got all the files back ect :)

---

### Post by komputes on 2007-12-09
Does anyone know how to make this change at startup before the Ethernet controllers come up?

---

### Post by IamAcoconut on 2007-12-14
Add the script 
**ifconfig** <interface_name> ** hw ether** <new mac address>  to **/etc/init.d/networking** should do the trick.
Not sure where exactly to make it tidy, but just after the line begining with 'PATH' should be ok.

Note: Be extremely careful if you rely on connection to a remote computer via this particular interface!

---

### Post by komputes on 2007-12-14
> **IamAcoconut said:**
> 
Note: Be extremely careful if you rely on connection to a remote computer via this particular interface!

I don't quite understand what you mean by "rely on connection to a remote computer", do you mean that it will mess things up on setups such as LTSP (where you need to boot from a server).

If that is the case, is there any way to change the MAC before Ubuntu even boots up (like a script that runs at about the same time as grub)...hmmm all of this is very in.te.res.ting.

---

### Post by stchman on 2007-12-14
> **bigken said:**
> why would you want to change the mac address :confused:

A lot of times hackers will need to change the MAC address to obtain access into wireless connections that use MAC filtering.

The OP must have their reasons, lets hope they are not to hack someone's wireless connection.

---

### Post by komputes on 2007-12-15
> **bigken said:**
> why would you want to change the mac address :confused:

To bypass any type of MAC address filter mechanism, or to change your identification to force a new IP address to yourself from the DHCPd. It fools the connection into thinking you have put anther computer on the network. Some people change it to not have their NIC detected (like Apple users who do not want to be identified as Apple users on the network). It is used for testing on a network to see how it reacts to two computers with the same MAC address (some freeze up, others broadcast to both computers).

I think that's all I could think of, but I know there's more...

---

### Post by bigken on 2007-12-15
well you learn something new every day :)

---

### Post by komputes on 2007-12-20
> **IamAcoconut said:**
> Add the script 
**ifconfig** <interface_name> ** hw ether** <new mac address>  to **/etc/init.d/networking** should do the trick.
Not sure where exactly to make it tidy, but just after the line begining with 'PATH' should be ok.


This thread is [SOLVED]

This works, it changes my MAC addresses at startup:

```
ubuntu@ubuntu:~$ sudo gedit /etc/init.d/networking
```

This is the networking file after the MAC address change. The change is marked in bold (as operation "MACMACSPOOF"). Afterwards the script goes on to initialize networking (that part of the script is not included here).
```

#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          networking
# Required-Start:    mountkernfs ifupdown $local_fs
# Required-Stop:     ifupdown $local_fs
# Default-Start:     S
# Default-Stop:      0 6
# Short-Description: Raise network interfaces.
### END INIT INFO

PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"

[B]###HIDE REAL MAC ADDRESS AND PRETEND TO BE AN APPLE
###STARTING OPERATION MACMACSPOOF
ifconfig eth0 hw ether 00:30:65:29:00:0A
ifconfig eth1 hw ether 00:30:65:29:00:0B
ifconfig eth2 hw ether 00:30:65:29:00:0C
###END OF OPERATION MACMACSPOOF[/B]

###Networking script goes on...
```


A great resource to see what you are being recognized as (when you are on a network) is [http://coffer.com](http://coffer.com)
You can get or lookup any MAC address prefix on there.

Thank you for your help IamAcoconut.

---

### Post by cilynx on 2008-01-10
You can also install the macchanger package which has a bit nicer interface than using the low level options of ifconfig.  Both ways work fine, just depends on your style.

Personally, I use macchanger to get through an old Netgear router that decided that it didn't like the brand of NIC in my desktop.  Reset the MAC to a different vendor and it works fine.

---

