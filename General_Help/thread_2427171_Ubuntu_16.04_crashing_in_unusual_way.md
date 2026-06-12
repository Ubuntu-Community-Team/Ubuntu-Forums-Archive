---
title: "Ubuntu 16.04 crashing in unusual way"
date: 2019-09-18
forum: General Help
---

### Post by BryanPotts on 2019-09-18
My ubuntu 16.04 installation periodically freezes by looping the last second or so in audio while the screen is completely locked. This repeats for maybe 15-20 seconds than self-reboots.

I've tried swapping out the PSU, ubdating the GRUB settings by changing...

```
GRUB_CNDLINE_LINUX_DEFAULT=quiet splash"
```
into
```
GRUB_CNDLINE_LINUX_DEFAULT=quiet splash intel_idle.maxcstate=1"
```

However, this has not resolved the issues. dmesg doesn't seem to show anything after a crash, but after the next crash I can update the post with the results. I've also read that a similar issue can be caused by a bad GPU. However I'm using onboard graphics and I want to make sure, as reasonably possible, that it isn't something else before I dump the money on a new MoBo.

Thank you! Any extra information I can provide that is needed I will post as soon as possible.

---

### Post by TheFu on 2019-09-18
Onboard GPUs are usually in the GPU, not on the motherboard.  I've never heard of a failure.

Check all the system logs in /var/log/ for issues.
Also, it sounds like a low-memory situation.  How much RAM and swap is configured?
```
free -hm 
```
will show that. If you know it is about to happen, perhaps running **top** to see the current situation is worth while?

---

