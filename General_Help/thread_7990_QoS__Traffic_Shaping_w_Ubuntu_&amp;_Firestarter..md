---
title: "QoS / Traffic Shaping w/ Ubuntu &amp; Firestarter."
date: 2004-12-13
forum: General Help
---

### Post by Lukano on 2004-12-13
So I've gotten Firestarter up and running perfectly, NAT is working great and the three clients on my internal network are chugging along.  

But my internet connection is ALSO "chugging along" due to the fact that I had switched from Smoothwall to Ubuntu, and therefor lost all of the HTB based QoS/Traffic Shaping that was in place.  I know I can simply htb.init the classes I had created with the Smoothwall QoS addon - but to be honest it wasn't doing it for me anyways. 

So I'd like to see if anyone had some traffic shaping / QoS scripts - suggestions - idea's.  The things that are most important are;
- Traffic shaping / QoS not only for clients on the LAN but for the Ubuntu box itself.
- Decent if not fantastic shaping/control for Bittorrent traffic.
- GUI control would be nice, but not essential.

I may or may not have picked the appropriate forum for this (using Hoary, but it's really not Hoary specific) so if it needs to be moved no hard feelings.  And I know that I have the option of Shorewall (never been a huge fan) or taking some older scripts / or writing my own from scratch - but I wanted to see what the Ubuntu community had for idea's or scripts to begin with.

 \\:D/

---

### Post by Lukano on 2004-12-13
Also just to get the ball rolling, I'll reply to my own thread with my existing shaping/qos script(s).

This is what I've been using on another machine for a while, and although it works it has a few bugs.  RNETLINK directory does not exist on the first run of "my_shaper" - goes away if run twice, and the fact that I need to run this, clear it and run another script, then run another script (that does really poor QoS/shaping but seems to initialize or clear the path so that if I run my_shaper and my_mangler yet again - they'll finally do shaping/qos and trim my latency back down to ~70ms instead of 300+.  And even then it only keeps it low for a little bit then starts to climb.

So here's my_shaper, my_mangler, and shaper.

my_mangler;
```

#!/bin/sh

# RESET IPTABLES MANGLE RULES
iptables -t mangle -F
iptables -t mangle -X

# SETUP OUTPUT PRIORITY MARKING CHAINS
iptables -t mangle -N MARK-CRITICAL
iptables -t mangle -A MARK-CRITICAL -j MARK --set-mark 20
iptables -t mangle -A MARK-CRITICAL -j TOS --set-tos Minimize-Delay
iptables -t mangle -A MARK-CRITICAL -j ACCEPT

iptables -t mangle -N MARK-REALTIME
iptables -t mangle -A MARK-REALTIME -j MARK --set-mark 21
iptables -t mangle -A MARK-REALTIME -j TOS --set-tos Minimize-Delay
iptables -t mangle -A MARK-REALTIME -j ACCEPT

iptables -t mangle -N MARK-NORMAL
iptables -t mangle -A MARK-NORMAL -j MARK --set-mark 22
iptables -t mangle -A MARK-NORMAL -j TOS --set-tos Normal-Service
iptables -t mangle -A MARK-NORMAL -j ACCEPT

iptables -t mangle -N MARK-LOW
iptables -t mangle -A MARK-LOW -j MARK --set-mark 23
iptables -t mangle -A MARK-LOW -j TOS --set-tos Maximize-Throughput
iptables -t mangle -A MARK-LOW -j ACCEPT

iptables -t mangle -N MARK-VERYLOW
iptables -t mangle -A MARK-VERYLOW -j MARK --set-mark 24
iptables -t mangle -A MARK-VERYLOW -j TOS --set-tos Minimize-Cost
iptables -t mangle -A MARK-VERYLOW -j ACCEPT

# LET INCOMING DATA PASS THROUGH
iptables -t mangle -A FORWARD -d 192.168.0.1/255.255.0.0 -j ACCEPT

# SET UP TRAFFIC PRIORITIES
# ICMP
iptables -t mangle -A FORWARD -p icmp -j MARK-CRITICAL
# Games
iptables -t mangle -A FORWARD -p udp --sport 1716 -j MARK-REALTIME
iptables -t mangle -A FORWARD -p udp --sport 1717 -j MARK-REALTIME
# Standard Services
iptables -t mangle -A FORWARD -p tcp --sport telnet -j MARK-REALTIME
iptables -t mangle -A FORWARD -p tcp --dport telnet -j MARK-REALTIME
iptables -t mangle -A FORWARD -p tcp --sport ssh -j MARK-REALTIME
iptables -t mangle -A FORWARD -p tcp --dport ssh -j MARK-REALTIME
iptables -t mangle -A FORWARD -p tcp --sport smtp -j MARK-LOW
iptables -t mangle -A FORWARD -p tcp --sport http -j MARK-LOW
# Remote Connections
iptables -t mangle -A FORWARD -p tcp --sport 5800:6000 -j MARK-REALTIME
iptables -t mangle -A FORWARD -p tcp --dport 5800:6000 -j MARK-REALTIME
# Ahhh, FTP... for both active and passive, the client connects to the
# server via destination port 21 (ftp).  We'll make this realtime priority,
# since this is the control channel and we don't want big delays if the user
# is typing in the commands manually.  We need to be explicit because all FTP
# traffic from our server is marked with "Maximize-Throughput" so this would
# otherwise be set to low priority (see below).
iptables -t mangle -A FORWARD -p tcp --sport ftp -j MARK-REALTIME
iptables -t mangle -A FORWARD -p tcp --dport ftp -j MARK-REALTIME
# This is where FTP gets strange.  For the original "active" FTP, the
# server then connects back to the client from source port 20 (ftp-data)...
# We'll make this low priority if we are the server, otherwise it'll just
# default to normal priority.  For "passive" FTP, the server tells the client
# to connect to some random port (and from a random port), so we basically
# have no idea what port it could be.  We could limit the available ports
# somewhat at the FTP server (this is configurable), but we couldn't guarantee
# that some other connection would not accidentally be considered to be FTP
# traffic.  So, we'll deal with this by having the computer that is acting
# as the FTP server mangle its FTP packets with the TOS bits indicating
# "Maximize-Throughput", which we'll translate to LOW priority later.
iptables -t mangle -A FORWARD -p tcp --sport ftp-data -j MARK-LOW
# BitTorrent
iptables -t mangle -A FORWARD -p udp --dport 6881:6889 -j MARK-VERYLOW
iptables -t mangle -A FORWARD -p udp --sport 6881:6889 -j MARK-VERYLOW
iptables -t mangle -A FORWARD -p tcp --dport 6881:6889 -j MARK-VERYLOW
iptables -t mangle -A FORWARD -p tcp --sport 6881:6889 -j MARK-VERYLOW
# FreeNet: the only port we know is our server port, but FreeNet initiates
# connections from all sorts of random ports.  Therefore we'll have the
# computer that it is running on set the TOS bits to "Minimize-Cost" and we'll
# set the priority based on that.
iptables -t mangle -A FORWARD -p tcp --sport 17601 -j MARK-VERYLOW
iptables -t mangle -A FORWARD -p tcp --dport 17601 -j MARK-VERYLOW
# TOS based: in some cases (see above) we make decisions based on the TOS bits
# that are set at the machines sending the traffic.
iptables -t mangle -A FORWARD -m tos --tos Maximize-Throughput -j MARK-LOW
iptables -t mangle -A FORWARD -m tos --tos Minimize-Cost -j MARK-VERYLOW
# Everything else...
iptables -t mangle -A FORWARD -j MARK-NORMAL

```

my_shaper
```

#!/bin/sh

# RESET QUEUES
tc qdisc del dev eth0 root
tc qdisc del dev eth0 ingress

# default is 100
ip link set dev eth0 qlen 30
# default is 1100
ip link set dev eth0 mtu 1100
# create HTB root qdisc
tc qdisc add dev eth0 root handle 1: htb default 22
# create classe
tc class add dev eth0 parent 1: classid 1:1 htb rate 691kbit
# create leaf classes
tc class add dev eth0 parent 1:1 classid 1:20 htb rate 200kbit ceil 691kbit prio 0
tc class add dev eth0 parent 1:1 classid 1:21 htb rate 200kbit ceil 691kbit prio 1
tc class add dev eth0 parent 1:1 classid 1:22 htb rate 30kbit ceil 691kbit prio 2
tc class add dev eth0 parent 1:1 classid 1:23 htb rate 30kbit ceil 691kbit prio 3
tc class add dev eth0 parent 1:1 classid 1:24 htb rate 20kbit ceil 691kbit prio 4
# attach qdisk to leaf classes - using SFQ for fairness
tc qdisc add dev eth0 parent 1:20 handle 20: sfq perturb 10
tc qdisc add dev eth0 parent 1:21 handle 21: sfq perturb 10
tc qdisc add dev eth0 parent 1:22 handle 22: sfq perturb 10
tc qdisc add dev eth0 parent 1:23 handle 23: sfq perturb 10
tc qdisc add dev eth0 parent 1:24 handle 24: sfq perturb 10
# create filters to determine to which queue each packet goes
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 20 fw flowid 1:20
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 21 fw flowid 1:21
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 22 fw flowid 1:22
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 23 fw flowid 1:23
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 24 fw flowid 1:24

# police ingress
tc qdisc add dev eth0 handle ffff: ingress

# filter everything to it, drop whatever is coming to fast
tc filter add dev eth0 parent ffff: protocol ip prio 50 u32 match ip src 0.0.0.0/0 police rate 5500kbit burst 10k drop flowid :1

```

shaper
```

#!/bin/bash

#
#  Outbound rate limiting stuff
#
#  modified & hacked from:
#  http://www.tldp.org/HOWTO/ADSL-Bandwidth-Management-HOWTO/implementation.html


RATEUP=691
DEV=eth0

#
# End Configuration Options
#

if [ "$1" = "status" ]
then
        echo "[qdisc]"
        tc -s qdisc show dev $DEV
        echo "[class]"
        tc -s class show dev $DEV
        echo "[filter]"
        tc -s filter show dev $DEV
        echo "[iptables]"
        iptables -t mangle -L MYSHAPER-OUT -v -x 2> /dev/null
        exit
fi

# Reset everything to a known state (cleared)
tc qdisc del dev $DEV root    2> /dev/null > /dev/null
iptables -t mangle -D POSTROUTING -o $DEV -j MYSHAPER-OUT 2> /dev/null > /dev/null
iptables -t mangle -F
iptables -t mangle -X

if [ "$1" = "stop" ]
then
        echo "Shaping removed on $DEV."
        exit
fi

###########################################################
#
# Outbound Shaping (limits total bandwidth to RATEUP)

# set queue size to give latency of about 2 seconds on low-prio packets
ip link set dev $DEV qlen 2

# changes mtu on the outbound device.  Lowering the mtu will result
# in lower latency but will also cause slightly lower throughput due
# to IP and TCP protocol overhead.
ip link set dev $DEV mtu 1452

# add HTB root qdisc
tc qdisc add dev $DEV root handle 1: htb default 26

# add main rate limit classes
tc class add dev $DEV parent 1: classid 1:1 htb rate ${RATEUP}kbit

# add leaf classes - We grant each class at LEAST it's "fair share" of bandwidth.
#                    this way no class will ever be starved by another class.  Each
#                    class is also permitted to consume all of the available bandwidth
#                    if no other classes are in use.
tc class add dev $DEV parent 1:1 classid 1:20 htb rate $[$RATEUP/7]kbit ceil ${RATEUP}kbit prio 0
tc class add dev $DEV parent 1:1 classid 1:21 htb rate $[$RATEUP/7]kbit ceil ${RATEUP}kbit prio 1
tc class add dev $DEV parent 1:1 classid 1:22 htb rate $[$RATEUP/7]kbit ceil ${RATEUP}kbit prio 2
tc class add dev $DEV parent 1:1 classid 1:23 htb rate $[$RATEUP/7]kbit ceil ${RATEUP}kbit prio 3
tc class add dev $DEV parent 1:1 classid 1:24 htb rate $[$RATEUP/7]kbit ceil ${RATEUP}kbit prio 4
tc class add dev $DEV parent 1:1 classid 1:25 htb rate $[$RATEUP/7]kbit ceil ${RATEUP}kbit prio 5
tc class add dev $DEV parent 1:1 classid 1:26 htb rate 10kbit ceil 100kbit prio 6

# attach qdisc to leaf classes - here we at SFQ to each priority class.  SFQ insures that
#                                within each class connections will be treated (almost) fairly.
tc qdisc add dev $DEV parent 1:20 handle 20: sfq perturb 10
tc qdisc add dev $DEV parent 1:21 handle 21: sfq perturb 10
tc qdisc add dev $DEV parent 1:22 handle 22: sfq perturb 10
tc qdisc add dev $DEV parent 1:23 handle 23: sfq perturb 10
tc qdisc add dev $DEV parent 1:24 handle 24: sfq perturb 10
tc qdisc add dev $DEV parent 1:25 handle 25: sfq perturb 10
tc qdisc add dev $DEV parent 1:26 handle 26: sfq perturb 10

# filter traffic into classes by fwmark - here we direct traffic into priority class according to
#                                         the fwmark set on the packet (we set fwmark with iptables
#                                         later).  Note that above we've set the default priority
#                                         class to 1:26 so unmarked packets (or packets marked with
#                                         unfamiliar IDs) will be defaulted to the lowest priority
#                                         class.
tc filter add dev $DEV parent 1:0 prio 0 protocol ip handle 20 fw flowid 1:20
tc filter add dev $DEV parent 1:0 prio 0 protocol ip handle 21 fw flowid 1:21
tc filter add dev $DEV parent 1:0 prio 0 protocol ip handle 22 fw flowid 1:22
tc filter add dev $DEV parent 1:0 prio 0 protocol ip handle 23 fw flowid 1:23
tc filter add dev $DEV parent 1:0 prio 0 protocol ip handle 24 fw flowid 1:24
tc filter add dev $DEV parent 1:0 prio 0 protocol ip handle 25 fw flowid 1:25
tc filter add dev $DEV parent 1:0 prio 0 protocol ip handle 26 fw flowid 1:26

# add MYSHAPER-OUT chain to the mangle table in iptables - this sets up the table we'll use
#                                                      to filter and mark packets.
iptables -t mangle -N MYSHAPER-OUT
iptables -t mangle -I POSTROUTING -o $DEV -j MYSHAPER-OUT

# add fwmark entries to classify different types of traffic - Set fwmark from 20-26 according to
#                                                             desired class. 20 is highest prio.
iptables -t mangle -A MYSHAPER-OUT -p tcp --sport 0:1024 -j MARK --set-mark 23 # Default for low port traffic
iptables -t mangle -A MYSHAPER-OUT -p tcp --dport 0:1024 -j MARK --set-mark 23 # ""
iptables -t mangle -A MYSHAPER-OUT -p tcp --dport 20 -j MARK --set-mark 26     # ftp-data port, low prio
iptables -t mangle -A MYSHAPER-OUT -p tcp --dport 25 -j MARK --set-mark 25     # ftp-data port, low prio
iptables -t mangle -A MYSHAPER-OUT -p tcp --dport 5190 -j MARK --set-mark 23   # aol instant messenger
iptables -t mangle -A MYSHAPER-OUT -p icmp -j MARK --set-mark 26               # ICMP (ping) - high prio, impress friends
iptables -t mangle -A MYSHAPER-OUT -p udp -j MARK --set-mark 20                # DNS name resolution (small packets)
iptables -t mangle -A MYSHAPER-OUT -p tcp --dport ssh -j MARK --set-mark 22    # secure shell
iptables -t mangle -A MYSHAPER-OUT -p tcp --sport ssh -j MARK --set-mark 22    # secure shell
iptables -t mangle -A MYSHAPER-OUT -p tcp --sport 80:81 -j MARK --set-mark 25   # Local web server
iptables -t mangle -A MYSHAPER-OUT -p tcp -m length --length :64 -j MARK --set-mark 21 # small packets (probably just ACKs)

iptables -t mangle -A MYSHAPER-OUT -p udp -j MARK --set-mark 22  # Battlefield Vietnam
iptables -t mangle -A MYSHAPER-OUT -p tcp --dport 6881:7000 -j MARK --set-mark 26  # Torrents - ultra low.
iptables -t mangle -A MYSHAPER-OUT -p tcp --sport 6881:7000 -j MARK --set-mark 26  # Torrents - ultra low.

iptables -t mangle -A MYSHAPER-OUT -m mark --mark 0 -j MARK --set-mark 26


echo "Outbound shaping added to $DEV.  Rate: ${RATEUP}Kbit/sec."

```

---

### Post by tvlad on 2005-01-14
Hi, i was looking at your shaper script and i've a few questions since i've just started looking at traffic shaping. After you create the htb class, and add the htb leafs, why add to those leafs sfq qdiscs, from what i've read you do that to prioritize between leafs, but couldn't you use the prio option from htb ?

Could you shed some light on tc filter, i don't really know what id does.

tc qdisc del dev eth0 root
tc qdisc del dev eth0 ingress

tc qdisc add dev eth2 parent root handle 1:0 htb default 20
tc class add dev eth0 parent 1:0 classid 1:1 htb rate 256kbit
 
tc class add dev eth0 parent 1:1 classid 1:10 htb rate 24kbit ceil 256Kbit
tc class add dev eth0 parent 1:1 classid 1:20 htb rate 24kbit ceil 256Kbit
tc class add dev eth0 parent 1:1 classid 1:30 htb rate 24kbit ceil 256Kbit
tc class add dev eth0 parent 1:1 classid 1:40 htb rate 96kbit ceil 256Kbit prio 0
tc class add dev eth0 parent 1:1 classid 1:50 htb rate 96kbit ceil 256Kbit prio 1

What would happen if for the prio 0 leaf i'd add 196kbit as the rate, would that mean that if the total bandwitdth isn't higher than 256kbit, it will take all that it can from the other leafs even if they have a min guaranteed rate ?

---

### Post by tvlad on 2005-01-15
I was wondering, shouldn't this topic be moved to the server section ? i think it would be a better place for it.

---

