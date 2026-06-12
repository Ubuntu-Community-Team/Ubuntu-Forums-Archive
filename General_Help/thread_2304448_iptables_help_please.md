---
title: "iptables help please"
date: 2015-11-26
forum: General Help
---

### Post by davaweb on 2015-11-26
Hi,
14.04.2

I'm trying to get this to run in a bash script but nothing happens.

It is from a Debian script here:
[http://forums.debian.net/viewtopic.php?f=10&t=108381&sid=8d991c050e8bc7053df2cfff144c7e77#p517286](http://forums.debian.net/viewtopic.php?f=10&t=108381&sid=8d991c050e8bc7053df2cfff144c7e77#p517286)

```
#!/bin/sh
/sbin/iptables -P INPUT DROP
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A INPUT -i eth0 -s 192.168.1.0/24 -j ACCEPT
/sbin/iptables -A OUTPUT -o eth0 -d 192.168.1.0/24 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A OUTPUT -p udp --sport 67 -j ACCEPT
/bin/grep -h '^remote ' /etc/openvpn/*.ovpn | /usr/bin/cut -d ' ' -f 2 | /usr/bin/sort -du | /usr/bin/xargs -I @ /sbin/iptables -A OUTPUT -d @ -j ACCEPT
/sbin/iptables -A OUTPUT -o eth0 -j REJECT
```

I have put my ovpn and crt scripts in /etc/ovpn

This is my first attempt to use iptables so my level of knowledge on it is low.

Any help is appreciated - thank you.

---

### Post by matt_symes on 2015-11-26
Hi

> **davaweb said:**
> 

```

...
/bin/grep -h '^remote ' /etc/openvpn/*.ovpn ...
...
```

I have put my ovpn and crt scripts in /etc/ovpn


It's grepping files in /etc/openvpn and you have your files in  /etc/ovpn ?

When you say nothing is happening, what exactly do you mean by that ? What is not happening that you were expecting to happen ?

Do you understand what those IP tables rules are doing ? Can you read them ?

Kind regards

---

