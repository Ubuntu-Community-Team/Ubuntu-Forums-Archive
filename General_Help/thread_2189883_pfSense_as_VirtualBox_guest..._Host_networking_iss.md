---
title: "pfSense as VirtualBox guest... Host networking issues"
date: 2013-11-24
forum: General Help
---

### Post by talz13 on 2013-11-24
So this is what I'm trying to do:

1. Set up pfSense as a VirtualBox VM running on my Ubuntu server as the FW/Router.
2. Have the pfSense VM be the DHCP server for my home LAN.

Unfortunately, this doesn't seem possible without setting up a static IP / routing on my Ubuntu host.  If I have eth0 (the LAN card) set for DHCP, the boot process will hang waiting for network config since the pfSense VM is not up yet.  Eventually it moves on, but eth0 is not configured.

I tried setting up eth0 to be a static IP, etc., and that fixed most of the issue.  This is how I configured eth0:

```

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-nameservers 192.168.1.1

```

Where 192.168.1.1 is the LAN address of the pfSense VM.

But when I try to ping from the Ubuntu host to a website, I get:

```

jeff@server:~$ ping google.com
PING google.com (74.125.228.101) 56(84) bytes of data.
From server.home (192.168.1.2) icmp_seq=1 Destination Port Unreachable
From server.home (192.168.1.2) icmp_seq=2 Destination Port Unreachable
From server.home (192.168.1.2) icmp_seq=3 Destination Port Unreachable
^C
--- google.com ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms

```

Here's the output of the route command on the Ubuntu host:
```

jeff@server:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         pfSense.home    0.0.0.0         UG    100    0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
jeff@server:~$

```

---

### Post by bashiergui on 2013-11-24
The VM needs to have a bridged interface. Once the VM is up did you stop and fen start networking on the server? It would then get an IP from the VM.

---

### Post by talz13 on 2013-11-26
Ok, I'm back to trying to get everything working as I had it before pfSense...

Interestingly, I can ping my ubuntu server from my win7 pc, but I cannot ping my win7 pc from my ubuntu server:
```
C:\Users\Jeff>ping server

Pinging server [192.168.1.2] with 32 bytes of data:
Reply from 192.168.1.2: bytes=32 time<1ms TTL=64
Reply from 192.168.1.2: bytes=32 time<1ms TTL=64
Reply from 192.168.1.2: bytes=32 time<1ms TTL=64
Reply from 192.168.1.2: bytes=32 time<1ms TTL=64

Ping statistics for 192.168.1.2:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

C:\Users\Jeff>

```

```


jeff@server:~$ ping 192.168.1.4
PING 192.168.1.4 (192.168.1.4) 56(84) bytes of data.
^C
--- 192.168.1.4 ping statistics ---
21 packets transmitted, 0 received, 100% packet loss, time 19999ms

```

I restored my networking config on the server to auto / dhcp:

```
jeff@server:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
#iface eth0 inet static
#       address 192.168.1.2
#       network 192.168.1.0
#       netmask 255.255.255.0
#       broadcast 192.168.1.255
#       gateway 192.168.1.1
#       dns-nameservers 192.168.1.1

#The new Intel PCI-e card
#auto eth1
#iface eth1 inet static
#       address 0.0.0.0
#       netmask 255.255.255.0
#       hwaddress ether xxxxxxxxxxxxxxxxxx

```

and pinging web addresses still does not work from the ubuntu server:

```
jeff@server:~$ ping google.com
PING google.com (74.125.228.4) 56(84) bytes of data.
From server.home (192.168.1.2) icmp_seq=1 Destination Port Unreachable
From server.home (192.168.1.2) icmp_seq=2 Destination Port Unreachable
From server.home (192.168.1.2) icmp_seq=3 Destination Port Unreachable
From server.home (192.168.1.2) icmp_seq=4 Destination Port Unreachable
^C
--- google.com ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 2999ms

```

My route table looks right again, pointing to my router instead of the pfSense VM (which is no longer running, nor plugged into the network)
```
jeff@server:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         router          0.0.0.0         UG    100    0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0

```




Edit:

Also, even though I can't ping google, I can still use lynx to navigate to google from the command line:
```
                                                                          Google
   Search Images Maps Play YouTube News Gmail Drive More Â»
   Web History | Settings | Sign in

   Google

     _______________________________________________________
     Google Search  I'm Feeling Lucky                          Advanced search
                                                               Language tools

   Advertising Programs     Business Solutions     +Google     About
   Google

                          Â© 2013 - Privacy & Terms









http://www.google.com/imghp?hl=en&tab=wi

```

---

### Post by talz13 on 2013-11-28
Well, I figured out one part.  My win7 PC had the windows firewall on, and was not responding to ICMP ping requests.  I added a rule to allow that, and now I am able to ping my win7 PC from my ubuntu server.

However, I'm still concerned why the ubuntu server can't ping WAN addresses, responding with the "Destination Port Unreachable".

---

### Post by capedra on 2013-12-04
I'm facing exactly this same issue that you're dealing with.  :(

---

### Post by bashiergui on 2013-12-05
I had some odd networking issues with a linux vm in virtualbox. It was fixed when I rebuilt the vm and gave it more disk space. Check that the vm has more than the minimum size limit.

---

### Post by talz13 on 2013-12-05
> **capedra said:**
> I'm facing exactly this same issue that you're dealing with.  :(

What is the current state of your issue?  I can try to help with anything that I figured out in my limited experience.



Edit: I'll also add that I am currently using my pfSense VM as my "router" for my LAN now.  I've turned off DHCP and WAN on my ASUS router, and plugged the cable modem in directly to the VM's NIC.  Everything appears to be working, aside from my ability to successfully ping WAN addresses outside of Time Warner's network from my Ubuntu server or the pfSense VM.  Other PCs on my LAN can ping google.com, et. al. perfectly fine.

---

