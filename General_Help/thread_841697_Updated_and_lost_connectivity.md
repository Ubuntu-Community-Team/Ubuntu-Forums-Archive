---
title: "Updated and lost connectivity"
date: 2008-06-26
forum: General Help
---

### Post by seeker1458 on 2008-06-26
I just built a hardy box, and got everything set up the way I wanted it. I was using a static IP. I downloaded and installed the updates (120), and now I cant get online. I changed the interface back to dhcp from static...still no luck. Where should I look, & what should I do?

---

### Post by Titan8990 on 2008-06-26
Is your DHCP server successfully giving you an IP? Did you restart networking or reboot after changing those settings?

---

### Post by seeker1458 on 2008-06-26
No, if I run ifconfig after setting the interface to dhcp, I dont get an ip address.  Yes i have restarted networking, and rebooted.

---

### Post by seeker1458 on 2008-06-26
contents of /etc/network/interfaces:

```
auto eth0
iface eth0 inet static
address 172.16.1.5
gateway 172.16.1.1
netmask 255.255.255.0
network 172.16.1.0
broadcast 172.16.1.255
```

---

### Post by seeker1458 on 2008-06-26
in regards to the DHCP server...it was recieving an address fine before I applied the updates.  Should know better than to fix something that isn't broken!!

---

### Post by Titan8990 on 2008-06-26
Did the updates include a kernel patch?

I see that in that list eth0 is still set to static. Is the DHCP server assigning addresses to your other systems? Do you have limit set on the number of DHCP clients?

---

### Post by seeker1458 on 2008-06-27
yes there is a defined dhcp pool, but it is not even close to being complelty assigned. 150 available address, and only about 40 PCs are in the office.

---

### Post by seeker1458 on 2008-06-27
here is the output of ifconfig

```
user@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:07:ed:c5
	  inet addr:172.16.1.5  Bcast:172.16.1.255  Mask:255.255.255.0
	  inet6 addr: fe80::20c:29ff:fe07:edc5/64 Scope:Link         
	  UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          
	  RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:636 (636.0 B)  TX bytes:8614 (8.4 KB)
          Interrupt:18 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24120 (23.5 KB)  TX bytes:24120 (23.5 KB)
```

---

