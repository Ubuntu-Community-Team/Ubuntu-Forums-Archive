---
title: "Cannot ping 127.0.0.1"
date: 2006-11-24
forum: General Help
---

### Post by eklypse on 2006-11-24
I cannot get my loopback to work.  Amsn give me an error that it cannot access it and to check the /etc/hosts file but that seems to  be fine.  Also I tried to ping 127.0.0.1 and it fails 100%.  On thing I found out also is that I cannot use Gedit but I can use nano to open files.  Also my internet works and I can renew my other ip addresses.  Everything but amsn, loopback and gedit seem to work.

---

### Post by taurus on 2006-11-24
What does your /etc/hosts look like then?

```
cat /etc/hosts
```

---

### Post by eklypse on 2006-11-24
> 127.0.0.1 localhost ellp105351.ellp105351
127.0.1.1 ellp105351.ellp105351

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

this is what I get ellp105351 is correct too.

---

### Post by eklypse on 2006-11-24
Also I cannot access webadmin or Azureus HTML UI.  It will just timeout.

---

### Post by eklypse on 2006-11-25
When I run ifconfig -a I get:

>  ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:0D:C0:19:61  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:dff:fec0:1961/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1926085 (1.8 MiB)  TX bytes:467269 (456.3 KiB)

eth1      Link encap:Ethernet  HWaddr 00:02:2D:7D:80:6B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xc100 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

And I see that lo is not looking so good, but have no idea how to fix it.

---

### Post by bruce449 on 2006-12-04
here is my ifconfig -a

and I am pindable

root@arco-id:/# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:DC:07:AA:BC  
          inet addr:192.168.1.144  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:dcff:fe07:aabc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:493 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71254 (69.5 KiB)  TX bytes:86931 (84.8 KiB)
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21840 (21.3 KiB)  TX bytes:21840 (21.3 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@arco-id:/# 

I hope it helps

Bruce

---

### Post by technodigifreak on 2006-12-04
It looks like your loopback device (lo) is down.  You should see **UP** for device lo when you run ifconfig, if you do not then it is down.  ifup/ifdown commands control the individual interfaces.  

I believe the command is:
**ifup lo**

This should bring interface lo up and you should be able to ping it.  I'm going to double check this and I'll edit this post as soon as I've confirmed it.

***********edit****************
The following console session will show you the before and after state, and the proper command is **sudo ifup lo**


```
 
vmadmin@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0C:29:95:42:73
          inet addr:192.168.151.68  Bcast:192.168.151.255  Mask:255.255.252.0
          inet6 addr: fe80::20c:29ff:fe95:4273/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:495474 (483.8 KiB)  TX bytes:16331 (15.9 KiB)
          Interrupt:177 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmadmin@ubuntu:~$ sudo ifup lo
vmadmin@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0C:29:95:42:73
          inet addr:192.168.151.68  Bcast:192.168.151.255  Mask:255.255.252.0
          inet6 addr: fe80::20c:29ff:fe95:4273/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4285 errors:0 dropped:0 overruns:0 frame:0
          TX packets:182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:528324 (515.9 KiB)  TX bytes:23441 (22.8 KiB)
          Interrupt:177 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

---

### Post by misty soul on 2006-12-10
I have exactly the same problem on one old laptop.
The loopback device seems to refuse beeing configured. I have tried "/etc/init.d/networking restart", this didn't change anything. I also tried "ifup lo" and got the error message "ifup: interface lo already configured". I succeded once with "ifdown lo" followed by "ifup lo" but am not sure this works every time.
This occurs every time this laptop is started (I have several other computers running edgy, they all work perfectly well). The same laptop did work well when it was running dapper. I cannot grasp why the loopback device of this specific old laptop behaves like this. This is a real problem as many services need the loopback device (local mail handling for example).

---

### Post by mschrenk on 2007-12-05
I had to do the same as misty soul, "ifdown lo" followed by "ifup lo".  That did fix it now, and I can ping myself.

---

