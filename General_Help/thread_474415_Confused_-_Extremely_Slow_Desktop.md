---
title: "Confused - Extremely Slow Desktop"
date: 2007-06-15
forum: General Help
---

### Post by _simon_ on 2007-06-15
I'm wondering if anyone can shed some light on this.

I cold booted my machine this morning and it took 5 minutes for the desktop to load and when it did finally load it was taking up to a minute to open anything. (Normally it's very quick - I run an X2 4600+ with 2GB RAM)

My other half started her machine and it was doing the exact same thing!

I noticed that firefox wasn't opening pages, so restarted both router and DSL modem, this fixed the problem with both machines!

What I don't understand is why?

---

### Post by Mr. C. on 2007-06-15
Is your router's listed in /etc/resolv.conf on a nameserver line ?

MrC

---

### Post by _simon_ on 2007-06-15
My modem is but not my router, should it be?

---

### Post by Mr. C. on 2007-06-15
No, you should not use your router's or modem's poor DNS implementation.  These cheap products and their DNS implementations are not very robust, and have caused endless grief for users.  The have been primarily tested in Windows environments where the DNS system in Windows behaves differently than in Linux/Unix.

Set the nameserver lines in your /etc/resolv.conf file to the DNS servers provided by your ISP.  The will look like :

```
nameserver x.x.x.x
nameserver y.y.y.y
```

If you do not have that information available, first look on your ISP site, and if that fails, you can use the free DNS servers provided by opendns. ([www.opendns.com](www.opendns.com) for more info).

MrC

---

### Post by _simon_ on 2007-06-15
Thank you, already use opendns and those are entered, have removed my modem's IP from the list.

---

