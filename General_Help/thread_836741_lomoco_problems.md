---
title: "lomoco problems"
date: 2008-06-21
forum: General Help
---

### Post by circlemaster on 2008-06-21
Hi.

I have 2 serious problems with lomoco that I really want to fix asap:

1) It does not set the resolution for my mouse when I log into Ubuntu, I have to do "sudo lomoco -8" manually.

2) At seemingly random times, my mouse resolution is set back to 400 dpi. This, as you may understand, is especially frustrating if you play latency-dependant FPS games that can't handle many seconds of these problems without something turning around because of it.

Specs:
Ubuntu Hardy Heron (amd64)
Intel C2D
GeForce 8800GTS (proprietary drivers)
Logitech mx500 (LOGITECH_MOUSE_RESOLUTION=800 is set in /etc/default/lomoco)

Thanks.

---

### Post by circlemaster on 2008-06-25
Ok the problem is not lomoco, it must be in the kernel. Here's the kernel log for what happens frequently: [http://rafb.net/p/WXwcFw14.html](http://rafb.net/p/WXwcFw14.html)

---

