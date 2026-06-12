---
title: "Serve DHCP on Desktop version?"
date: 2007-03-26
forum: General Help
---

### Post by Drate on 2007-03-26
I am in the process of making a total convert out of my father, but to maintain internet functionality on his lan I need to make on of his Desktops a DHCP server, XP had some sort of method for this, we do have two NICs installed, we are running Edgy desktop version on this machine, what do we need to do?

---

### Post by mexlinux on 2007-03-27
Try this:
[https://wiki.ubuntulinux.org/DHCPD_-_Dynamic_Host_Configuration_Protocol_Daemon](https://wiki.ubuntulinux.org/DHCPD_-_Dynamic_Host_Configuration_Protocol_Daemon)

---

### Post by simonn on 2007-03-27
To be honest, look at dns-masq. It is a dns cacheing and DHCP server designed for small home LAN type of networks.

It is a lot easier to setup than dhcpd and the DNS cacheing does seem to speed up things.

---

### Post by Drate on 2007-03-27
To the first post... um... is that available in english?  I mean, I guess I could just type in the commands, but I'd prefer know what it was. :biggrin: 

But thank you both, I'll look into both of those ideas and see what happens!

BTW, I have been suggested to try IP Cop... know anything about this?

---

### Post by simonn on 2007-03-27
IP Cop turns a PC into a dedicated router. So, if you want a dedicated router it is good. However, if you also want to use the PC, it is not what you want.

---

### Post by dcstar on 2007-03-27
> **Drate said:**
> To the first post... um... is that available in english?  I mean, I guess I could just type in the commands, but I'd prefer know what it was. :biggrin: 
........

There will be a DHCP server package in Synaptic, just do a search for those terms and then install the package.

---

