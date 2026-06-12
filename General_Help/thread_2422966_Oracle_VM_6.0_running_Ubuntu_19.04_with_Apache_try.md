---
title: "Oracle VM 6.0 running Ubuntu 19.04 with Apache trying to access web site"
date: 2019-07-15
forum: General Help
---

### Post by sigmano on 2019-07-15
I have a virtual machine (Ubuntu 19.04) with the following installation:
[LIST]
[*]Apache 
[*]PHP 
[*]MySQL 
[*]phpMyAdmin 
[/LIST]

Now I want to access Apache from my Windows machine that is hosting Ubuntu 19.04.

In Ubuntu I can see that Apache is listening on port 80, and that my IP is 10.0.2.15. 
On Ubuntu I can access [http://10.0.2.15](http://10.0.2.15), but on the Windows host I cant.

[URL="https://ibb.co/P1ycNDF"][IMG]https://i.ibb.co/XFP7bYj/ip.png[/IMG]

[/URL]> samsmith2024@phpserver:~$ sudo netstat -nap | grep apache
[sudo] password for samsmith2024:
tcp6       0      0 :::443 :::*                    LISTEN      781/apache2
[COLOR=#ff0000]**tcp6       0      0 :::80 :::*                    LISTEN      781/apache2**[/COLOR]

samsmith2024@phpserver:~$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
group default qlen 1000
     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
     inet [127.0.0.1/8]("http://127.0.0.1/8") scope host lo
        valid_lft forever preferred_lft forever
     inet6 ::1/128 scope host
        valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel 
state UP group default qlen 1000
     link/ether 08:00:27:48:43:7c brd ff:ff:ff:ff:ff:ff
     inet [[COLOR=#ff0000]**10.0.2.15**[/COLOR]/24]("http://10.0.2.15/24") brd 10.0.2.255 scope global dynamic noprefixroute 
enp0s3
        valid_lft 85996sec preferred_lft 85996sec
     inet6 fe80::582e:9ad4:5bb3:7aa2/64 scope link noprefixroute
        valid_lft forever preferred_lft forever



Any suggestions?

---

### Post by SeijiSensei on 2019-07-15
Is the Windows machine in the 10.0.2.0/24 subnet? If not, does it have a route to that network?

Since the problem is with Windows, you'll need to see that it has the proper network configuration to reach the server.

Can the Windows machine ping 10.0.2.15?

---

### Post by sigmano on 2019-07-15
Windows is connected to a router on 192.168.1.1. It gives me my IP dynamicly (my Windows IP is 192.168.1.2).
Windows cannot reach Ubuntu with ping.

[B]

C:\Users\bruker>ping 10.0.2.15[/B]

Pinging 10.0.2.15 with 32 bytes of data:
[COLOR=#ff0000]Request timed out.[/COLOR]

Ping statistics for 10.0.2.15:
    Packets: Sent = 1, Received = 0, Lost = 1 (100% loss),

**C:\Users\bruker>ipconfig**

Windows IP Configuration


Ethernet adapter Ethernet:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Ethernet adapter VirtualBox Host-Only Network:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::e06b:c8e5:b20:1365%8
   IPv4 Address. . . . . . . . . . . : 192.168.56.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :

Wireless LAN adapter Lokal tilkobling* 1:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Lokal tilkobling* 3:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Wi-Fi:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::b5ab:8039:13fe:778%13
   IPv4 Address. . . . . . . . . . . : **192.168.1.2**
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : **192.168.1.1**

Ethernet adapter Bluetooth-nettverkstilkobling:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

---

### Post by sigmano on 2019-07-15
Ok, so you pointed me in the right direction.
I changed network to "Host-only adapter" in Oracle VM VirtualBox Manager. 
Now it works! 

Thank you!

---

