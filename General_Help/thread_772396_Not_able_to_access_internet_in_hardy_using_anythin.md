---
title: "Not able to access internet in hardy using anything other than firefox"
date: 2008-04-28
forum: General Help
---

### Post by prateekdayal on 2008-04-28
Hi

I have run into a very strange problem. I had been using ubuntu 7.10 and then i upgraded it to hardy beta and have kept it in sync will updates since then.

I had flock and spicebird installed (not through apt-get but using some tarballs unzipped in my home) on the hardy beta and they used to work just fine. However since I updated to the finaly hardy release, I can't seem to access internet from anything other than firefox 3.0 beta that shipped with the system. 

I tried redownloading flock, spicebird, firefox 2.0 but nothing can connect to the internet and I always get the server not found error for every address. apt-get wget all seem to be working fine though.

I would really appreciate any help here because firefox 3 won't work with firebug and all my development work has been pretty much stalled since then

Regards
Prateek Dayal

---

### Post by kaylus on 2008-04-28
Looking into your issue with connectivity, someone else might answer that faster. I do have some advice until that is corrected -- this is not so much a fix but a workaround until you get sorted:

I know Firebug 1.1.0b10 works with Firefox 3.0 :) b11 may work as well, but I'm not sure.

Kaylus

---

### Post by howlingmadhowie on 2008-04-28
that is very strange. do you have some sort of firewall installed? maybe
```
sudo iptables -L
```
says something unusual.

---

### Post by kaylus on 2008-04-28
Also, since your other browsers may be having issues due to the upgrade, I would try recreating the profiles:

> firefox -profilemanager

(make sure you are using firefox 2 or one of the other browsers to get to profile manager)

Kaylus

---

### Post by ghost_ryder35 on 2008-04-28
> **prateekdayal said:**
> Hi

I have run into a very strange problem. I had been using ubuntu 7.10 and then i upgraded it to hardy beta and have kept it in sync will updates since then.

I had flock and spicebird installed (not through apt-get but using some tarballs unzipped in my home) on the hardy beta and they used to work just fine. However since I updated to the finaly hardy release, I can't seem to access internet from anything other than firefox 3.0 beta that shipped with the system. 

I tried redownloading flock, spicebird, firefox 2.0 but nothing can connect to the internet and I always get the server not found error for every address. apt-get wget all seem to be working fine though.

I would really appreciate any help here because firefox 3 won't work with firebug and all my development work has been pretty much stalled since then

Regards
Prateek Dayal
what is the output of
```

ifconfig

```
and
```

iptables -L

```
#just like howling suggested
your iptables should look something similar to this unless you have modified yours extensivly
```

[root@localhost ~]# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:ssh 
REJECT     all  --  anywhere             anywhere            reject-with icmp-host-prohibited 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
REJECT     all  --  anywhere             anywhere            reject-with icmp-host-prohibited 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
[root@localhost ~]# 

```
 your ifconfig should look something like this except the ip's will be diffrent
```

[root@localhost ~]# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1C:23:A1:E0:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2203816 (2.1 MiB)  TX bytes:2203816 (2.1 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:1E:4C:4B:73:2E  
          inet addr:10.0.0.100  Bcast:0.0.0.0  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13561095 (12.9 MiB)  TX bytes:2765220 (2.6 MiB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-4C-4B-73-2E-F4-3F-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

[root@localhost ~]# 

```
One thing I might suggest while were trying to figure out your problem is that you blacklist ipv6 if you do not need it and also assign your self a static ip address via network manager
```

cd /etc/
sudo gedit modprobe.conf

```
then add these lines
```

blacklist net-pf-10
blacklist ipv6

```

---

### Post by prateekdayal on 2008-04-28
Hi

Thanks for the replies. No the iptables thing shows nothing really wrong. Here is the output

```
prateek@prateek-desktop:~/Softwares/firefox$ sudo iptables -L
[sudo] password for prateek: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination        

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   
``` 

The output of ifconfig is here
```
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:7f:6f:f9  
          inet addr:10.1.1.100  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe7f:6ff9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86296727 (82.2 MB)  TX bytes:17086619 (16.2 MB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4128153 (3.9 MB)  TX bytes:4128153 (3.9 MB)
```

