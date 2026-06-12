---
title: "Show Network Connection selection on login screen?"
date: 2015-03-03
forum: General Help
---

### Post by peridian on 2015-03-03
Hi,

Can you show the network connections toolbar options on the login screen?

I have a single LAN port on this machine, that gets connected to one of three LAN switches, each one with its own address/subnet.  I have all three saved as configured Ethernet connections, and can switch between them as appropriate.

The problem is that at the point of login, there seems to be no control over which one it will pick, it seems to be random.  This causes some issues with the nslcd settings.  All three subnets are able to access a central kerberos/ldap service, so none of the config for that changes between the switches.  Since the interface address and gateway change depending on which switch it is plugged into, an inability to establish the correct connection then either a) prevents the nslcd service from correctly obtaining the list of valid users, or b) prevents the machine from obtaining a kerberos ticket to login with.

Regards,
Rob.

---

### Post by dino99 on 2015-03-03
Only my two cents,
actual design require that a session is opened (so past login) before beeing able to work with it.
I suppose you need to adapt some network config files ; but the "general help" forum will probably never returns a solution. Better to ask into the "network" forum where people are aware of different issues; or even better, write your question on 'http://askubuntu.com/' and devs will answer you with way better solutions.

---

### Post by peridian on 2015-03-03
Thanks, I had started to suspect that you needed to be logged in for the network to be selectable.

I'll search elsewhere and see what I can find out.

Regards,
Rob.

---

