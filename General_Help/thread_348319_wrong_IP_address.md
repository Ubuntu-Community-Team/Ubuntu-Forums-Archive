---
title: "wrong IP address"
date: 2007-01-28
forum: General Help
---

### Post by dlenmn on 2007-01-28
Howdy,
I'm running Kubuntu 6.10 x64 and I've got a weird problem. When I start up my system, my computer decides its IP address is 169.254.250.143. It shows this both under the network settings preference and with ifconfig. However, I have no trouble doing stuff online... but it reports that IP address to dyndns, which is annoying.

Anyhow, in network settings, when I click "Disable Interface" then "Enable Interface" I get a reasonable IP address and everything keeps working fine. However, I don't want to do that every time I start my comp... Any advice? Thanks
-Leon

---

### Post by phossal on 2007-01-28
That sounds a little like a configuration problem. For example, if you're using  a DSL modem and a switch/router, it's like you're being assigned an IP from the DSL router. 

What is your setup like?

---

### Post by dlenmn on 2007-01-28
I'm connected to my college's network via ethernet... I can't think of anything unusual about my setup. This also happened when I was at home and I was connected to a linksys router that was in turn connected to a cable modem.

---

### Post by phossal on 2007-01-28
It always reports the *same* IP initially?

---

### Post by dlenmn on 2007-01-28
Yes, I believe so.

---

### Post by phossal on 2007-01-28
What's in /etc/network/interfaces?
```
sudo gedit /etc/network/interfaces
```

---

### Post by dlenmn on 2007-01-29
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface

iface eth0 inet dhcp

iface wlan0 inet dhcp



iface eth1 inet dhcp

auto eth1

---

### Post by dlenmn on 2007-01-30
bump...

---

### Post by dlenmn on 2007-02-01
Here's an example of what I'm talking about... Nonsense IP address, then I take the interface down, then up, and the IP address is reasonable... Anyone spot anything wrong?

```
lnm@LeonsKubuntuBox:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:17:31:D9:0D:8B
          inet addr:169.254.250.143  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::217:31ff:fed9:d8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60489 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:57118130 (54.4 MiB)  TX bytes:5569852 (5.3 MiB)
          Interrupt:10 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:145143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:89462974 (85.3 MiB)  TX bytes:89462974 (85.3 MiB)

lnm@LeonsKubuntuBox:~$ sudo ifdown eth1
Password:
There is already a pid file /var/run/dhclient.eth1.pid with pid 3639
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:17:31:d9:0d:8b
Sending on   LPF/eth1/00:17:31:d9:0d:8b
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 129.170.16.4 port 67
lnm@LeonsKubuntuBox:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:17:31:d9:0d:8b
Sending on   LPF/eth1/00:17:31:d9:0d:8b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 129.170.146.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 129.170.146.1
bound to 129.170.146.159 -- renewal in 10783 seconds.
lnm@LeonsKubuntuBox:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:17:31:D9:0D:8B
          inet addr:129.170.146.159  Bcast:129.170.146.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fed9:d8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:57525881 (54.8 MiB)  TX bytes:5587441 (5.3 MiB)
          Interrupt:10 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:145518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:89685448 (85.5 MiB)  TX bytes:89685448 (85.5 MiB)

```

---

### Post by phossal on 2007-02-02
Do me a favor and play a little game with your settings, if possible. Do you have access/permissions to shut down both your machine *and* the router? If you can do so, I'm curious to know if you're really being assigned the *same* IP each time, which would lead us down one path, or if you're being assigned IPs from a different network, from your ISP, for example.

Ideally, you'll shut down both your machine and the router in order to disconnect from the ISP. That way, we can see if your machine really gets the same address.

---

### Post by dlenmn on 2007-02-03
I have no access to the router. Like I said, I'm on my college's network and they don't just let students turn it off! I know that on Windows and OS X, an ip address starting with 169 is a self assigned IP address -- one a computer makes up when it can't connect to a DHCP server. I assume the same thing is true on linux. I can say without a doubt that 169.254.250.143 is not my real IP address (also, that is the address it gets every time -- I'm sure of it now). First off, my college does not assign IP address starting with 169. Also, when I try to ping 169.254.250.143 with my other computer, I get no responce. On my network, IP address assigned to computers connected via ethernet start with 127.

So, I assume this IP address is self assigned. Maybe the DHCP daemon tries to get an IP address before the ethernet connection is good to go. Who knows? All I know is that my initial IP address if bad (but I still have internet access for reasons that are unclear), but I get a good one when I renew it.

If I knew more about things linux, I could probably make myself a little script that automatically renews my IP address (aka ifdown eth1 then ifup eth1) say one minute after kubuntu loads up. It would be a kludge, but it would fix my problem. Any takers?

"Note: Addresses in the self-assigned range (169.x.x.x) are usually not routed for traffic on the public Internet. A 169 address typically indicates that your DHCP server is not assigning you a valid IP address or that you cannot connect to the network to receive the address."
[http://docs.info.apple.com/article.html?artnum=106879](http://docs.info.apple.com/article.html?artnum=106879)

"If the IP address which starts with 169.x.x.x, Windows has assigned you an automatic IP because it did not receive one from your Internet service provider."
[http://support.microsoft.com/kb/326155](http://support.microsoft.com/kb/326155)

---

### Post by phossal on 2007-02-03
Some network devices "record" settings. I wonder if you own one, and it's "saved" its IP from the last time you ran it in *Windows*?

---

### Post by dlenmn on 2007-02-03
That's possible, although I've never seen windows get such an IP address -- every time I've looked it has had a reasonable IP address. Anyhow, I took a peak in my log files -- when I turned on my computer, dhclient got me a reasonable IP address -- 129.170.146.159. It has renewed that IP address since then. However, my IP address is still shown as that unreasonable one. I'm not sure what to make of that...

```
lnm@LeonsKubuntuBox:~$ cat /var/log/syslog | grep dhclient
Feb  3 08:34:55 LeonsKubuntuBox dhclient: DHCPREQUEST on eth1 to 129.170.16.4 port 67
Feb  3 08:34:55 LeonsKubuntuBox dhclient: DHCPACK from 129.170.16.4
Feb  3 08:34:55 LeonsKubuntuBox dhclient: bound to 129.170.146.159 -- renewal in 1755 seconds.
Feb  3 09:04:10 LeonsKubuntuBox dhclient: DHCPREQUEST on eth1 to 129.170.16.4 port 67
Feb  3 09:04:10 LeonsKubuntuBox dhclient: DHCPACK from 129.170.16.4
Feb  3 09:04:10 LeonsKubuntuBox dhclient: bound to 129.170.146.159 -- renewal in 8307 seconds.
Feb  3 11:22:37 LeonsKubuntuBox dhclient: DHCPREQUEST on eth1 to 129.170.16.4 port 67
Feb  3 11:22:37 LeonsKubuntuBox dhclient: DHCPACK from 129.170.16.4
Feb  3 11:22:37 LeonsKubuntuBox dhclient: bound to 129.170.146.159 -- renewal in 8102 seconds.
lnm@LeonsKubuntuBox:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:17:31:D9:0D:8B
          inet addr:169.254.250.143  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::217:31ff:fed9:d8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:49026855 (46.7 MiB)  TX bytes:4474386 (4.2 MiB)
          Interrupt:10 Base address:0x2000
```

---

