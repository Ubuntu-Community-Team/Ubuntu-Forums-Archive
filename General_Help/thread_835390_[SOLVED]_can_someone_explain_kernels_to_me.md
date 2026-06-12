---
title: "[SOLVED] can someone explain kernels to me?"
date: 2008-06-20
forum: General Help
---

### Post by natirips on 2008-06-20
Can someone tell me what's the difference between diffrent kernel versions like: linux-image-VERSION-generic ...-openvz ...-rt -server -xen
For some reason I cannot explain, I have most of them installed, and had no problems with that before, but recently the -rt version got updated and was set as default, with it the computer couldn't detect my graphics card, when I used -generic, it run just fine (and I'm using it right now). Is it safe to uninstall them all except the -generic one, or is some version other than -generic better for 64-bit computers (I have a 64-bit one)?

---

### Post by Nepherte on 2008-06-20
I think rt is the real-time version of the kernel mostly used in systems that require immediate response of the system. Audio recording or alike for example. That's why Ubuntu Studio comes with that one. For normal use the generic one is the one you'd want. You can safely remove those normally. The xen kernel is for virtualization I believe.

---

