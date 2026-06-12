---
title: "Ubuntu Hardy inconsistantly starts up"
date: 2008-06-07
forum: General Help
---

### Post by kwolf on 2008-06-07
Hi,
I've did a fresh install of Hardy over a Hardy upgrade to Feisty, because I was having problems that I thought were most likely the fault of the upgrade (I'm having the same problems now). Basically what happens is when I select Hardy at the boot menu the loading bar just goes back and forth for about a minute, and then my computer restarts. *Sometimes* Ubuntu will load normally after a few tries, but it is quite a hassle to have to wait for it to eventually work. I've ran a repair install. Again, sometimes it works and I am allowed to boot Ubuntu, but most of the time it restarts my computer before I have such an option. 

The repair install seems to be getting caught up at at the point of:

```
 B HID core driver
aq timeout (cmd 0x27)

failed to read native max address
failed to recover some devices, retrying in 5 secs
revalidation failed (errno=-5)
```

Hopefully that's clear enough. Any help would be much appreciated.

---

### Post by ethanklein on 2008-06-07
I have a similar problem. It boots to a blank login screen. Very frustrating restarting every time waiting for it to boot correctly

---

### Post by josh8 on 2008-06-08
I've figured out that if I run a repair boot, even if the repair restarts and doesn't let me boot into ubuntu, the next time I try normally booting Ubuntu it will always work after the repair boot.

---

