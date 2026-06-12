---
title: "Using SSH between LAN and ADSL"
date: 2008-06-10
forum: General Help
---

### Post by heatblazer on 2008-06-10
Here is my problem. My mom has an ADSL connection with the ADSL modem. I have a LAN with an out ip not local. She is DHCP and I am static ip. So from her pc I can log to mine via the SSH but form mine I cannot enter hers. I saw her IP in the Amule (weird huh). When I type ssh [email]mama@xx.xx.xx.xx[/email] it just displays nothing. No error messages nothing. I`ve waited a lot of time but it does not log. So what must I do to enter my ADSL modem from my other PC???

 Thanx!

---

### Post by heatblazer on 2008-06-10
Probably port 22 is closed. I think that is the ADSL modem port because it gave me that the connection can not be established: port 22: Connection timed out.

---

### Post by issih on 2008-06-10
You probably do need to open the port, if there is a router between the modem and her pc you will need to forward port 22 to her pc, so that incoming connections get sent to her pc rather than any others on the network.

Finally her wan (internet side) ip address is probably assigned to her via dhcp from her ISP, consequently it can change every time she logs on, just because that ip was her's once doesn't mean it will be again. If you really want to do this you will need to set up a dynamic dns service: e.g. 

[http://www.dyndns.com/](http://www.dyndns.com/)

[http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html?gclid=CM662M_i6pMCFREWQgodMnewzA](http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html?gclid=CM662M_i6pMCFREWQgodMnewzA)

These are servers that forward a domain to a dynamically assigned ip by having your mums computer run a daemon that logs in and tells them its currently assigned ip address.

---

### Post by wdaniels on 2008-06-10
> **heatblazer said:**
> Probably port 22 is closed. I think that is the ADSL modem port because it gave me that the connection can not be established: port 22: Connection timed out.

Is there definitely a SSH server listening on your Mom's computer? Are we talking about something like a USB modem or an actual router? It's also possible that the ISP might block that port.

You say you got the IP from Amule, but when was that? Since it's DHCP could it have been reconnected since then and given a different address? You might want to consider setting up [Dynamic DNS]("https://help.ubuntu.com/community/DynamicDNS") on that computer if you're going to be connecting to it remotely.

---

### Post by heatblazer on 2008-06-12
Thank you, guys. I`ll try it ASAP. I am sure there is a way :)

---

### Post by eldragon on 2008-06-12
you could always have her connect to your computer setting a reverse tunnel in order for you to connect to hers through there
from your moms computer:
ssh you@your-ip -R 2222:localhost:22

then in order for you to connect to her computer, just do ssh -p 2222 mama@localhost

thats how ive done it it the past to connect to a friend's computer which is behind a lan we have no access to.

if you dont want her to be inserting passwords, then create a public/private key pair with ssh-keygen at the server (or was it client?)
just google it :D

this would effectively bypass any blocking she might have on her side. she still needs sshd up and running on her computer.

it will also be more secure, having ssh servers open in the wild in non tech-savy users is a security risk. ssh servers get scanned daily for weak passwords. installing fail2ban is recommended.

---

### Post by heatblazer on 2008-06-12
Great suggestion, Eldragon. I`ll try it in Saturday and I`ll report you ASAP. You have a "Thank you" for that.

---

