---
title: "[SOLVED] icmp requests from 198.168.0.1"
date: 2007-09-06
forum: General Help
---

### Post by nvteighen on 2007-09-06
Ehmm... this is strange, could someone please give me a little lisght on this?

In Firestarter I have noticed that I sometimes recieve ICMP requests from IP 198.168.0.1... Yes, that's my router internal IP! What does that mean? Do routers ping computers or is someone pinging the whole network? Iptables/Firestarter is blocking, but I'm really annoyed.

Thanks!

---

### Post by x64Jimbo on 2007-09-06
That doesn't sound normal, but maybe you have a weird router. Also, is your network wireless? If so, is it secure?

---

### Post by marx2k on 2007-09-06
Maybe your router is pinging the computers to ensure they are still on the router?

---

### Post by nvteighen on 2007-09-07
Yes, it's a wireless. The router is a Thomson TCW710.

But, can routers ping? Or could it be someone else pinging from outside to the router and then, the router to the computer? 

Looking at Firestarter, it occurred again just some minutes ago. Here's the log:
```

Time: Sep  7 12:42:17 Source: 192.168.0.1 Destination: 192.168.0.14 In IF: eth1 Out IF:  Port:  Length: 84 ToS: 0x00 Protocol: ICMP Service: Desconocido

```

("Desconocido" means "Unknown" in Spanish)

Well, my computer is blocking it, but I'm really annoyed.

---

### Post by robert_pectol on 2007-09-07
Probably just an ICMP type 3 (destination unreachable) or similar packet from your router.  You did know that there are other types of ICMP than just ping, right?

---

### Post by nvteighen on 2007-09-07
> **robert_pectol said:**
> Probably just an ICMP type 3 (destination unreachable) or similar packet from your router.  You did know that there are other types of ICMP than just ping, right?

Yes, I knew. I just thought of "ping" because it's the most common. I've googled about ICMP Type 3 and from what I understand they're a message that sends the router to the computer so this readjust itself to match the router's config. Am I right?

---

### Post by robert_pectol on 2007-09-07
No, not really.  In simple terms, it's the router trying to tell you that the destination host is unreachable.  If your host sends a packet destined for another host that doesn't exist, or cannot be reached for whatever reason, your router may send an ICMP type 3 message indicating that the destination host is not reachable.  See the following page for more info:

[http://www.networksorcery.com/enp/protocol/icmp/msg3.htm](http://www.networksorcery.com/enp/protocol/icmp/msg3.htm)

If it is indeed type 3 ICMP that are being blocked by your firewall, you probably don't need to concern yourself too much with those messages, except that I would question why my firewall config is blocking them - which it probably shouldn't be doing.  Usually the affects are minimal to none in most cases but that is legit traffic and probably should be allowed, not blocked.   Anyway, hope that helps a little.

---

### Post by nvteighen on 2007-09-07
> **robert_pectol said:**
> No, not really.  In simple terms, it's the router trying to tell you that the destination host is unreachable.  If your host sends a packet destined for another host that doesn't exist, or cannot be reached for whatever reason, your router may send an ICMP type 3 message indicating that the destination host is not reachable.  See the following page for more info:

[http://www.networksorcery.com/enp/protocol/icmp/msg3.htm](http://www.networksorcery.com/enp/protocol/icmp/msg3.htm)

If it is indeed type 3 ICMP that are being blocked by your firewall, you probably don't need to concern yourself too much with those messages, except that I would question why my firewall config is blocking them - which it probably shouldn't be doing.  Usually the affects are minimal to none in most cases but that is legit traffic and probably should be allowed, not blocked.   Anyway, hope that helps a little.

Well, that's the page I read... And I was who blocked all ICMP in purpose... maybe a little paranoid; but I don't see any problem in connectivity nor anything so I'll leave it that way.

Thank you all! I surely have learnt a bit today.

---

