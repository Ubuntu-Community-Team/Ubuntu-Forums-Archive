---
title: "network applet frozen in 12.04"
date: 2013-03-09
forum: General Help
---

### Post by jimzen on 2013-03-09
Been using ubuntu since V5.04.  Shortly after I installed 12.04 (I always install from scratch, never by the "upgrade" route), the little gizmo in the upper right corner that represents network connectivity stopped updating its visuals.

I have all the connectivity, I just don't get a proper visual representation of it; the applet or whatever it is just shows an empty pie-slice.

I've put up with that for the past 8 months or so.  This morning I tried reinstalling Network-Manager.  That didn't accomplish anything.

Help.

---

### Post by rnerwein on 2013-03-09
hi
if you mean that the sign is there but empty - same thing happened on my box time ago  (12.04 LTS). the reason was easy. my son switched the wlan off on my router ( is just a little knob).
try: sudo iwlist scan (even the router wasn't in wlan state -> works)
ciao

---

### Post by jimzen on 2013-03-09
> **rnerwein said:**
> hi
if you mean that the sign is there but empty - same thing happened on my box time ago  (12.04 LTS). the reason was easy. my son switched the wlan off on my router ( is just a little knob).
try: sudo iwlist scan (even the router wasn't in wlan state -> works)
ciao

I'm not doing anything, on this machine, with wireless.  When I ran 'sudo iwlist scan' it reported
"lo        Interface doesn't support scanning.
vboxnet0  Interface doesn't support scanning.
eth1      Interface doesn't support scanning.
eth0      Interface doesn't support scanning."

In its present configuration, only eth0 is in use.  eth1 is another NIC, currently not connected to anything.

Thanks for your speedy reply.  It's a trivial issue, I suppose: but I want that little icon to report the true state of my networking connections.

---

### Post by steeldriver on 2013-03-09
it has been like that a while for me - I just kill and restart the applet:

```

pkill nm-applet
nm-applet 2>/dev/null &

```

---

### Post by jimzen on 2013-03-09
> **steeldriver said:**
> it has been like that a while for me - I just kill and restart the applet:

```

pkill nm-applet
nm-applet 2>/dev/null &

```

Uh -- yes, that kills the applet, and restarts it, but nothing else changes.  I still get the empty pie-slice.  What I'm looking for is the two-arrow icon that indicates a hardwired network connection.

I suppose that could turn out to be some misconfiguration of the stuff in /etc/dbus-1.system.d or something similar.  I've never knowingly messed around with that, but accidents can always happen.

---

