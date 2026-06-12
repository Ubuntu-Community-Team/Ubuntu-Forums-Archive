---
title: "Power outage--Now Ubuntu won't boot"
date: 2007-05-31
forum: General Help
---

### Post by Sturm on 2007-05-31
We had a power outage last night sometime, evidently, as all the clocks are flashing here.  My main gaming PC, which has Windows on it, seemed to boot okay after a couple of tries.  The Ubuntu server machine, however, appears to be having issues.

It was hung up on booting, so I just hit the "reset" button on the case to start fresh.  Now I get the "Ubuntu" loading bar, but it stops about 1/32 of the way up.  If I let it sit like that for a few minutes, it then goes to a text view of what's happening, and I only see:

```
* Reading files needed to boot...
```

...and it just stays like that forever.  What can I do to fix this problem?  Thanks.

---

### Post by phidia on 2007-05-31
I'm not 100% sure on a server install but if you have the install cd you may be able to boot from that.  At the start menu see if you can chose "rescue broken (or unbootable) system"

---

### Post by Sturm on 2007-06-01
It's not really a server install; I just call it my "server", but it's really a desktop install.  It's Feisty 7.04.

Booting from the Live CD, I am not given an option anywhere to "rescue broken (or unbootable) system."  Where would I find that?

---

### Post by Sturm on 2007-06-01
Just for kicks, I chose an earlier kernel version at the GRUB screen--that seemed to work.  Hopefully, it will stay that way and I won't have to come back to this thread again to complain.  ;)

---

### Post by sefs on 2007-06-01
Which means you can now reinstall the latest kernel (from the working installation) and everything should work?

---

