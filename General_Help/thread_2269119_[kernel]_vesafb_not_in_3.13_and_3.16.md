---
title: "[kernel] vesafb not in 3.13 and 3.16"
date: 2015-03-13
forum: General Help
---

### Post by f-mike-2 on 2015-03-13
Hi,

Before I consider posting this to launchpad as regression, I wanted to get some more feedback and make sure I wasn't doing anything obviously wrong.

I originally came across this issue due to having a bunch of Dell servers that I was testing with kernel 3.13 on 12.04. The text console is so slow that it is unusable and the text looks visibly different, as if it is a different font. Comparing the exact same system with kernel 3.2 or 3.11 loaded and running lsmod, vesafb is listed. It is not listed on the 3.13 system. The same issue exists on 14.04 with the 3.13 or 3.16 kernel.

Attempting to do modprobe vesa or modprobe vesafb returns:

```
modprobe: FATAL: Module vesa not found.
```

and

```
modprobe: FATAL: Module vesafb not found.
```

respectively.

I am familiar with [launchpad bug #1316035]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035"), but a lot of the discussion in there is about X and the "solutions" people are posting are also about X. I have no intentions of installing X on my servers, and a usable console of 1280x1024 is required.

Attempting to use uvesafb results in a black screen. Attempting to use vga16fb results in good performance, but I am locked to 640x480. I tried to use fbset to force higher resolutions, but it either results in a distorted display or tells me there is not enough memory.

Is there another way to manually load the vesafb that was present in previous kernels that I am unaware of, or is this regression?

Thanks

---

