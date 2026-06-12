---
title: "About iptables rules"
date: 2007-08-24
forum: General Help
---

### Post by satimis on 2007-08-24
Hi folks,


Ubuntu 7.04 lamp server amd64 - Host OS
VMware
Guest OS - not yet installed.
Iptables-1.3.6


$ cat /etc/network/interfaces```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        gateway 192.168.0.1

```


Browser can connect Internet w/o problem.


After performing following steps to setup iptables, Internet connection blocked.

Edited /etc/rc.local and entered following rules on it```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#exit 0

#
# INPUT
#

# allow all incoming traffic from the management interface NIC
# as long as it is a part of an established connection
iptables -I INPUT 1 -j ACCEPT -d 192.168.0.10 -m state --state RELATED,ESTABLISHED

# allow all ssh traffic to the management interface NIC
iptables -I INPUT 2 -j ACCEPT -p TCP -d 192.168.0.10 --destination-port 22

# allow all VMware MUI HTTP traffic to the management interface NIC
iptables -I INPUT 3 -j ACCEPT -p TCP -d 192.168.0.10 --destination-port 8222

# allow all VMware MUI HTTPS traffic to the management interface NIC
iptables -I INPUT 4 -j ACCEPT -p TCP -d 192.168.0.10 --destination-port 8333

# allow all VMware Authorization Daemon traffic to the management interface NIC
iptables -I INPUT 5 -j ACCEPT -p TCP -d 192.168.0.10 --destination-port 902

# reject all other traffic to the management interface NIC
iptables -I INPUT 6 -j REJECT -d 192.168.0.10 --reject-with icmp-port-unreachable


#
# OUTPUT
#

# allow all outgoing traffic from the management interface NIC
# if it is a part of an established connection
iptables -I OUTPUT 1 -j ACCEPT -s 192.168.0.10 -m state --state RELATED,ESTABLISHED

# allow all DNS queries from the management interface NIC
iptables -I OUTPUT 2 -j ACCEPT -s 192.168.0.10 -p UDP --destination-port 53

# reject all other traffic from localhost
iptables -I OUTPUT 3 -j REJECT -s 127.0.0.10 --reject-with icmp-port-unreachable

# reject all other traffic from the management interface NIC
iptables -I OUTPUT 4 -j REJECT -s 192.168.0.10 --reject-with icmp-port-unreachable

```


$ sudo /etc/init.d/rc.local start```

 * Running local boot scripts (/etc/rc.local)                                                     [ OK ] 

```

$ sudo iptables -L```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             192.168.0.10        state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:8222 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:8333 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:902 
REJECT     0    --  anywhere             192.168.0.10        reject-with icmp-port-unreachable 
ACCEPT     0    --  anywhere             192.168.0.10        state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:8222 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:8333 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:902 
REJECT     0    --  anywhere             192.168.0.10        reject-with icmp-port-unreachable 
ACCEPT     0    --  anywhere             192.168.0.10        state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:8222 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:8333 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:902 
REJECT     0    --  anywhere             192.168.0.10        reject-with icmp-port-unreachable 
ACCEPT     0    --  anywhere             192.168.0.10        state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:8222 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:8333 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:902 
REJECT     0    --  anywhere             192.168.0.10        reject-with icmp-port-unreachable 
ACCEPT     0    --  anywhere             192.168.0.10        state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:8222 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:8333 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:902 
REJECT     0    --  anywhere             192.168.0.1         reject-with icmp-port-unreachable 
ACCEPT     0    --  anywhere             192.168.0.10        state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             192.168.0.10        tcp dpt:ssh 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  192.168.0.10         anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  192.168.0.10         anywhere            udp dpt:domain 
REJECT     0    --  127.0.0.10           anywhere            reject-with icmp-port-unreachable 
REJECT     0    --  192.168.0.10         anywhere            reject-with icmp-port-unreachable 
ACCEPT     0    --  192.168.0.10         anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  192.168.0.10         anywhere            udp dpt:domain 
REJECT     0    --  localhost            anywhere            reject-with icmp-port-unreachable 
REJECT     0    --  192.168.0.10         anywhere            reject-with icmp-port-unreachable 
ACCEPT     0    --  192.168.0.10         anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  192.168.0.10         anywhere            udp dpt:domain 
REJECT     0    --  localhost            anywhere            reject-with icmp-port-unreachable 
REJECT     0    --  192.168.0.10         anywhere            reject-with icmp-port-unreachable 
ACCEPT     0    --  192.168.0.10         anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  192.168.0.10         anywhere            udp dpt:domain 
REJECT     0    --  localhost            anywhere            reject-with icmp-port-unreachable 
REJECT     0    --  192.168.0.10         anywhere            reject-with icmp-port-unreachable 
ACCEPT     0    --  192.168.0.10         anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  192.168.0.10         anywhere            udp dpt:domain 
REJECT     0    --  localhost            anywhere            reject-with icmp-port-unreachable 
REJECT     0    --  192.168.0.10         anywhere            reject-with icmp-port-unreachable 

```


$ ping -c3 yahoo.com```

PING yahoo.com (216.109.112.135) 56(84) bytes of data.
From 192.168.0.10 icmp_seq=1 Destination Port Unreachable
From 192.168.0.10 icmp_seq=1 Destination Port Unreachable
From 192.168.0.10 icmp_seq=1 Destination Port Unreachable

--- yahoo.com ping statistics ---
0 packets transmitted, 0 received, +3 errors

```
Failed.


I have to run following command to stop iptables.

$ sudo iptables -F
No complaint

$ ping -c3 yahoo.com```

PING yahoo.com (216.109.112.135) 56(84) bytes of data.
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=1 ttl=55 time=242 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=2 ttl=54 time=247 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=3 ttl=54 time=246 ms

--- yahoo.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 242.397/245.283/247.256/2.086 ms

```
Internet connection then worked.


Please advise where goes wrong.  TIA


B.R.
satimis

---

