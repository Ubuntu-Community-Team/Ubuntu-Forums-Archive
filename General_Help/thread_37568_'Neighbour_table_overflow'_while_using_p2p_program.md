---
title: "'Neighbour table overflow' while using p2p programs"
date: 2005-05-27
forum: General Help
---

### Post by NeTo on 2005-05-27
I have just installed today amule, as a replacement for emule (that I was using on windows). This is the first connection-intensive program I try on Linux (since Im very new at it :p)

Anyway, after leaving amule running for several minutes with a big list of files I started noticing several connection problems. Web pages didn't open, host names weren't resolved, I was unable to ping my adsl router and so on.

I checked my router config and the amule settings and they were both ok. When running dmesg I found several of the following messages: "Neighbour table overflow."

Looking on the net I found the following solution: echo 10000 > /proc/sys/net/ipv4/neigh/default/gc_thresh3

It seems to work so far, but I'm puzzled on what that is doing (I barely understand what ARP is about anyway). Why isn't the value set to something higher by default? What should I do to keep that setting on reboot?

---

### Post by MrTom on 2005-05-27
As far as I understand it (someone correct me if i'm wrong) -

ARP translates between IP and MAC (Hardware) addresses.

Neighbour table or ARP cache keeps track of the machines you recently talked to.

The thing that bothers me is that your cache should only contain the MAC addresses of machines on your local network (mine has 2 to 6 entries!). Makes me think your network configuration is a little messed up.

what do 'ifconfig' and 'route' say?

---

### Post by NeTo on 2005-05-27
Uhm, actually I don't remember to have setup anything, maybe there is something I missed. Actually there's one thing: On install I choosed to configure my network settings from a dhcp server (my adsl router). I setup the router in ZIPB bridging mode  (Zero Installation PPP Bridging) so it acts like an ethernet modem.

Here's what ifconfig returns:```
eth0      Link encap:Ethernet  HWaddr 00:E0:7D:D7:57:B3
          inet addr:200.126.91.163  Bcast:200.126.91.163  Mask:255.255.255.255
          inet6 addr: fe80::2e0:7dff:fed7:57b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4003149 (3.8 MiB)  TX bytes:4682537 (4.4 MiB)
          Interrupt:19 Base address:0xb800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:559315 (546.2 KiB)  TX bytes:559315 (546.2 KiB)
```

route:```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         200-126-91-163. 0.0.0.0         UG    0      0        0 eth0

```

---

### Post by MrTom on 2005-05-28
Thats cool, you are directly connected to the internet via that bridging malarky, when you connected amule you saw a lot of IPs in a short space of time - and the table overflowed.

the command

echo 10000 > /proc/sys/net/ipv4/neigh/default/gc_thresh3

sets the hard limit size of the table to 10000, this is probably not want you want. Try setting gc_thresh1 to a lower limit say 2048 then increasing till the problem goes away, using powers of 2 is the best for maximum effienciency.

To set this value every time create a little shell script with the command in, chmod +x then place in the /etc/network/if-up.d/

Hope that was of some help, I still think someones arp config may be borked - but it's probably not yours :) If you want to look at your arp cache, the command 'arp' will print it (if the table is huge arp -an will be faster)

---

### Post by NeTo on 2005-05-31
[QUOTE=MrTom]Thats cool, you are directly connected to the internet via that bridging malarky, when you connected amule you saw a lot of IPs in a short space of time - and the table overflowed.

the command

echo 10000 > /proc/sys/net/ipv4/neigh/default/gc_thresh3

sets the hard limit size of the table to 10000, this is probably not want you want. Try setting gc_thresh1 to a lower limit say 2048 then increasing till the problem goes away, using powers of 2 is the best for maximum effienciency.

To set this value every time create a little shell script with the command in, chmod +x then place in the /etc/network/if-up.d/

Hope that was of some help, I still think someones arp config may be borked - but it's probably not yours :) If you want to look at your arp cache, the command 'arp' will print it (if the table is huge arp -an will be faster)[/QUOTE]

Thank you very much for help so far. I have one remaining doubt. If I set gc_thresh1 to 2048 do I need to set the other 2 files (gc_thresh2 and gc_thresh3) to greater or equal values? Or I is it correct to have gc_thresh1>gc_thresh2?

Ona  side note, I would like to read more on this topic. However I seem to find little on the net, mostly "do an echo 10000>...." stuff. By any chance do you know where I can I get more info on this?

---

