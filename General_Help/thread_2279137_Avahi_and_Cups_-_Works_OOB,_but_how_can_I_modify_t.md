---
title: "Avahi and Cups - Works OOB, but how can I modify the announced name?"
date: 2015-05-21
forum: General Help
---

### Post by mumie_die on 2015-05-21
Hi There,

I went trough the web and had a look at several tutorials and blog post on how to make a printer airprint compatible.
Unfortunatly most articles date back to the time, when one needed to create a service file for avahi to announce a printer.
By now it seems to work just by installing cups and avahi and enabling share.
Unfortunatly I get a printer called <<description>>@<<Servername>> eg. Farbdrucker@SVFOE01.
I woud rather prefer to use the printes name or queue name what would be eg. PRFOE101 since this is the standart description.

I thought of several ways to achive that:
[LIST]
[*]changing the description
[*]disable automatic sharing and create a manual .service file
[/LIST]
But on the other hand I suppose cups has to pass the data somehow to avahi and maybe uses a tamplate to do so. DBus might be involved in this inter service communication. I think that would be the cleanest solution, but I just don't know what or where to search for this information.

I hope somebody around here can help me with this.

Thanks

---

### Post by efflandt on 2015-05-22
I was wondering where you came up with that description@servername, but just enabled printer sharing and see where it comes from. Apparently it is the printername@your_hostname. So it should automatically use the name of your printer (in my case cups shows Description: Lexmark C543CMD:PS, which is actually a network printer Connection: socket://172.16.0.69:9100), but without the @hostname, not sure how anything local would resolve the MAC of your computer to get to your printer.```
efflandt@XPS-8100-1404:~$ avahi-browse -at
+   ham0 IPv6 Lexmark C543CMD:PS @ XPS-8100-1404            Internet Printer     local
+   ham0 IPv4 Lexmark C543CMD:PS @ XPS-8100-1404            Internet Printer     local
+  wlan0 IPv6 Lexmark C543CMD:PS @ XPS-8100-1404            Internet Printer     local
+  wlan0 IPv4 Lexmark C543CMD:PS @ XPS-8100-1404            Internet Printer     local
+  wlan0 IPv4 lexmark                                       Internet Printer     local
+   ham0 IPv6 Lexmark C543CMD:PS @ XPS-8100-1404            _ipps._tcp           local
+   ham0 IPv4 Lexmark C543CMD:PS @ XPS-8100-1404            _ipps._tcp           local
+  wlan0 IPv6 Lexmark C543CMD:PS @ XPS-8100-1404            _ipps._tcp           local
+  wlan0 IPv4 Lexmark C543CMD:PS @ XPS-8100-1404            _ipps._tcp           local
+   ham0 IPv6 Lexmark C543CMD:PS @ XPS-8100-1404            UNIX Printer         local
+   ham0 IPv4 Lexmark C543CMD:PS @ XPS-8100-1404            UNIX Printer         local
+  wlan0 IPv6 Lexmark C543CMD:PS @ XPS-8100-1404            UNIX Printer         local
+  wlan0 IPv4 Lexmark C543CMD:PS @ XPS-8100-1404            UNIX Printer         local
+   ham0 IPv6 XPS-8100-1404 [9e:0b:3d:82:61:33]             Workstation          local
+   ham0 IPv4 XPS-8100-1404 [9e:0b:3d:82:61:33]             Workstation          local
+  wlan0 IPv6 XPS-8100-1404 [78:e4:00:26:b8:ac]             Workstation          local
+  wlan0 IPv4 XPS-8100-1404 [78:e4:00:26:b8:ac]             Workstation          local
```Looking at that one line I thought maybe lexmark.local might work, but I guess not.```
efflandt@XPS-8100-1404:~$ ping -c1 lexmark.local
ping: unknown host lexmark.local

efflandt@XPS-8100-1404:~$ ping -c1 xps-8100-1404.local
PING xps-8100-1404.local (25.103.107.62) 56(84) bytes of data.
64 bytes from 25.103.107.62: icmp_seq=1 ttl=64 time=0.029 ms

--- xps-8100-1404.local ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.029/0.029/0.029/0.000 ms
```Which bounced off my wlan0 IP before, but this round bounced off my hamachi IP

---

