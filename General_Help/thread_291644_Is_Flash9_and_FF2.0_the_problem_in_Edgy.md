---
title: "Is Flash9 and FF2.0 the problem in Edgy?"
date: 2006-11-02
forum: General Help
---

### Post by Epperly on 2006-11-02
When I upgraded Dapper to Edgy(again, but this time the non-beta), I uninstalled Firefox 2.0 and installed 1.5, and Flash 9 was installed as well. Having this setup I still had my Firefox crashes like I thought 2.0 was responsible for, and I don't think it can be Flash 9 that is responsible because I have Flash 9 installed on Firefox 1.5 in Dapper and it works fine, no crashing..

So, for me at least, it doesn't add up too well...

---

### Post by pay on 2006-11-02
you need to change  your default depth to 24bit in your /etc/X11/xorg.conf

---

### Post by Epperly on 2006-11-02
um, that's it?

---

### Post by NeoChaosX on 2006-11-02
Yeah, it appears to be a bug involving the XComposite extension, using 15 or 16-bit color and the Flash player. [It's fixed](http://www.kaourantin.net/2006/10/flashxcomposite-crasher-in-x11.html), but it won't show up until the next Flash 9 beta.

I always have my colors set to 24-bit, so I haen't had any crashes. :cool:

---

