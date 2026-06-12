---
title: "Alright, I can't get any updates or anything"
date: 2008-01-08
forum: General Help
---

### Post by Master-of-None on 2008-01-08
I don't know if this is a problem on my end, or the update server, but this is the 3rd time I reinstalled Ubuntu for various windoesn't dual-boot problems. Now, this time, I can't seem to connect to the update servers(Canonical?) but in any case, this is a huge inconvienience in the worst possible time and I'd like a temporary fix, or some help getting back together.

---

### Post by PeterJS on 2008-01-08
Was the machine connected to the internet when you installed this latest time. There's a [bug](https://blueprints.launchpad.net/ubuntu/+spec/networkless-installation-fixes) in gutsy that causes it to disable online updates if it's installed without an active internet connection. To fix this go to System > Administration > Software Sources and re-enable the four main repositories.

---

