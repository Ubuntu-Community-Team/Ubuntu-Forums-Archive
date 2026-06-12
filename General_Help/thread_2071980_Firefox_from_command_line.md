---
title: "Firefox from command line"
date: 2012-10-16
forum: General Help
---

### Post by otetiani on 2012-10-16
Trying to run Firefox from the command line with LightDM stopped.  What I would like is to start Firefox and when I close it I return to the command line.

I can do this now by starting LightDM, logging in, opening Firefox, using Firefox, closing Firefox, and stopping LightDM.  I am using Lynx for now, but would like the bookmark feature from Firefox which I have added to over the years.

I looked at the solution for servers, but as I have LightDM installed I couldn't see how it applies.

Thanks

---

### Post by Toz on 2012-10-16
Try this:
```
xinit firefox $* -- :1
```

This will start X, run firefox, and upon exit, return you back to the command prompt.

---

### Post by otetiani on 2012-10-17
Works perfectly, thanks.  Sorry for wasting time with something I should have figured out myself, time to spend more time in the man pages I guess!:-?

---

