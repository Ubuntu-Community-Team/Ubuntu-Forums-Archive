---
title: "resolv.conf modification?"
date: 2008-07-07
forum: General Help
---

### Post by blackhatbrigade on 2008-07-07
What controls the nameservers that show up in /etc/resolv.conf?  With a DHCP client that is.  Does that setting get pulled from the LAN or is that something that the Local Host controls with DHCP?

Gotta figure out what needs work, my router or my computer

---

### Post by dentaku65 on 2008-07-07
> **blackhatbrigade said:**
> What controls the nameservers that show up in /etc/resolv.conf?  With a DHCP client that is.  Does that setting get pulled from the LAN or is that something that the Local Host controls with DHCP?

Gotta figure out what needs work, my router or my computer

They are not managed by resolv.conf, but by dhclient.conf; so edit the file:
```
sudo nano /etc/dhcp3/dhclient.conf
```
change this line:
```
#prepend domain-name-servers 127.0.0.1;
```
to
```
prepend domain-name-servers a.a.a.a,b.b.b.b,c.c.c.c;
```
where a,b and c are the ip addresses of your DNS servers
Then do:
```
sudo /etc/init.d/networking restart
```
or reboot the machine

---

### Post by blackhatbrigade on 2008-07-07
Should I assume that because that line is commented out that it currently gets the DNS server list from the router/DHCP Server?

The reason I ask is because I'd rather just figure out the problem there so I don't have to do this to every machine on my network (or every machine that will be a part of network).

---

### Post by Car60n on 2008-07-07
resolv.conf gets the list of its nameservers from network manager
and the network manager is responsible for modifying resolv.conf...
don't know the part bout dhcp...

---

### Post by blackhatbrigade on 2008-07-07
I've changed the DNS servers through the Network Manager before (I assume you're talking about the X utility) and the settings change after a while (seemingly at random) which makes me think it's controlled by the network and not the system.  But I want to be sure before I start smacking my head against my router.

---

### Post by dentaku65 on 2008-07-07
> **blackhatbrigade said:**
> Should I assume that because that line is commented out that it currently gets the DNS server list from the router/DHCP Server?

The reason I ask is because I'd rather just figure out the problem there so I don't have to do this to every machine on my network (or every machine that will be a part of network).

It's normal to get the dns configuration from DHCP server.
You can bypass this changing (on every machine you needs on the same lan) the lines in dhclient.conf, otherwise as normal you get the DNS from DHCP (in your case from the router)

---

### Post by blackhatbrigade on 2008-07-07
That's what I needed to know. Thanks!

** /me trudges off to beat his router into submission **

---

