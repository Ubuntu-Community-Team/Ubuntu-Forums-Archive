---
title: "/etc/network/interfaces multple gateways"
date: 2005-05-04
forum: General Help
---

### Post by Spleenie on 2005-05-04
Gday,

Wasnt sure how to implement multiple gateways in the file /etc/network/interfaces, if indeed it is possible

 # The primary network interface
iface eth0 inet static
        address xxx.xxx.xxx.xxx
        netmask 255.255.255.0
        network xxx.xxx.xxx.0
        broadcast xxx.xxx.xxx.255
        gateway xxx.xxx.xxx.xxx <---- IS IT POSSIBLE TO ADD TO THIS???
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers xxx.xxx.xxx.xxx

Cheers, Spleenie

---

### Post by odix on 2005-05-04
Hi there is very good description in the [Debian Reference](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html) , helped me a lot with ubuntu, chapter 10.6 describes the high level network configuration (also used in ubuntu) with examples. But if you describe your problem more deeply, maybe we could help you.

regards odiX

---

### Post by Spleenie on 2005-05-04
Ok, my apologies if I did not make it clear.

I want my computer to see/use the two gateways available to it. in the interfaces file above, there is only one gateway IP, How can I modify this file so that two gateways are registered and understood by eth0

Cheers, Spleenie

---

### Post by odix on 2005-05-09
those gateways, are they default gateways or for different subnets ?

---

### Post by Spleenie on 2005-05-09
[QUOTE=odix]those gateways, are they default gateways or for different subnets ?[/QUOTE]
 Not for different subnets, I just want to have more than one way out to the net

Win XP allows for multiple Gateway listing in its network tcp/ip config.

Cheers, Spleenie

---

