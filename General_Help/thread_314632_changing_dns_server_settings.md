---
title: "changing dns server settings"
date: 2006-12-07
forum: General Help
---

### Post by gwpritch on 2006-12-07
The dns server provided by my isp is impossibly slow. I found alternates and created a new location using these servers in the network settings dialog. I tried deleting the original dns. However, when I reboot, the old dns shows up as default. How do I make the alternate location the start-up default for this connection?
Thanks.

---

### Post by emdeem on 2006-12-07
Tell us more about your setup.  Are you using a router?  I assume you are using DHCP.  Are you getting the IP address from the router or from the ISP?

---

### Post by gwpritch on 2006-12-07
I am using dhcp through a  wired dsl connection at the moment. My wireless router crapped out a while ago. The alternate dns servers are much faster but I can't seem to make them default. Its a PITA manually changing location every time I reboot.

---

### Post by linuchsan on 2006-12-07
in /etc/dhcp3/dhclient.conf, look for prepend domain-name-servers

---

### Post by gwpritch on 2006-12-07
```
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
```

now what?

---

### Post by linuchsan on 2006-12-07
remove the # and:
prepend domain-name-servers ip.dns.server

---

### Post by gwpritch on 2006-12-07
Thanks...that did it. I appreciate your help.

---

