---
title: "X11 and the DISPLAY variable"
date: 2007-06-13
forum: General Help
---

### Post by TheodoreWard on 2007-06-13
I have been playing around with trying to use alternate display locations for applications with little luck. 

Trying to follow the instructions from: [http://www.linux-tip.net/cms/content/view/302/26/](http://www.linux-tip.net/cms/content/view/302/26/)

# Start X on another console
$> X :12.0 vt12 2>&1 >/dev/null &
  # (I had to change /etc/X11/Xwrapper.config -> allowed_users=anybody)

# Verify it's running
$> ps -ef
...
root     22575 19672  3 12:24 ?        00:00:01 X :12.0 vt12

$> xterm -display :12.0
AUDIT: Wed Jun 13 12:27:00 2007: 22575 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":12.0" refused by server
Xlib: No protocol specified

xterm Xt error: Can't open display: :12.0

I have had no luck in figuring this out. Clearly display :12.0 is running... So any ideas what I'm doing wrong? 

Thanks
Ted Ward

---

