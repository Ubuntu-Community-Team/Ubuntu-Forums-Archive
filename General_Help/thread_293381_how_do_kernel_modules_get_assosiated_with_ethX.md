---
title: "how do kernel modules get assosiated with ethX?"
date: 2006-11-05
forum: General Help
---

### Post by glenndavy on 2006-11-05
hi - just wondering how an ethernet kernel module gets associated with an ethernet 'device' number (i.e. eth0,eth1 etc).

For example if I have 2 network cards, say eth0=ne2kpci and eth1=sky2, - where is that association 'written' or stored, or inferred? similiarly, if I want (for whatever insane reason) to swap these so that eth0=sky2 and eth1=ne2kpci - where/what do i edit? 
In suse, you can use Yast to explicity make this association, is there an equiv somewhere in deb based systems?

questions mostly academic for my satisfaction - and I have other ways of solving the real problem im presented with - but I'd love to know

Glenn

---

### Post by mark_g on 2006-11-05
Those names are stored in /etc/iftab.

---

### Post by glenndavy on 2006-11-05
thanks mark_g - damn I knew it would be simple - I even did a grep eth /etc/* - missed it - thanks, i feel foolish, but much saner
glenn

---

