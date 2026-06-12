---
title: "Network performance issues"
date: 2007-03-07
forum: General Help
---

### Post by DiGiTY on 2007-03-07
I'm backiing up my 6.06 box and I notice when I copy files from the machine over SMB and download a file from it's web server simultaneously (all within my home network), the transfer speeds dramatically drop (namely the web download, goes from 400+ kb/s to about 7 kb/s)... is this normal???

TIA

P.S. - 933 MHz PIII, 512 MB, built-in Intel 10/100 MB NIC

---

### Post by bryan.taylor on 2007-03-07
What speed is the SMB transfer going at when the web transfer drops?  Also, how fast does the SMB transfer run without the web transfer going?

---

### Post by DiGiTY on 2007-03-07
i'm not sure... i'm assuming 8-9 Mb/s, the norm for my 100 mbit home network, but it's transfering 9,000 small size files which is hard to get a read on

it appears the network transfer is taking the majority of the bandwidth no matter what

my concern here is whether or not this is the norm because i'm backing to box up to install Ubuntu 6.10 and run a file, media, backup, nas, web dev server and speed is obviously an issue (i'd hate for my gf to get playback stutters on the HTPC because I'm transfering files or updating a web site).

---

### Post by bryan.taylor on 2007-03-07
Assuming that you're still using your full bandwidth, but that it's just partitioned poorly, you might want to look at running some traffic shaping on the server box.  It's really not that hard to do.  It took me two hours to research and implement some basic traffic shaping for our home network.

My usage scenario is this:  We are constantly consuming all of our available upload bandwidth and we need to have web browsing, ssh, etc. be responsive.  The following works like a charm.

