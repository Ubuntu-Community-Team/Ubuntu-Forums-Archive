---
title: "Screen Won't Stay On"
date: 2013-06-30
forum: General Help
---

### Post by AnotherKevin on 2013-06-30
Running newest release.  Turned off screensaver and disabled powersaver.  Monitor goes off after about 10 minutes.  Can't find anything else to investigate.  My PC is a HP Omni (all in one).  No issues with memory or processors.

Any one have an idea of where I should look now?

Thanks!

Kevin

---

### Post by pqwoerituytrueiwoq on 2013-06-30
Hostilely i find that strange i usually have difficulty getting the opposite to happen, always get black screen instead of off screen
anyway give this command a try
```
xset -dpms
```
not expecting output, hoping that makes it act as you desire
to undo it
```
xset dpms
```
to view current state
```
xset -q | grep -ce 'DPMS is Enabled'
```
1 means Enabled 0 means Disabled

---

### Post by AnotherKevin on 2013-06-30
Thanks!  I think that's it!

---

