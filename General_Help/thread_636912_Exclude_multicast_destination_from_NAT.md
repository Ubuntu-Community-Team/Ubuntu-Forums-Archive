---
title: "Exclude multicast destination from NAT"
date: 2007-12-10
forum: General Help
---

### Post by Anonymouslemming on 2007-12-10
Hi all,

I'm trying to configure twonkyvision on my Linux server. This machine also acts as the house firewall and does NAT for all machines inside the house.

If I remove the following lines from my firewall:
$IPT -t nat -A POSTROUTING -s 192.168.10.0/24 -j SNAT --to $EXT_IP
$IPT -A FORWARD -t filter -o eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
then my Xbox 360 can see Twonkyvision on this machine fine. However, with these lines in, it does not work.

What iptables rule do I need to use to say "Do not NAT any connection where the destination IP is NOT 224.0.0.0/4 ? 

I've tried using
$IPT -t nat -A POSTROUTING -s 192.168.10.0/24 -d ! 224.0.0.0/4 -j SNAT --to $EXT_IP
but that still didn't work.

Thanks in advance...

---

