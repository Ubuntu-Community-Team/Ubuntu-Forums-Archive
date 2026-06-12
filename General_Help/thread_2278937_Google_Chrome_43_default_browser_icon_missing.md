---
title: "Google Chrome 43: default browser icon missing"
date: 2015-05-20
forum: General Help
---

### Post by vasa1 on 2015-05-20
I got updated to Google Chrome 43 today. It's working fine but I'm not seeing the usual Google Chrome icon. Instead, I'm seeing the icon that Openbox uses when there's no specific icon available :(

---

### Post by kerry_s on 2015-05-20
what panel are you using ? maybe remove & add again.
i just updated mine earlier, had no problems with plank. but i also do the chrome launcher fix, so my launcher is in ~/.local/share/applications 

i'm assuming you already rebooted since there was a kernel update along with it.

---

### Post by spsf2 on 2015-05-20
Seems to happen in XFCE and Mate, check these links:
[https://bbs.archlinux.org/viewtopic.php?id=197589](https://bbs.archlinux.org/viewtopic.php?id=197589)
[https://code.google.com/p/chromium/issues/detail?id=478714](https://code.google.com/p/chromium/issues/detail?id=478714)
No solution for now...

---

### Post by vasa1 on 2015-05-20
> **kerry_s said:**
> what panel are you using ? maybe remove & add again.
i just updated mine earlier, had no problems with plank. but i also do the chrome launcher fix, so my launcher is in ~/.local/share/applications 

i'm assuming you already rebooted since there was a kernel update along with it.

No joy after a reboot. The panel is tint2. I also tried lxpanel but the icon stayed missing :(

> **spsf2 said:**
> Seems to happen in XFCE and Mate, check these links:
[https://bbs.archlinux.org/viewtopic.php?id=197589](https://bbs.archlinux.org/viewtopic.php?id=197589)
[https://code.google.com/p/chromium/issues/detail?id=478714](https://code.google.com/p/chromium/issues/detail?id=478714)
No solution for now...
Thanks for the links. Looks like someone has taken up work on the bug. I starred the bug for what it's worth :)

---

### Post by Seamless in Northampton on 2015-05-20
I am having the same icon problem with Firefox. That also arrived with my being stuck in a login loop and at my wit's end with fixing it, so no idea if it relates, but maybe it's of use!

---

### Post by vasa1 on 2015-05-20
A fix maybe on the way: [https://code.google.com/p/chromium/issues/list?q=label:Merge-Approved-43](https://code.google.com/p/chromium/issues/list?q=label:Merge-Approved-43)

---

### Post by vasa1 on 2015-05-25
Today's update to version Version 43.0.2357.81 brings back the icon.

---

