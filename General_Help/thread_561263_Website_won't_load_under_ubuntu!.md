---
title: "Website won't load under ubuntu!"
date: 2007-09-27
forum: General Help
---

### Post by KitChy on 2007-09-27
So yeh, basically when I try to access [http://cue.cf.ac.uk](http://cue.cf.ac.uk) using FF and Ubuntu the website doesn't load and just hangs. I've tried to ping the website using the network tools in Ubuntu and nothing is returned. However, my friend who also uses Ubuntu has the same problem and the page doesn't load, but when he boots into Windows the site loads perfectly using FF. Also when his friend, who is on the same network as him tries to access the website using Windows, he is able to view the site. Does anyone know why this is happening, but not only why it happens, but why it seems to be just specific to Ubuntu

Thanks

---

### Post by aashay on 2007-09-27
Website loading fine using FF 2.0.0.4 pre

---

### Post by Keyper7 on 2007-09-27
Loading fine here with Firefox 2.0.0.7 in Ubuntu 7.04 amd64.

Is the network connection properly configured? Do other sites load fine?
Can it be that someone blocked that specific ip in the firewall?

---

### Post by rfruth on 2007-09-27
all okay here :confused:

---

### Post by DomZ on 2007-09-27
I'm the other guy it doesn't load for. All other sites load with no problems, and it happened back home on my ADSL connection, and is still happening now that I am in a completely different location/ISP etc.

Anyways I havn't got any firewalls or anything installed, heres the output of my "ifcoinfig". Not that it really matter as I said earlier it has happened when I used adsl (ppp0) back home, eth0 (wired ethernet direct to the cable modem at the location I am at now) and also eth1 which is the wireless interface.

```

eth0      Link encap:Ethernet  HWaddr 00:15:C5:B8:B7:ED  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:71:04:6C  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe71:46c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1750549 errors:29 dropped:9654 overruns:0 frame:0
          TX packets:1606340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1639559959 (1.5 GiB)  TX bytes:1061408123 (1012.2 MiB)
          Interrupt:16 Base address:0xa000 Memory:dfdff000-dfdfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6188 (6.0 KiB)  TX bytes:6188 (6.0 KiB)

```

Here's the output of my "route" command. I don''t see anything exciting here either?


```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```

If I do a traceroute from the network tools in system, the last few hops are:

```

11. LLNW-W1.site.ja.net (146.97.42.94)
12.  card-lln-swman.welshnetworking.net (193.63.78.5)
13. sar-bi4k.cf.swman.net.uk (194.83.179.78)
14. *
15. *

```

If I run the command "netstat" while the page is trying to load I get:

```

tcp        0      0 domz-laptop.local:56290 vleappcl.cf.ac.uk:www   ESTABLISHED

```

I've tried opera and konqueror as well, non of which load the site either. The site used to load and randomly stoppped working in the summer, I assumed the server was down, and can't remember if I installed anything at the particular time.

Any idea's on what could be causing this? Or how I can find out what exactly is happening? Any help is greatly appreciated as that site is a key part of my university course, and I don't want to be booting into windows whenever I need to use it.

---

### Post by aashay on 2007-09-29
not a solution, but maybe you could try with IE6 running under wine

---

### Post by dennis1200 on 2007-10-01
I'm having the same problem, currently running Gutsy Beta, with Firefox 2.0.0.6+2-0ubuntu4. I realize that this is a development build, but like the original post, pinging from a terminal fails as well. Firefox under WINE also fails on the same sites (unfortunately, sites like google.com). Epiphany doesn't work right either. I can do everything fine in Windows, also in Firefox, so it pretty clearly seems to be a system issue.

I've looked around, and suspect it may be something to do with the DNS cache, but haven't found anything on how to flush the DNS cache in Linux (plenty for Windows and Mac), or the solutions are based on problems with programs that I don't even have installed (programs for running a DNS server on the computer). I did restart my router, so that the router would clean its DNS cache, but that didn't solve my problem. Still, KitChy - worth a shot.

I may be wrong, and would love to hear whether KitChy is running Gutsy or not. I'm just going to stick it out until the release candidate, I guess.

---

### Post by dennis1200 on 2007-10-02
**[COLOR="Red"]SOLUTION[/COLOR]** (at least for me):

I followed the instructions [_[COLOR="Red"]here[/COLOR]_]("https://www.opendns.com/start?device=ubuntu") to set my DNS servers to OpenDNS. All websites load normally, instantly. Google is back, hurrah!

If that is one of the websites to which you can't connect, here are the instructions:
> 
Open a terminal window and type the following.

  ```
sudo network-admin
```

Change to the DNS tab and enter the following two addresses in the top of the first field labeled DNS Servers.
    208.67.222.222
    208.67.220.220

To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ sudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

I had to change eth0 to wlan0 for my interface (which is another story; it was eth1 until Gutsy came along and suddenly changed it).

---

