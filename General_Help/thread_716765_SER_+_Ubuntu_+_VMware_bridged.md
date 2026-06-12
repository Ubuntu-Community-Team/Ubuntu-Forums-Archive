---
title: "SER + Ubuntu + VMware bridged"
date: 2008-03-06
forum: General Help
---

### Post by anothersam on 2008-03-06
Hi,

I am trying to get ser (SIP Express Router) running on a Ubuntu Server 7.10 VMware machine with bridged Ethernet.

So far:
- Downloaded VMware image from thoughtpolice.co.uk
- Ran it and installed vmware tools
- Configured network settings in etc/networking/interfaces
- Used aptitude to update cache and upgrade all packages
- Used aptitude to install Openssh-server and ser

I can ssh into machine, so I know networking is OK
However I cannot get SJPhone to register an alias of 761 with SER.

By running Wireshark on the host machine (winXP), I see repeatadly:

Source         Destination   Protocol  Info
192.168.2.201  192.168.2.10  SIP       Request: REGISTER sip:192.168.2.10
192.168.2.10   192.168.2.201 ICMP      Destination unreachable (Port unreachable)

However, if I run ser -D -E -dddd I get no output during this.

Also I tried serctl alias show, but that responds:

Error opening ser's FIFO /tmp/ser_fifo
Make sure you have line fifo=/tmp/ser_fifo in your config

However I do have that line in /etc/ser/ser.cfg - in fact I haven't changed the defaults.

I have had SER working fine on another ubuntu machine (this one running directly on its host).
So I suspect the problem may be this bridged virtual machine setup.

UPDATE:

After a reboot I got the registration to work, but now I cannot get the calls to work, with the same response ICMP Destination unreachable (Port unreachable)

Requests include:
UDP: Source port: sip Destination port: sip
UDP: Source port: 49152 Destination port: sip
SIP/SDP: Request: INVITE sip:765@192.168.2.10, with session description
SIP: Request: CANCEL sip:765@192.168.2.10

I'm curious the registration succeeded possibly during the bootup. Does ubuntu include a personal firewall or equivalent which is starting later in the boot sequence than ser? Seems unlikely, but I am at the straw clutching stage.

I've checked iptables -L:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

