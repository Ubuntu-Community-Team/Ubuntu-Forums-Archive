---
title: "compiz shutdown note"
date: 2012-10-28
forum: General Help
---

### Post by carlton22 on 2012-10-28
Using Ubuntu 12.04 on an HP laptop, have had it up for close to a week and it has been working fine, but just now when I tried to shut down the computer (and I've tried several times) I get a message in the shutdown box saying, "compiz not responding." There's an option to shut down anyway, but I don't know what the consequences of doing that might be. No other programs are windows are up when I was trying to shut down.

I'm unfamiliar with compiz - what it is. Any idea what's happening here, and suggestions how to proceed? (I've not yet carried through with a shutdown since seeing the message.)

---

### Post by stinkeye on 2012-10-28
Compiz is the window manager for Unity.
It should be ok to shut down.

Can try setting Unity back to default compiz settings...
Press alt+F2 and run
```
unity --reset
```
and then shutdown.

---

### Post by carlton22 on 2012-10-28
Thanks. I tried the reset and it seemed to work; then restarted the computer, and it came up fine. Issue evidently resolved.

---

