---
title: "Router Traffic Monitor"
date: 2022-07-28
forum: General Help
---

### Post by mauricekuhn on 2022-07-28
[COLOR=#000000]I have a dumb question about monitoring my traffic at the router/IP level. I recently "upgraded" my router from an TPLink Archer 7, which had a traffic statistics function, to an Archer 8, which doesn't.[/COLOR]

[COLOR=#000000]Is there a simple traffic monitoring app that will do the same thing at the router level (and not just for the traffic on my PC)? I've installed darkstat, but can't figure out how to fire it up.[/COLOR]

[COLOR=#000000]Thanks![/COLOR]

---

### Post by TheFu on 2022-07-28
Many routers support SNMP, so if you setup an SNMP server on your Linux system and have the router send SNMP traffic to it, then you can see all sorts of things.
Or get a better router.  Any that run OPNSense or pfSense generally have network-wide traffic for each client-system using a tool called netflow.

For example: [https://www.linuxscrew.com/how-to-monitor-traffic-at-cisco-router-using-linux-netflow](https://www.linuxscrew.com/how-to-monitor-traffic-at-cisco-router-using-linux-netflow) shows how to use Cisco and Linux to monitor traffic.
Other results showed how to configure different routers, none of the brand you listed, to sent their netflow data to Nagios.

I'm lazy, so my router runs OPNSense and has netflow built-in.

---

