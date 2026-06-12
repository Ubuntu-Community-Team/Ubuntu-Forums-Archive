---
title: "Ethernet disabled"
date: 2005-11-02
forum: General Help
---

### Post by dummy on 2005-11-02
Yesterday I finally installed my first linux-system on my Thinkpad T42 with intel pro 1000MT ethernet card and the atheros w-lan mini pci adapter.

After I finished the installation procedure everything worked fine except for the w-lan, but I heard that I would need some advanced trickery to get this to work so I didn't wonder...

But as I restarted Kubuntu today, the ethernet adapater is disabled and I can't enable it again (if I try to do so in the settings it just stays disabled).

I hope somebody here can help me to reenable my ethernet adapter and possibly even my w-lan (alltough that one is not the priority)

thx

---

### Post by TomG on 2005-11-02
May be : 
K menu -> Utilities -> Network -> select Eth0 -> activate

Tom

---

### Post by dummy on 2005-11-02
well that was my first try as well. however, if i try to enable the adapter it just stays disabled. So nothing changes...

dummy

---

### Post by tonysathre on 2005-11-02
from the konsole:

ifup eth0

---

### Post by ecobuntu on 2005-11-02
if you have gnome installed you could use network-admin

---

### Post by dummy on 2005-11-06
It's workings again now...

pretty strange as I'm quite sure I didn't change anything. However, it's working now so everything's fine... :smile: 

thx
dummy

---

