---
title: "vino.server starts using 1 CPU full"
date: 2016-06-15
forum: General Help
---

### Post by Roland_Msl on 2016-06-15
I use Ubuntu 16.0.4 on an Acer ES1-331-C0YK notebook with quadcore Celeron N3150

At each start, the fan starts, the reason for the fan is, that vino-server uses 25% CPU power, 1 of 4 CPUs full.

When I stop the prozess with Gnome System Monitor, the system is quiet again.

Since stopping the process seems to have no negative side effects,
how to prevent this process to start,
why does this process use 1 CPU full?

---

### Post by steeldriver on 2016-06-15
If you're not using remote desktop, then simply disable it - either from the 'Desktop Sharing' GUI, or from a terminal using dconf

```

dconf write /org/gnome/desktop/remote-access/enabled 'false'

```
(this works on 14.04, if it doesn't work for you please post back and we can investigate further)

As to why it's loading the CPU, I can only guess - if your VNC port is accessible from the public network then perhaps it's fighting off script kiddies / post scanners

---

