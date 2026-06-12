---
title: "How can I disable ping &amp; icmp requests?"
date: 2013-08-02
forum: General Help
---

### Post by koda2 on 2013-08-02
Does anybody know how can I disable ping & icmp requests? like, if somebody is PINGing my IP-Address, he/she should see nothing, but I SHOULD be able to ping websites/IPs though.  Any idea how can I do this? perhaps via gufw, or ufw..or any other similiar method?  If yes, please give me the exact command to disable ping & icmp requests.

---

### Post by GwL3eNC on 2013-08-02
Hi,

the only way i know to do this is iptables. 
I accept some things you have to set there DENY. i made that on my own and i am not pro. therefore
you have to think about it on your own.

set $fw=iptables in your script

$fw -A FORWARD -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT
$fw -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT

$fw -A INPUT -p icmp --icmp-type destination-unreachable -j ACCEPT
$fw -A INPUT -p icmp --icmp-type time-exceeded -j ACCEPT
$fw -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT

$fw -A OUTPUT  -p icmp --icmp-type destination-unreachable -j ACCEPT
$fw -A OUTPUT  -p icmp --icmp-type time-exceeded -j ACCEPT
$fw -A OUTPUT  -p icmp --icmp-type echo-reply -j ACCEPT
$fw -A OUTPUT  -p icmp --icmp-type echo-request -j ACCEPT

---

