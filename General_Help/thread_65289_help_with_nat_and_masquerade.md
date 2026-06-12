---
title: "help with nat and masquerade"
date: 2005-09-13
forum: General Help
---

### Post by danielgc on 2005-09-13
I have hoary runing in a  PIII 800EB.  I connect to internet via a USB speedtouch
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html).  IT WORKS FINE

I installed a dhcp server whit the next configuration
--------------------------------------------------------------------------------

 sudo gedit /etc/default/dhcp3-server
INTERFACES="eth0"

sudo gedit /etc/dhcp3/dhcpd.conf
# A slightly different configuration for an internal subnet.
subnet 192.168.1.0 netmask 255.255.255.0 {
 range 192.168.1.100 192.168.1.200;
 option domain-name-servers 202.188.0.133, 202.188.1.5;
 option domain-name "tm.net.my";
 option routers 192.168.1.1;
 option broadcast-address 192.168.1.255;
 default-lease-time 600;
 max-lease-time 7200;
}
--------------------------------------------------------------------------------
AND IT WORKS FINE TOO.

Now, i would like to share internet whit 3 Ms Windows Pcs.

I have read everything about NAT and MASQUERADE.  I tried using the next scrips:
(my inner NIC is eth0 and my outer NIC is ppp0,  ppp0 conects to internet)

--------------------------------------------------------------------------------

#!/bin/bash
# Masquerade out ppp0
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

# Disallow NEW and INVALID incoming or forwarded packets from ppp0.
iptables -A INPUT -i ppp0 -m state --state NEW,INVALID -j DROP
iptables -A FORWARD -i ppp0 -m state --state NEW,INVALID -j DROP

# Turn on IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

--------------------------------------------------------------------------------

#!/bin/bash
LAN_IP_NET=192.168.1.0/24
LAN_NIC=eth0
OUT_NIC=ppp0
iptables -t nat -A POSTROUTING -s $LAN_IP_NET -o $OUT_NIC -j MASQUERADE
iptables -A FORWARD -j ACCEPT -i $LAN_NIC -s $LAN_IP_NET
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

--------------------------------------------------------------------------------

IN BOTH CASES SHARING INTERNET FROM UBUNTU DIDN´T WORK.
WHAT IS WRONG?  

P.D.
THE Ms Windows PCs WORKS FINE WHEN I SHARE INTERNET VIA WINDOWS XP/ISC  AND THEY RECEIVE AUTOMATIC IP ADDRESS WHEN UBUNTU DCHP IS RUNING.

---

### Post by KenLazlo on 2005-09-13
When your Windows PCs try to connect to Internet, they make a new connection. 
So, you have to allow your Windows PCs to do this. 
iptables -A FORWARD -i eth0 -o ppp0 -m state --state NEW -j ACCEPT

Try this

#!/bin/bash

# Turn on IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

# Masquerade out ppp0
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

# Disallow NEW and INVALID incoming or forwarded packets from ppp0.
iptables -A INPUT -i ppp0 -m state --state NEW,INVALID -j DROP

# establishing a new connection to the internet from win pc
iptables -A FORWARD -i eth0 -o ppp0 -m state --state NEW -j ACCEPT

# accept answers 
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

---

### Post by danielgc on 2005-09-13
thanks ken i tried ur scrip but didn work

i thought that this may be my problem.

danielgc@ubuntu:~$ /sbin/route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.17.31.30    *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         172.17.31.30    0.0.0.0         UG    0      0        0 ppp0

am i right?

---

### Post by KenLazlo on 2005-09-16
change last 2 statements to

# establishing a new connection to the internet from win pc
iptables -A FORWARD -i eth0 -o ppp0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

# accept answers
iptables -A FORWARD -i ppp0 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT


for your linux box you need a input and output rule
iptables -A OUTPUT -o ppp0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT     -i ppp0 -m state --state ESTABLISHED,RELATED -j ACCEPT

---

