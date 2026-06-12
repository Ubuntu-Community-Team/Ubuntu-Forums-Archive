---
title: "System fails to shutdown after starting firewall rules"
date: 2007-09-28
forum: General Help
---

### Post by satimis on 2007-09-28
Hi folks,


Ubuntu 7.04 server amd64 - Host OS
VMware
one NIC


After adding following script on /etc/rc.local```

#
# INPUT
#

# allow all incoming traffic from the management interface NIC
# as long as it is a part of an established connection
iptables -I INPUT 1 -j ACCEPT -d MGMT_NIC_IP -m state --state
RELATED,ESTABLISHED

# allow all ssh traffic to the management interface NIC
iptables -I INPUT 2 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 22

# allow all VMware MUI HTTP traffic to the management interface NIC
iptables -I INPUT 3 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 8222

# allow all VMware MUI HTTPS traffic to the management interface NIC
iptables -I INPUT 4 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 8333

# allow all VMware Authorization Daemon traffic to the management
interface NIC
iptables -I INPUT 5 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 902

# reject all other traffic to the management interface NIC
iptables -I INPUT 6 -j REJECT -d MGMT_NIC_IP --reject-with
icmp-port-unreachable


#
# OUTPUT
#

# allow all outgoing traffic from the management interface NIC
# if it is a part of an established connection
iptables -I OUTPUT 1 -j ACCEPT -s MGMT_NIC_IP -m state --state
RELATED,ESTABLISHED

# allow all DNS queries from the management interface NIC
iptables -I OUTPUT 2 -j ACCEPT -s MGMT_NIC_IP -p UDP --destination-port 53

# reject all other traffic from localhost
iptables -I OUTPUT 3 -j REJECT -s 127.0.0.1 --reject-with
icmp-port-unreachable

# reject all other traffic from the management interface NIC
iptables -I OUTPUT 4 -j REJECT -s MGMT_NIC_IP --reject-with
icmp-port-unreachable

```
MGMT_NIC-IP = fixed IP address assigned by ISP.

and running;

sudo /etc/init.d/rc.local start
No complaint.

Internet can be connected.


$ sudo iptables -nvL```

Chain INPUT (policy ACCEPT 2652 packets, 2244K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     0    --  *      *       0.0.0.0/0             xxx.xxx.xxx.xxx     state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            xxx.xxx.xxx.xxx     tcp dpt:22 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            xxx.xxx.xxx.xxx     tcp dpt:8222 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            xxx.xxx.xxx.xxx     tcp dpt:8333 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            xxx.xxx.xxx.xxx     tcp dpt:902 
    0     0 REJECT     0    --  *      *       0.0.0.0/0            xxx.xxx.xxx.xxx    reject-with icmp-port-unreachable 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 2355 packets, 393K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     0    --  *      *       xxx.xxx.xxx.xxx      0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       xxx.xxx.xxx.xxx      0.0.0.0/0           udp dpt:53 
    0     0 REJECT     0    --  *      *       127.0.0.1            0.0.0.0/0           reject-with icmp-port-unreachable 
    0     0 REJECT     0    --  *      *       xxx.xxx.xxx.xxx     0.0.0.0/0           reject-with icmp-port-unreachable 

```

But on turning off the PC running;
$ sudo shutdown -h now```

.....
Stopping MySQL database serverice mysqld     [OK]
Shutting donw ALSA    [OK]
Stopping domain name service bind    [OK]

```
It hung here.  I have to turn off the PC manually.  I suspect it is caused by the script.


Any advice?  TIA

B.R.
satimis

---

