---
title: "Ubuntu Gateway with Exchange Configuration"
date: 2015-09-15
forum: General Help
---

### Post by ajnozari on 2015-09-15
Ok, so first I hope that this is in the right place.

I have needed to replace my old firewall (Microsoft Threat Management Gateway) for a while and finally got around to installing Ubuntu 15.04.  I have set it up as a gateway and I am able to connect to the internet, but everything is redirecting to the internal web domain instead of loading external sites.  I think a route is borked there.

I am using iptables and apache reverse proxy in order to get things up and running.  I am using webmin for the iptables and most everything works except RDP which isn't that big of a deal for me right now.  I have opened the ports but nothing.

However, for some reason any attempts to ping will only go out over the external interface eth1 and nothing can resolve (using FQDN and microsoft wins names) over eth0 (internal).

I have also setup exchange OWA reverse proxy with Apache and have installed my certificates.  However I cannot login to OWA nor can I utilize autodiscover for exchange settings and cannot get email from outside my local lan.

I can post information as it is requested so that I don't overload you guys with stuff to look at.

Thanks in advanced.

---

