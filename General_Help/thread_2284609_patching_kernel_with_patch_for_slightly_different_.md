---
title: "patching kernel with patch for slightly different version"
date: 2015-06-30
forum: General Help
---

### Post by halfbeing on 2015-06-30
I want to build a kernel with the -rt patch because I believe that I am not getting satisfactory performance from the low-latency kernel. I want to stick with the Ubuntu kernel sources if possible to reduce the number of things that could go wrong. However the sources I have for Ubuntu 15.04 are version 3.19.something, while the latest -rt patch at kernel.org is for version 3.18.something. Will I be OK to try to patch the 3.19 sources with the 3.18 patch despite the slight discrepancy of version numbers?

Alternatively, would I get into a mess if I tried to run Ubuntu from a kernel built from vanilla sources (+ the -rt patch of course)?

---

### Post by sandyd on 2015-06-30
The instructions here should help: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.17-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.17-vivid/)

Required patch files are in [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.17-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.17-vivid/)

This should give you a kernel with Ubuntu patches. You can then apply the RT patches on top.

---

### Post by halfbeing on 2015-06-30
Thank you :) I'll try it out later when I get a bit of time.

---

