---
title: "[SOLVED] Uninstalled when built from source"
date: 2007-06-25
forum: General Help
---

### Post by galvao on 2007-06-25
Hi everyone.

This is a long time question that I have:

How can I uninstall a software that I've installed via ./configure -> make -> make install?

I know, I know, I always try to stick with installations via Synaptic, but sometimes I'm forced to deviate from that.

On a related subject (sorry to post everything in one single question, just tell me and I'll split): What is the difference between using Synaptic and the "Add/Remove" in the Applications Menu? I mean, if there's Synaptic why having the other?

TIA,

---

### Post by FuturePilot on 2007-06-25
I think you can just run```
sudo apt-get remove blah-blah
``` or it should also be listed in Synaptic.

The Add/Remove program is a front end to Synaptic. I think it's there because it's more user friendly for new users. Synaptic is like the Advanced mode. In fact I think there's a button in the Add/Remove that will launch Synaptic. Simply put they both do the same task and are both front ends to apt-get

---

### Post by galvao on 2007-06-25
Sorry, I believe I wasn't clear:

I build from source when it's *not* listed at Synaptic, and therefore not listed in apt-get either.

Thanks,

---

### Post by FuturePilot on 2007-07-03
Ah, hopefully you still have the source for whatever you installed. cd into that directory and ```
sudo make uninstall
```
I think that should do it.

---

