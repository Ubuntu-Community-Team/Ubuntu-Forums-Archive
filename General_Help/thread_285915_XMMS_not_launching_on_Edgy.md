---
title: "XMMS not launching on Edgy"
date: 2006-10-27
forum: General Help
---

### Post by Ferio on 2006-10-27
Since I upgraded yesterday to Edgy, XMMS won't launch. If I try to do it from a terminal (using both normal and root users), it says:
> Message: device: default
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 2472 error_code 8 request_code 72 minor_code 0


Any idea?

---

### Post by Ferio on 2006-10-28
I've just switched to Beep Media Player, but I'd like to return some day to XMMS. Well, in fact I'd hope that Rhythmbox worked for me just one time, but it hasn't done it ever...

---

### Post by cbpxy on 2006-10-30
I had this problem, too (and I'd love to see it fixed).  According to this bug report: [https://launchpad.net/distros/ubuntu/+source/xmms/+bug/63144]("https://launchpad.net/distros/ubuntu/+source/xmms/+bug/63144")   (which I found in another thread), the problem is that my config had double-sized enabled (the "D" button).  The trick is to start it like this:
```
export XLIB_SKIP_ARGB_VISUALS=1 && xmms
```
This is my only problem with edgy so far.  Great work, all!

---

