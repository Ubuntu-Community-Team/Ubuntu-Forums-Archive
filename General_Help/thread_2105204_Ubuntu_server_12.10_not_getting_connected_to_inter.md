---
title: "Ubuntu server 12.10 not getting connected to internet after install"
date: 2013-01-15
forum: General Help
---

### Post by tech291083 on 2013-01-15
Hi Friends,
 
I just installed Ubuntu Server 12.10 64-bit on a desktop pc that is connected to a router via LAN port. During the installation I unplug the LAN cable and forgot to configure DHCP as well. Now the system is working, but there is no internet connection for me to go ahead and install other packages more importantly a GUI/desktop to make it a system that I want it to be. Do I need to re-install the OS with the LAN connected to the router or is there a solution to this problem? Thanks.

---

### Post by TheFu on 2013-01-15
> **tech291083 said:**
> Hi Friends,
 
I just installed Ubuntu Server 12.10 64-bit on a desktop pc that is connected to a router via LAN port. During the installation I unplug the LAN cable and forgot to configure DHCP as well. Now the system is working, but there is no internet connection for me to go ahead and install other packages more importantly a GUI/desktop to make it a system that I want it to be. Do I need to re-install the OS with the LAN connected to the router or is there a solution to this problem? Thanks.

No need to reinstall. Just plug back in to the LAN port - it should receive an IP via DHCP automatically. Then you can** update**, **upgrade **and load any GUI packages that you like.

If you don't have a DHCP address - well, that is a different issue.

The output of **ifconfig** will tell us much. Please post.

---

### Post by tech291083 on 2013-01-15
Hi,
 
I plugged and unplugged the LAN cable a couple of times. Even restarted the router thrice, but to no avail. My other pc being a laptop works well with wireless internet using the same router, it has Win 7 on it. Please guide me. Output of ifconfig command is listed below. Thanks a lot.
 
 
```

 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2288 (2.2KB)  TX bytes:2288 (2.2KB)

```

---

### Post by TheFu on 2013-01-15
Well, no interface has been configured. I can't imagine that reinstalling with a network connection or 100% without any network connection for the entire time would be that much trouble. Just 10 minutes of effort.  I'd recommend that over all the troubleshooting we'd need to resolve the issue.

However, you could see of the network adapter is even recognized by Linux with 
$ **sudo lshw -C network**

It really shouldn't take much to reinstall, just either have the network or do not have the network connected for the entire installation process.

---

### Post by kpuz on 2013-01-15
what does your /etc/network/interfaces file look like? You may have to add the following:

auto eth0
iface eth0 inet dhcp

---

### Post by tech291083 on 2013-01-16
> **kpuz said:**
> what does your /etc/network/interfaces file look like? You may have to add the following:
 
auto eth0
iface eth0 inet dhcp
 
Mine had the following two lines..
 
 
```
 
auto lo
iface lo inet loopback

```
 
 
I used nano as root and deleted the above 2 lines and typed in the 2 lines that you gave. Now my internet is working via LAN port on a router. Thanks a lot indeed.

---

### Post by MasterJimmy on 2013-01-16
notspecifically on topic but i have noticed a whole host of issues with 12.10 that i never had with 12.04. some of them are just that the specific software i want isnt supported by 12.10 yet and a bunch of other little things that indivudually are not really a problem but taken together as a whole has really screwed up the experience for me. im going to be switching back to 12.04 because i never have any issues with LTS versions. as forwhat flavor, i havent decided kubuntu or ubuntu yet but k is winning so far

---

### Post by TheFu on 2013-01-16
> **tech291083 said:**
> Mine had the following two lines..
 ```
 
auto lo
iface lo inet loopback

``` 
I used nano as root and deleted the above 2 lines and typed in the 2 lines that you gave. Now my internet is working via LAN port on a router. Thanks a lot indeed.

You need to put those loopback lines back in. That is an important internal interface used by all sorts of program that need to communicate between each other inside the machine.  ADD, not REPLACE.

I'm sorta concerted that the eth0 lines weren't automatically added for you after a reboot. **Something important is still missing in your install.**

I'd check that eth0 is being assigned during boot and that the /etc/udev/r*/*net* file has the MAC of the NIC assigned to eth0 too.  If not, you probably want to reinstall the **udev** package.

---

### Post by tech291083 on 2013-01-17
> **TheFu said:**
> You need to put those loopback lines back in. That is an important internal interface used by all sorts of program that need to communicate between each other inside the machine.  ADD, not REPLACE.


Sorry, I have put them back. Thanks a lot.


> 
I'd check that eth0 is being assigned during boot and that the /etc/udev/r*/*net* file has the MAC of the NIC assigned to eth0 too.  If not, you probably want to reinstall the **udev** package.
Please have a look at the code below on my pc.

```
root@ubuntu:~# cat /etc/udev/rules.d/70-persistent-net.rules 
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="50:e5:49:49:91:76", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
root@ubuntu:~# 
root@ubuntu:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 50:e5:49:49:91:76  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:fe49:9176/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1212 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:1171922 (1.1 MB)  TX bytes:180365 (180.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

root@ubuntu:~# 

```

---

