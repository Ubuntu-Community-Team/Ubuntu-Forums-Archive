---
title: "/var/logs terminology"
date: 2008-01-08
forum: General Help
---

### Post by gilloz on 2008-01-08
In looking at my /var/logs I can't understand some of the terminology or abbreviations that they use in the various logs listed.  Where can I get definitions to the terms used in these logs?

---

### Post by MobiusNZ on 2008-01-08
You're probably best to google (or ask) about a specific log, but most system logs log in the format
```

[DATE] [TIME] [COMPUTERNAME] [PROGRAMNAME]: [MESSAGE]

```
Generally a google of [PROGRAMNAME] and [MESSAGE] will give you a good idea of what is happening.

For example, the last entry in my server's log at the moment is
```

Jan  9 09:47:26 sarge dhcpd: DHCPACK on 192.168.1.101 to 00:0f:ea:4c:fb:82 (grif) via eth0

```
This is saying that on Jan 9 at 09:47:26 on that server (sarge), dhcp sent a DHCPACK (acknowledgment) to a client pc, giving details of which address it assigned and the client's mac address.

---

