---
title: "Boot hangs on- configuring network interfaces"
date: 2007-04-04
forum: General Help
---

### Post by lancest on 2007-04-04
Feisty boots slow because has to stop at: *configuring network interfaces*.   How to fix this?  I also notice my wireless is very slow to connect to my buffalo router. Have to restart the router often (not with windoze however)
Intel wireless 3945

---

### Post by kwilliam on 2007-04-05
This is a confirmed bug.  (see [https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/102675](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/102675))  The comments also suggest a fix.  I'm about to reboot to try it out myself, so I'll let you know how it goes.

I don't know about the router bit.  I'm using a Linksys.

---

### Post by kwilliam on 2007-04-05
Alright, to fix the boot hanging, delete everything but the first two lines in "/etc/network/interfaces".  It should say only
> auto lo
iface lo inet loopback

Apparently an update messed up the file.

---

### Post by jdriessen on 2007-04-05
> **kwilliam said:**
> Alright, to fix the boot hanging, delete everything but the first two lines in "/etc/network/interfaces".  It should say only

Apparently an update messed up the file.

fixed my problem. thanks for the tip.

---

