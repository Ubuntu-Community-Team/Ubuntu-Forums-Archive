---
title: "Recent upgrade of 16.04 broke DNS - HELP!"
date: 2018-09-02
forum: General Help
---

### Post by gene14 on 2018-09-02
Hi All -
I have three boxes running Ubuntu. Two are 16.04 and one is version 18. Everything was great until the 16.04 boxes auto-updated.

Both 16.04 boxes were rendered "DNS Impotent". I can ping the outside world as long as I supply the IP address. Pings using 'domain.com' (substitute your favorite domain here) go to the land of the "Unknown Host". nslookup domain.name results in 'Connection timed out;No servers could be reached'. I've read through a large number of posts on this problem, but none of the solutions were of any help.

I added nameserver 8.8.8.8 & nameserver 8.8.4.4 to /etc/resolvconf/resolv.conf.d/tail and now "nmcli device show enp3s0" shows these IP's along with the old default DHCP assigned IPs (see below). I tried "nslookup -d2 ..." but discovered I'm not knowledgeable enough to understand the output. (Incidentally, the '-d2' and '-deb' switches for nslookup do nothing whatsoever on the ver 18 box). At any rate, I've dumped a lot of information which I've included below in the hope that some one more skilled might just be able to help figure it out, or at least point me in the right direction. 
Any and all help is greatly appreciated.

Gene

```
&#65279;Script started on Sun 02 Sep 2018 01:44:28 PM CDT




#Brightstar#:#~#> ipconfig


ipconfig: Command not found.
#Brightstar#:#~#> ifconfig


enp3s0    Link encap:Ethernet  HWaddr 40:8d:5c:72:e7:dc  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::272b:5201:533c:140a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12413508 (12.4 MB)  TX bytes:3995337 (3.9 MB)


enp4s6    Link encap:Ethernet  HWaddr 00:04:5a:69:46:0c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:15 dropped:0 overruns:0 carrier:30
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4499 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4499 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:281830 (281.8 KB)  TX bytes:281830 (281.8 KB)










#Brightstar#:#~#> nmcli device show enp3s0


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         40:8D:5C:72:E7:DC
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.CONNECTION:                     enp3s0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.5/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
IP4.DNS[3]:                             205.171.1.65
IP4.DNS[4]:                             205.171.2.65
IP4.DOMAIN[1]:                          Home
IP6.ADDRESS[1]:                         fe80::272b:5201:533c:140a/64
IP6.GATEWAY:                            fe80::e618:6bff:feed:9229
IP6.ROUTE[1]:                           dst = 2602:3f:e5cf:3000::/64, nh = fe80::e618:6bff:feed:9229, mt = 100
IP6.ROUTE[2]:                           dst = fd00::/64, nh = fe80::e618:6bff:feed:9229, mt = 100








#Brightstar#:#~#> ip address


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s6: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 00:04:5a:69:46:0c brd ff:ff:ff:ff:ff:ff
3: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 40:8d:5c:72:e7:dc brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.5/24 brd 192.168.0.255 scope global dynamic enp3s0
       valid_lft 84985sec preferred_lft 84985sec
    inet6 fe80::272b:5201:533c:140a/64 scope link 
       valid_lft forever preferred_lft forever





#Brightstar#:#~#> ip route


default via 192.168.0.1 dev enp3s0  proto static  metric 100 
169.254.0.0/16 dev enp3s0  scope link  metric 1000 
192.168.0.0/24 dev enp3s0  proto kernel  scope link  src 192.168.0.5  metric 100 






#Brightstar#:#~#> cat /etc/network/interfaces


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback




#Brightstar#:#~#> cat /etc/resolv.conf


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 205.171.1.65
search Home
nameserver 8.8.8.8
nameserver 8.8.4.4








#Brightstar#:#~#> ls /etc/resolvconf/resolv.conf.d/tail


nameserver 8.8.8.8
nameserver 8.8.4.4








#Brightstar#:#~#> cat /etc/nsswitch.conf


# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.


passwd:         compat
group:          compat
shadow:         compat
gshadow:        files


#hosts:          files mdns4_minimal [NOTFOUND=return] dns
hosts:         files dns
 
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis








#Brightstar#:#~#> nslookup ubuntu.com


;; connection timed out; no servers could be reached






#Brightstar#:#~#> dig ubuntu.com




; <<>> DiG 9.10.3-P4-Ubuntu <<>> ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached






#Brightstar#:#~#> exit


Script done on Sun 02 Sep 2018 01:51:09 PM CDT



```

---

### Post by gene14 on 2018-09-03
by the way, I forgot to mention, the info above is from a Kubuntu system. The other 16.04 box is Ubuntu desktop (gnome).

---

### Post by sgian on 2018-09-04
There are two ethernet connections showing.  Have you tried disconnecting the second ethernet cable and rebooting?  Does it work if you only use one or the other cable, but not both at the same time?

---