I tried to see if iptables is running but i don't think its running (assuming this is how you check for it)
```

prateek@prateek-desktop:~/Softwares/firefox$ ps -ef | grep iptables
prateek   5538 28629  0 20:12 pts/0    00:00:00 grep iptables
```

I will try the static ip approach but since everything else (i mean wget etc) seems to be working am not sure if it will help

Thanks again for all the help

Regards
Prateek

---

### Post by ghost_ryder35 on 2008-04-28
You might also want to try blacklisting ipv6 if you dont use it.  It's helped me numerious times (mostly in Fedora but heh might as well try right)

---

### Post by kaylus on 2008-04-28
> I will try the static ip approach but since everything else (i mean wget etc) seems to be working am not sure if it will help

Thanks again for all the help

Regards
Prateek

Have you even attempted the profile approach? The GECKO based browsers are **normally share profiles**, while Firefox 3 uses a completely separate format. Profile corruption is not uncommon and it causing lack of connectivity has happened quite a bit where I work, and it has also been addressed on this forum with Gecko-based browsers not connecting while Opera has.

I understand the radical approaches offered as solutions, but I would at least attempt to rule out the common smaller issues prior to jumping the gun and switching network configurations around. Just startup the Firefox 2 with the **-profilemanager** switch and test it out.

Kaylus

---

### Post by prateekdayal on 2008-04-28
Hi

I tried disabling ipv6 and rebooting and voila everything worked!

I will also try the profile based approach and post the results here.

I would really appreciate if I can know why ipv6 should affect the connectivity issue for software that did not ship with ubuntu. If there is a pointer to a document, I can probably go through that too

Thanks again for all the help

Regards
Prateek

---

### Post by kaylus on 2008-04-28
> **prateekdayal said:**
> Hi

I tried disabling ipv6 and rebooting and voila everything worked!

I will also try the profile based approach and post the results here.

I would really appreciate if I can know why ipv6 should affect the connectivity issue for software that did not ship with ubuntu. If there is a pointer to a document, I can probably go through that too

Thanks again for all the help

Regards
Prateek

Prateek,

This is what I can assume judging by your actions so far, the settings for IPv6 in the old firefox profiles were different then your new one. The usual setting I've seen on a fresh install of 7.10/prev for Firefox was network.dns.disableIPv6 = false.

Changing that would correct your issue if, instead of disabling IPv6 system-wide, you left it on and opened up your Firefox2 browser and typed:

> about:config

In the address line.

Search for IPv6 and double click the line

> network.dns.disableIPv6
That will change it to true for that profile and should correct the issues. Deleting the profile would be a drastic measure of the same issue. 

The reasoning behind it is the way that Firefox comes setup to use IPv6 and the way your system, and ISP, handle the request. During the upgrade to 8.04 some setting might have toggled, or something may have occured somewhere. Either way, Firefox 2 doesn't seem to roll failed IPv6 requests very nicely.

Quote from Firefox Website

> 
Internet Protocol version 6 (IPv6) can cause connection problems on some Internet connections. Firefox uses IPv6 by default. Disable IPv6 to see if this solves your connection issues:

   1. In the Firefox Location bar, type about:config and press Enter.
   2. In the displayed list, type network.dns.disableIPv6 in the Filter textbox.
   3. Find the entry for network.dns.disableIPv6.
   4. If the value is false, right-click it and select Toggle.
          * If the value is true, IPv6 is already disabled, so it isn't causing your problem. 
   5. Close Firefox, start it again, and try to reach a web site. 

If disabling IPv6 doesn't resolve the problem, re-enable IPv6 by setting the preference back to false. 


Kaylus

---

### Post by stoneage on 2008-04-28
Genius! Thank you, that worked for me too. Flock stopped working after upgrading to Hardy - it was unable to connect to the net. Back online now.

---

### Post by aalper on 2008-05-07
I had the same problem with zend studio 5.5.1 and the suggested blacklisting worked for me too. It seems something has been changed in Ubuntu 8.04 that should NOT have been. This should be fixed asap. Has anyone reported this as a bug?

A

---

### Post by alexisbellido on 2008-10-15
I had the same problem with the new Flock 2 in Hardy 64 bits and fixed it by disabling IPv6 on the browser settings:

[Flock and Internet connection problem in Hardy]("http://ventanazul.com/webzine/articles/flock-internet-connection-lost-ubuntu").

It's strange that this has not happened to me with other browsers, such as Opera, only with every version of Flock.

---

