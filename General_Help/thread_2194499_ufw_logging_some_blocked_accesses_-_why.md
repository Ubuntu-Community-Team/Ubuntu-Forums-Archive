---
title: "ufw logging some blocked accesses - why?"
date: 2013-12-18
forum: General Help
---

### Post by PaulBx on 2013-12-18
Here are three examples I see in my log:
[11890.718335] [UFW BLOCK] IN=eth0 OUT= MAC=20:89:84:8e:e6:8c:00:1a:70:65:23:48:08:00 SRC=173.194.33.15 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=255 ID=14983 PROTO=TCP SPT=443 DPT=44110 WINDOW=0 RES=0x00 RST URGP=0 
[11890.718335] [UFW BLOCK] IN=eth0 OUT= MAC=20:89:84:8e:e6:8c:00:1a:70:65:23:48:08:00 SRC=173.194.33.15 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=255 ID=14983 PROTO=TCP SPT=443 DPT=44110 WINDOW=0 RES=0x00 RST URGP=0 
[11894.720069] [UFW BLOCK] IN=eth0 OUT= MAC=20:89:84:8e:e6:8c:00:1a:70:65:23:48:08:00 SRC=74.125.235.143 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=255 ID=16353 PROTO=TCP SPT=443 DPT=55323 WINDOW=0 RES=0x00 RST URGP=0 

I do not have any ports open as I just have a laptop, not any kind of server. The thing I'm wondering about is, why, if I am behind a router that has a firewall, am I seeing anything at all in my logs? The router is a linksys WRT54G; don't most such routers block anything initiated from the internet?

I could not find any of those source addresses in a reverse dns lookup.

---

### Post by 3rdalbum on 2013-12-19
Routers will automatically forward ports if your computer requests it. This is done through a system called Avahi, Bonjour, or UPnP. (maybe it has yet another name!)

If you are torrenting, you might have UPnP turned on in your Bittorrent program. Otherwise it might be an online game or something else that has activated UPnP.

If you want to turn it off completely, turn off UPnP in your router.

---

### Post by Topsiho on 2013-12-19
"I could not find any of those source addresses in a reverse dns lookup."

with whois, in a terminal, I find they are Google's addresses :)

Topsiho

---

### Post by PaulBx on 2013-12-19
UPnP *is* off in the router, as is any remote management. No ports are forwarded. I don't play games. I don't torrent. I don't see anything called Avahi or Bonjour in the router. Anything else? :)

Maybe this is what people mean when they say consumer-grade routers with old crappy firmware are easily attacked. I guess firewalls in a PC are not redundant after all. Maybe I need to get my pfsense router going pretty quickly.

I guess addresses can be spoofed, right? So it probably isn't really google...

---

### Post by pbrane on 2013-12-19
As Topsiho pointed out those IP addresses are google's. Could be google chrome if you run it.

---

### Post by Lars Noodén on 2013-12-19
You can use [netstat](http://manpages.ubuntu.com/manpages/saucy/en/man8/netstat.8.html) to see what process is making a connection to those ips.

```

netstat -npt

```

---

### Post by PaulBx on 2013-12-20
Thanks for that netstat command; however the trick is running it when the blocked access is happening. Anyway if the firewall is blocking these, how can any process have that connection?

I had eliminated google chrome from this system. I am running Seamonkey for a browser. When I run that netstat command now, all I see is Seamonkey connections.

---

### Post by Lars Noodén on 2013-12-20
Seamonkey would make sense.  The packets are coming from port 443 (https) on Google's servers, so it looks like it might be that part of a reply from a web page request is getting caught.  I'm not sure what to look at next, but one guess is that iptables is getting confused as to the state of a connection or at least a few packets in that connection.  Are there a lot of packets blocked for a connection?  Picking an ID and grepping for it might tell. e.g:

```

grep ID=14983 /var/log/syslog

```

---

