---
title: "[SOLVED] Need to change port on Terminal Server Client"
date: 2008-01-12
forum: General Help
---

### Post by MountainX on 2008-01-12
I need to connect to a Windows Terminal Server from Ubuntu. I want to use the Terminal Server Client. The Windows Terminal Server is configured for a non-standard RDP port. How do I change the port in the Ubuntu Terminal Server Client? Thanks.

---

### Post by MobiusNZ on 2008-01-12
I believe you put a colon then the port number after the host name. eg rdp://example.org:9999

---

### Post by MountainX on 2008-01-12
The first thing I tried was using the colon followed by a port number and I could not get it to work. (That's the way it works in the Windows client, so I would have expected the same on the Linux client.)

---

### Post by MountainX on 2008-01-12
The problems seems to be that the Ubuntu machine can't resolve the name of the Windows server to an IP address. This is my first time using Linux, so I'm not sure how to make it aware of Windows hosts on the LAN.

---

### Post by MobiusNZ on 2008-01-12
You'll need to have some sort of DNS server to do that

---

### Post by MountainX on 2008-01-13
What about using the hosts file where I could simply enumerate host names and IP addresses for my LAN? My DHCP server always assigns the same IP to key machines on my LAN, so this might work.

Is there a simple way to get the kind of automated discovery/lookup that Windows has?

---

### Post by MobiusNZ on 2008-01-13
> **MountainX said:**
> What about using the hosts file where I could simply enumerate host names and IP addresses for my LAN?

Yep that will work, check out /etc/hosts

> **MountainX said:**
> Is there a simple way to get the kind of automated discovery/lookup that Windows has?

Not with windows interop as far as I'm aware, but I beleive 'Zeroconf' is meant to do this sort of thing for *nix based computers (including OSX). I'm not sure how mature the software for it is though....

---

