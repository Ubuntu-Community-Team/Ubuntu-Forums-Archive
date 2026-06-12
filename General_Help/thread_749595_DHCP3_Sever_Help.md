---
title: "DHCP3 Sever Help"
date: 2008-04-08
forum: General Help
---

### Post by Ryuujinx on 2008-04-08
So, I'm trying to get this box setup with webmin as a router like the last ubuntu box I made. 

Here's the network configuration: U-verse RG, Set to Leave Ubuntu box.

From there the Ubuntu Box, (10/100 input) out to a gigabit switch(gigabit card) then rest of the PCs.

```
server@ubuntu-router:~$ /etc/init.d/dhcp3-server restart
dhcpd self-test failed. Please fix the config file.
The error was:
server@ubuntu-router:~$

```

config file: 

```

ddns-update-style none;

option domain-name-servers 68.94.156.1, 68.94.157.7;

default-lease-time 86400;
max-lease-time 604800;

authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.100 192.168.1.254;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.1.255;
        option routers 192.168.1.1;
}

```


here's ifconfig -a

```
server@ubuntu-router:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:D3:1D:D1:AB
          inet addr:75.1.201.150  Bcast:75.1.207.255  Mask:255.255.240.0
          inet6 addr: fe80::213:d3ff:fe1d:d1ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4029008 (3.8 MB)  TX bytes:631058 (616.2 KB)
          Interrupt:17 Base address:0xc000

eth1      Link encap:Ethernet  HWaddr 00:1B:11:C3:28:45
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:11ff:fec3:2845/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1033 errors:0 dropped:0 overruns:0 frame:0
          TX packets:343 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:110014 (107.4 KB)  TX bytes:23250 (22.7 KB)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:162767 (158.9 KB)  TX bytes:162767 (158.9 KB)


```

eth1 = Internal
eth0 = External

Any other information you need to help me I can provide. I need to get this working ASAP :x

Thank you for the assitance

Also, Is there anyway to set the DNS servers (on the computer itself) to not change to the 192.168.1.254 of the RG and leave the actual custom defined DNS servers the same?

---

### Post by SpaceTeddy on 2008-04-09
> ddns-update-style none;

option domain-name-servers 68.94.156.1, 68.94.157.7;

default-lease-time 86400;
max-lease-time 604800;

authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.100 192.168.1.254;
       [B] option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.1.255;[/B]
        option routers 192.168.1.1;
}

i've never seen those two lines before. They are comming from the subnet (i.e. your network card) itself and should not be supplied by the dhcp. What happens if you take them out ?

also, have you actived the dhcp to listen on devices in your /etc/default/dhcp3-server ?

what does your syslog say towards the dhcp server not starting ? is there some more debug info on it ?

---

### Post by Ryuujinx on 2008-04-12
i actualy just wiped it re-isntalled ubuntu-server and set it up as a CSS server. Not worht the effort to get it working behind the RG atm when I'm moving soon.

---

