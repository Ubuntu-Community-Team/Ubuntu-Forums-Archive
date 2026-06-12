---
title: "Network dies after vpnc-disconnect"
date: 2008-06-07
forum: General Help
---

### Post by reader4 on 2008-06-07
Anyone else having this issue: I use vpnc to connect, do my thing, then use vpnc-disconnect.  At this point, my network dies.  No connection to anything... I can't ping IP addresses, etc.  I have to restart the computer to get things going again.  I've tried restarting the network and resetting the route information - no luck.  Any help would be appreciated.

---

### Post by artships on 2008-06-17
I'm not sure what you mean by "resetting the route information" but it sounds like /etc/resolv.conf is not being changed back to list your nameservers.

Execute, to see what it really is:

ls -l /etc/resolv.conf

To see it's contents execute :

cat /etc/resolv.conf

After running vpnc again:

cat /etc/resolv.conf

There is a command to return the contents to the original, but I don't know that.

---

### Post by freak42 on 2008-11-03
I know, a bit late, but still.

try executing
```
sudo modprobe tun
```

before making your next vpnc connection, and
check if it solves the problem (your normal internet
connection should be back up when you vpnc-disconnect)

if it indeed resolves your problem make this change permanent by adding
```
tun
``` on a new line
to your /etc/modules file (sudo gedit /etc/modules)

hth

---

