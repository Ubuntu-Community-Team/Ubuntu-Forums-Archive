---
title: "Has Anyone Tried Accessing A VPS Using Dial Up ?"
date: 2013-09-21
forum: General Help
---

### Post by Omnipresence on 2013-09-21
Has anyone tried accessing a VPS using dial up ?

Is it even possible ?

Thanks

---

### Post by TheFu on 2013-09-21
Not recently, but I have used dialup to connect to UNIX machines over ppp.
A VPS will not provide dialup endpoints. You'll need an ISP (dialup) to get onto the internet, then just use ssh to the VPS.  In no way would I attempt a remote desktop.  I tried it and back then it took 20 mins to see the desktop, 2 min for any button press ... bad idea.

---