Here are the resources I used:
[http://lartc.org/howto/lartc.cookbook.fullnat.intro.html](http://lartc.org/howto/lartc.cookbook.fullnat.intro.html)
[http://gentoo-wiki.com/HOWTO_Packet_Shaping](http://gentoo-wiki.com/HOWTO_Packet_Shaping)

To hopefully make it a bit easier for you, here are my configuration scripts:

I added this script to run at boot time in the local init script:
```
#!/bin/bash
#
# initialize the traffic control (tc) rules
#

#
# rates calculated by classnum^ln(${CEIL}/8kbit)/ln(${NUMCLASSES})
# where classnum begins at 1 and 1 is the lowest priority class
#
CEIL=376
# default bucket is 13
tc qdisc add dev ppp0 root handle 1: htb default 13
# root class
tc class add dev ppp0 parent 1: classid 1:1 htb rate ${CEIL}kbit ceil ${CEIL}kbit
# subclasses
tc class add dev ppp0 parent 1:1 classid 1:10 htb rate 184kbit ceil ${CEIL}kbit prio 0
tc class add dev ppp0 parent 1:1 classid 1:11 htb rate 96kbit ceil ${CEIL}kbit prio 1
tc class add dev ppp0 parent 1:1 classid 1:12 htb rate 48kbit ceil ${CEIL}kbit prio 2
# mass data transfer bucket
tc class add dev ppp0 parent 1:1 classid 1:13 htb rate 12kbit ceil ${CEIL}kbit prio 3
# bittorrent buckets; there should be one bucket per machine
tc class add dev ppp0 parent 1:1 classid 1:14 htb rate 12kbit ceil ${CEIL}kbit prio 4
tc class add dev ppp0 parent 1:1 classid 1:15 htb rate 12kbit ceil ${CEIL}kbit prio 4
tc class add dev ppp0 parent 1:1 classid 1:16 htb rate 12kbit ceil ${CEIL}kbit prio 4

# set up sfq qdiscs in each class
tc qdisc add dev ppp0 parent 1:10 handle 100: sfq perturb 10
tc qdisc add dev ppp0 parent 1:11 handle 110: sfq perturb 10
tc qdisc add dev ppp0 parent 1:12 handle 120: sfq perturb 10
tc qdisc add dev ppp0 parent 1:13 handle 130: sfq perturb 10
tc qdisc add dev ppp0 parent 1:14 handle 140: sfq perturb 10
tc qdisc add dev ppp0 parent 1:15 handle 150: sfq perturb 10
tc qdisc add dev ppp0 parent 1:16 handle 160: sfq perturb 10

#
# assign marked packets to their appropriate buckets
#
tc filter add dev ppp0 parent 1:0 protocol ip prio 1 handle 1 fw classid 1:10
tc filter add dev ppp0 parent 1:0 protocol ip prio 2 handle 2 fw classid 1:11
tc filter add dev ppp0 parent 1:0 protocol ip prio 3 handle 3 fw classid 1:12
tc filter add dev ppp0 parent 1:0 protocol ip prio 4 handle 4 fw classid 1:13
tc filter add dev ppp0 parent 1:0 protocol ip prio 5 handle 5 fw classid 1:14
tc filter add dev ppp0 parent 1:0 protocol ip prio 5 handle 6 fw classid 1:15
tc filter add dev ppp0 parent 1:0 protocol ip prio 5 handle 7 fw classid 1:16

```

This script adds the iptables rules that mark the packets so that they are handled by the appropriate buckets added above:
```
#!/bin/bash

iptables -t mangle -A FORWARD -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN -j MARK --set-mark 0x1
iptables -t mangle -A FORWARD -p tcp -m tcp --tcp-flags SYN,RST,ACK SYN -j RETURN

# icmp
iptables -t mangle -A FORWARD -p icmp -j MARK --set-mark 0x1
iptables -t mangle -A FORWARD -p icmp -j RETURN

# ssh
iptables -t mangle -A FORWARD -p tcp -m tcp --dport 22 -j MARK --set-mark 0x2
iptables -t mangle -A FORWARD -p tcp -m tcp --dport 22 -j RETURN
# telnet
iptables -t mangle -A FORWARD -p tcp -m tcp --dport 23 -j MARK --set-mark 0x2
iptables -t mangle -A FORWARD -p tcp -m tcp --dport 23 -j RETURN
# http
iptables -t mangle -A FORWARD -p tcp --dport 80 -j MARK --set-mark 0x2
iptables -t mangle -A FORWARD -p tcp --dport 80 -j RETURN
# https
iptables -t mangle -A FORWARD -p tcp --dport 443 -j MARK --set-mark 0x2
iptables -t mangle -A FORWARD -p tcp --dport 443 -j RETURN
# smtp
iptables -t mangle -A FORWARD -p tcp --dport 25 -j MARK --set-mark 0x3
iptables -t mangle -A FORWARD -p tcp --dport 25 -j RETURN
# pop3
iptables -t mangle -A FORWARD -p tcp --dport 110 -j MARK --set-mark 0x3
iptables -t mangle -A FORWARD -p tcp --dport 110 -j RETURN

# packet info
iptables -t mangle -A FORWARD -m tos --tos Minimize-Delay -j MARK --set-mark 0x1
iptables -t mangle -A FORWARD -m tos --tos Minimize-Delay -j RETURN
iptables -t mangle -A FORWARD -m tos --tos Minimize-Cost -j MARK --set-mark 0x3
iptables -t mangle -A FORWARD -m tos --tos Minimize-Cost -j RETURN
iptables -t mangle -A FORWARD -m tos --tos Maximize-Throughput -j MARK --set-mark 0x2
iptables -t mangle -A FORWARD -m tos --tos Maximize-Throughput -j RETURN

# deprecated in favor of the machine specific large upload buckets below; this rule is
# implied (because the default of 3 or 4 takes precedence over 5 and below) where it
# used to have to be stated explicitly
# dad's activities take precedence
#	iptables -t mangle -A FORWARD -i eth0 -s jim-laptop -j MARK --set-mark 0x2
#	iptables -t mangle -A FORWARD -i eth0 -s jim-laptop -j RETURN

#
# the machine specific upload sections to follow are set up so that upload bandwidth
# should be shared equally regardless of number of connections; e.g. fair bittorrent
#
# bryan's large uploads
iptables -t mangle -A FORWARD -i eth0 -s bryan-desktop -p tcp -m length --length 1024: -j MARK --set-mark 0x5
iptables -t mangle -A FORWARD -i eth0 -s bryan-desktop -p tcp -m length --length 1024: -j RETURN
iptables -t mangle -A FORWARD -i eth0 -s bryan-desktop -p udp -m length --length 1024: -j MARK --set-mark 0x5
iptables -t mangle -A FORWARD -i eth0 -s bryan-desktop -p udp -m length --length 1024: -j RETURN
# paul's large uploads
iptables -t mangle -A FORWARD -i eth0 -s paul-laptop -p tcp -m length --length 1024: -j MARK --set-mark 0x6
iptables -t mangle -A FORWARD -i eth0 -s paul-laptop -p tcp -m length --length 1024: -j RETURN
iptables -t mangle -A FORWARD -i eth0 -s paul-laptop -p udp -m length --length 1024: -j MARK --set-mark 0x6
iptables -t mangle -A FORWARD -i eth0 -s paul-laptop -p udp -m length --length 1024: -j RETURN
# steven's large uploads
iptables -t mangle -A FORWARD -i eth0 -s steven-desktop -p tcp -m length --length 1024: -j MARK --set-mark 0x7
iptables -t mangle -A FORWARD -i eth0 -s steven-desktop -p tcp -m length --length 1024: -j RETURN
iptables -t mangle -A FORWARD -i eth0 -s steven-desktop -p udp -m length --length 1024: -j MARK --set-mark 0x7
iptables -t mangle -A FORWARD -i eth0 -s steven-desktop -p udp -m length --length 1024: -j RETURN

# assume large packet size equals bandwidth-eating upload (mass data transfer)
iptables -t mangle -A FORWARD -p tcp -m length --length 1024: -j MARK --set-mark 0x4
iptables -t mangle -A FORWARD -p tcp -m length --length 1024: -j RETURN
iptables -t mangle -A FORWARD -p udp -m length --length 1024: -j MARK --set-mark 0x4
iptables -t mangle -A FORWARD -p udp -m length --length 1024: -j RETURN

# catch-all for everything not tcp and not handled above
iptables -t mangle -A FORWARD -p ! tcp -j MARK --set-mark 0x1
iptables -t mangle -A FORWARD -p ! tcp -j RETURN

# by default everyone else gets one class higher than mass data transfer 
iptables -t mangle -A FORWARD -j MARK --set-mark 0x3
```

The first script needs to be run every time the computer boots.  The second script needs to be run once and then handled by whatever saves and restores iptables rules on boot.

Your scripts will probably be slightly different.  You'll also most likely be adding the rules to the OUTPUT chain of the mangle table (if the packets originate from the box itself).

I hope that helps :)

---

### Post by DiGiTY on 2007-03-09
thanx, but I don't think that's what I need or want. the less customizing and modding I have to do, the better.

what about simply adding another NIC and having all traffic split between them or binding servers to one of the NICs/IP addresses???

Or what about upgrading my network to 1 gigabit?

---

### Post by bryan.taylor on 2007-03-09
I suppose that you could add an additional NIC, but I think that could become more complicated than a traffic shaping approach as your needs grow.

If you'd like a gui then I'm sure that some exist.  A quick google search pointed me to [http://www.ipcop.org/](http://www.ipcop.org/), but I've never tried it.

---

### Post by DiGiTY on 2007-03-10
thanx bryan

---

