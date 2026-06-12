---
title: "Loading after power failure"
date: 2017-06-11
forum: General Help
---

### Post by jimmykez on 2017-06-11
Hello,

Ubuntu 10.0.4, 3.0.0-15

After power failure Linux won't boot - Kernel panic - not syncing: VFS: Unable to mount root fs on unit block(0,0)
I have checked file systems already.

Any ideas how to fix this issue?

Thanks

---

### Post by Impavidus on 2017-06-11
10.04? That's ancient and no longer supported. You've had no updates for over 2 years and if this is not a pure server, the desktop parts haven't had updates for over 4 years. And kernel 3.0.0-15 sounds even older than that, but as it's no longer in the archives I can't really check it.

But we could provide support to help you move to a more recent release. There aren't so many people left who're still familiar with the peculiarities of 10.04.

---

### Post by jimmykez on 2017-06-11
> **Impavidus said:**
> 10.04? That's ancient and no longer supported. You've had no updates for over 2 years and if this is not a pure server, the desktop parts haven't had updates for over 4 years. And kernel 3.0.0-15 sounds even older than that, but as it's no longer in the archives I can't really check it.

But we could provide support to help you move to a more recent release. There aren't so many people left who're still familiar with the peculiarities of 10.04.

Thanks, I know it's very old release. After restore process yes, I sure it will be good idea to move out of kernel 3.0 )

I have used new release Ubuntu with rescue mode and I was surprised I not able to use update-initramfs command :(
In my case maybe somebody know how I can do it? I mean how I can update initram in this scenario.

Thanks!

---

### Post by efflandt on 2017-06-11
Your best bet is to see if you can repair it enough from live/install system booted from USB or DVD to at least be able to mount your partition(s) and copy anything to external storage not already backed up. Then install a newer Ubuntu version from scratch.

I still have 10.04 (32 and 64-bit versions) on an old PC that I have not used for a while. It is an early Athlon64 3200+ (2 GHz) single core from 2004 w/legacy ATI X1300 AGP graphics. I did boot 64-bit 16.04 live/install on it from USB and that works (slowly). I also have an old Dell Dimension 4700 from work with single core Pentium 3.2 GHz with hyperthreading, but no SpeedStep or 64-bit. I installed 32-bit 16.04 on it, but its PCIe 1.0 slot is so slow that even with my old GTX 550 Ti, I have to throttle streaming video to 480p to avoid dropped frames. It was also dropping frames with GTX 750 Ti. So it is just too old and slow to take advantage of modern graphics. Both were connected to real 720p (1280x720) HDTV Ready LCD via DVI.

---

