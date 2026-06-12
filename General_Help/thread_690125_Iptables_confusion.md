---
title: "Iptables confusion"
date: 2008-02-07
forum: General Help
---

### Post by SystemParanoia on 2008-02-07
here is my current iptables setup

```
[root@homeserver ~]# iptables -L -v
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
  246 13577 DROP       all  --  any    any     anywhere             anywhere            state INVALID
    0     0 REJECT     tcp  --  any    any     anywhere             anywhere            tcp flags:SYN,ACK/SYN,ACK state NEW reject-with tcp-reset
    3  1146 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN state NEW
    0     0 DROP       all  --  eth0   any     127.0.0.0/8          anywhere
    0     0 DROP       all  --  eth0   any     169.254.0.0/16       anywhere
 1850  407K ACCEPT     all  --  lo     any     anywhere             anywhere
    0     0 ACCEPT     all  --  pptp+  any     anywhere             anywhere
    0     0 ACCEPT     all  --  tun+   any     anywhere             anywhere
 2400  291K ACCEPT     all  --  eth1   any     anywhere             anywhere
   36  1044 ACCEPT     icmp --  eth0   any     anywhere             anywhere            icmp echo-reply
    0     0 ACCEPT     icmp --  eth0   any     anywhere             anywhere            icmp destination-unreachable
  611 18104 ACCEPT     icmp --  eth0   any     anywhere             anywhere            icmp echo-request
    0     0 ACCEPT     icmp --  eth0   any     anywhere             anywhere            icmp time-exceeded
  543  188K ACCEPT     udp  --  eth0   any     anywhere             anywhere            udp spt:bootps dpt:bootpc
    0     0 ACCEPT     tcp  --  eth0   any     anywhere             anywhere            tcp spt:bootps dpt:bootpc
    0     0 ACCEPT     tcp  --  any    any     anywhere             77-101-0-0.cable.ubr05.sand.blueyonder.co.uk tcp dpts:6891:6895
    0     0 ACCEPT     tcp  --  any    any     anywhere             77-101-0-0.cable.ubr05.sand.blueyonder.co.uk tcp dpts:afs3-fileserver:7050
  819 62012 ACCEPT     tcp  --  any    any     anywhere             77-101-0-0.cable.ubr05.sand.blueyonder.co.uk tcp dpt:ssh
 1322  180K ACCEPT     tcp  --  any    any     anywhere             77-101-0-0.cable.ubr05.sand.blueyonder.co.uk tcp dpt:81
   46  2709 ACCEPT     tcp  --  any    any     anywhere             77-101-0-0.cable.ubr05.sand.blueyonder.co.uk tcp dpt:83
    0     0 ACCEPT     tcp  --  any    any     anywhere             77-101-0-0.cable.ubr05.sand.blueyonder.co.uk tcp dpt:1875
  482 54577 ACCEPT     udp  --  eth0   any     anywhere             77-101-0-0.cable.ubr05.sand.blueyonder.co.uk udp dpts:1024:65535 state RELATED,ESTABLISHED
33636   32M ACCEPT     tcp  --  eth0   any     anywhere             77-101-0-0.cable.ubr05.sand.blueyonder.co.uk tcp dpts:1024:65535 state RELATED,ESTABLISHED
 6951  336K DROP       all  --  eth0   any     anywhere             anywhere

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     tcp  --  any    eth1    anywhere             10.0.0.5            tcp dpts:6891:6895
   15   708 ACCEPT     tcp  --  any    eth1    anywhere             10.0.0.5            tcp dpts:afs3-fileserver:7050
    0     0 ACCEPT     tcp  --  any    any     10.0.0.0/24          anywhere            tcp dpts:6891:6895
    0     0 ACCEPT     tcp  --  any    any     10.0.0.0/24          anywhere            tcp dpts:afs3-fileserver:7050
    0     0 ACCEPT     tcp  --  any    any     10.0.0.0/24          anywhere            tcp dpt:squid
    0     0 ACCEPT     tcp  --  any    any     10.0.0.0/24          anywhere            tcp dpt:ssh
   15   600 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED
    0     0 ACCEPT     icmp --  any    any     10.0.0.0/24          anywhere            icmp echo-reply
    0     0 ACCEPT     icmp --  any    any     10.0.0.0/24          anywhere            icmp echo-request
    0     0 ACCEPT     icmp --  any    any     10.0.0.0/24          anywhere            icmp time-exceeded
 3331  301K DROP       all  --  any    any     10.0.0.0/24          anywhere
    0     0 ACCEPT     all  --  pptp+  any     anywhere             anywhere
    0     0 ACCEPT     all  --  tun+   any     anywhere             anywhere
    0     0 DROP       all  --  any    any     anywhere             anywhere

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
 1850  407K ACCEPT     all  --  any    lo      anywhere             anywhere
    0     0 ACCEPT     all  --  any    pptp+   anywhere             anywhere
    0     0 ACCEPT     all  --  any    tun+    anywhere             anywhere
 2160  332K ACCEPT     all  --  any    eth1    anywhere             anywhere
  647 19148 ACCEPT     icmp --  any    eth0    anywhere             anywhere
    0     0 ACCEPT     udp  --  any    eth0    anywhere             anywhere            udp spt:bootpc dpt:bootps
    0     0 ACCEPT     tcp  --  any    eth0    anywhere             anywhere            tcp spt:bootpc dpt:bootps
    0     0 ACCEPT     tcp  --  any    eth0    77-101-0-0.cable.ubr05.sand.blueyonder.co.uk  anywhere            tcp spts:6891:6895
    0     0 ACCEPT     tcp  --  any    eth0    77-101-0-0.cable.ubr05.sand.blueyonder.co.uk  anywhere            tcp spts:afs3-fileserver:7050
  978  451K ACCEPT     tcp  --  any    eth0    77-101--0-0.cable.ubr05.sand.blueyonder.co.uk  anywhere            tcp spt:ssh
 1353  447K ACCEPT     tcp  --  any    eth0    77-101-0-0.cable.ubr05.sand.blueyonder.co.uk  anywhere            tcp spt:81
   51  7230 ACCEPT     tcp  --  any    eth0    77-101-0-0.cable.ubr05.sand.blueyonder.co.uk  anywhere            tcp spt:83
    0     0 ACCEPT     tcp  --  any    eth0    77-101-0-0.cable.ubr05.sand.blueyonder.co.uk  anywhere            tcp spt:1875
23588 1488K ACCEPT     all  --  any    eth0    anywhere             anywhere
    0     0 DROP       all  --  any    eth0    anywhere             anywhere

Chain drop-lan (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DROP       all  --  any    any     anywhere             anywhere

```

my problem is.

im trying to do what should be a simple task...

that is open up the following ports in the firewall

7000-7050
and 6891-6895

and then forward those ports to 10.0.0.5 on the lan.

the computer with the firewall has x2 network cards.

eth0 is directly connected to the wan, and eth1 in connected to the lan with the address 10.0.0.1



can anyone point out what it is im doing wrong?

im scanning my server remotely from another location with nmap, and nomatter what i do, the following ports consistantly remain closed, which means the programs that im trying to run dont work.

i.e msn file transfer.

and pysoulseek.


thanks in advance if anyone can help.

---

