---
title: "Is Microsoft Virtual PC VMC/VHD Files usable by any program?"
date: 2008-07-03
forum: General Help
---

### Post by Newuser1111 on 2008-07-03
I need some way to run these,(VMC is the settings and VHD is the hard drives)
But Microsoft Virtual PC is not on Ubuntu.


Note: I do not want to use VMware.

---

### Post by eriqjaffe on 2008-07-03
You may be able to convert it to a RAW image with qemu-img, but beyond that I don't know.  I don't think there's anything Linux-native that can read a VHD file directly.

---

### Post by Newuser1111 on 2008-07-03
> **eriqjaffe said:**
> You may be able to convert it to a RAW image with qemu-img
What would use that?
And how long would 15GB take?(It's 4 VHD's, the largest one is 9.25GB)

---

