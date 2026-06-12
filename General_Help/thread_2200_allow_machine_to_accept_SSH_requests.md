---
title: "allow machine to accept SSH requests?"
date: 2004-10-26
forum: General Help
---

### Post by sfw5000 on 2004-10-26
Hi,

I'm a little confused about how to allow a machine to accept SSH requests. I set up a machine for a friend and want to log in, installed ssh and sshd on his machine and am running it, but the ports don't seem to be open. I haven't made any changes to iptables, but it looks like the default configuration is to allow requests through. Can someone tell me how to enable this?

Thanks,

Sam

---

### Post by Kopf on 2004-10-26
Are you trying to do this over the Internet or on a LAN?

Kopf

---

### Post by sfw5000 on 2004-10-26
Over the internet. His machine is hooked up directly to a DSL modem (no router) and I set him up with ddclient and a dyndns.org domain name. That part is working fine, but I get a time out when I try to log in.

---

### Post by Kopf on 2004-10-26
Try connecting using his IP address instead of the DNS name.  If that still doesn't work I would guess there is a firewall or routing component in the DSL modem and you may need to open and forward port 22.

Kopf

---

### Post by sfw5000 on 2004-10-26
OK, yeah I already tried going straight to the IP. Of course, I didn't think of that. I haven't actually been to his place, but there might be some kind of router built into his modem. Although I can see through dyndns.org that his IP address is not using DHCP -- it's not like it's 192.198.1.1 -- it should be accessible. But there still might be a firewall of somesort in the modem.

Am I right in saying that by default, Ubuntu should allow it through if there's no external router/firewall configuration to block it?

EDIT: Thank you!

---

### Post by flygmaskin on 2004-10-26
[QUOTE=sfw5000]OK, yeah I already tried going straight to the IP. Of course, I didn't think of that. I haven't actually been to his place, but there might be some kind of router built into his modem. Although I can see through dyndns.org that his IP address is not using DHCP -- it's not like it's 192.198.1.1 -- it should be accessible. But there still might be a firewall of somesort in the modem.

Am I right in saying that by default, Ubuntu should allow it through if there's no external router/firewall configuration to block it?[/QUOTE]
 Ubuntu doesnt install sshd by default. apt-get install ssh

---

### Post by sfw5000 on 2004-10-26
Right -- I installed SSH, I'm just confirming that the default firewall config in Ubuntu should not block SSH requests.

---

### Post by Kopf on 2004-10-26
Ununtu should allow it through by default yes.

How does the DSL modem connect to his computer?

Have him run ifconfig and see what it brings up.  If it is something like 192.168.0.1 then the DSL moden is acting as a NAT router and you will have to open ports and forward it.

Kopf

---

### Post by sfw5000 on 2004-10-26
Yeah we did the ifconfig -- it's not a 192 address -- it's something like 171.231.45.34 (that's not it exactly, of course), but it should work, no? unless the dsl modem is blocking ports even though it's not using NAT.

---

### Post by Kopf on 2004-10-26
What is the DNS or IP address if you don't mind me knowing?  (you can email me if you want)

It looks like it should work unless the DSL modem is blocking it.  Was the IP address 171.x.x.x or 172.x.x.x thats important.

Kopf

---

### Post by HungSquirrel on 2004-10-26
I believe 172.x.x.x addresses are local ones similar to 192.x.x.x addresses.  In this case I think your friend is out of luck because AFAIK dyndns can't work with them.

---

### Post by sfw5000 on 2004-10-26
Ahh.... ignorant me. The IP is  172.16.1.13 -- I was just checking to make sure it wasn't 192.xxx.xxx.xxx, I didn't realize that 172.xxx.xxx.xxx would also be local -- so, yeah, that means the modem is acting as a router and we would need to log in there and enable port forwarding to his machine and open port 22.

---

### Post by Kopf on 2004-10-26
Aye glad we figured it out. Let me know if you need anything else.

Kopf

---

