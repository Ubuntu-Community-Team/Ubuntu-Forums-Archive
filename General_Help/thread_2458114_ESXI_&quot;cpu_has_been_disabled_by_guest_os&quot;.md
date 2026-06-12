---
title: "ESXI &quot;cpu has been disabled by guest os&quot; Ubuntu Server 20.04"
date: 2021-02-16
forum: General Help
---

### Post by lmtech on 2021-02-16
VT-XI have a server I built a couple days ago to host NextCloud that ran great for a few days but has started to lock up overnight, every night for no reason I can determine. the only real clue I can find is the error "cpu has been disabled by guest os" from VMware ESXI.  System boots clean and perfprms as expected until the next night, when we try to log in the next morning same error.  I have checked the recommended settings regarding the error from VMware (VT-X enabled in bios and CPU Id masked) with no luck.  I'm a mid level at best Linux administrator and feeling a bit lost, any ideas for me?

---

### Post by TheFu on 2021-02-16
Check the system logs on the ESXi host. Look for hardware errors there.

---

