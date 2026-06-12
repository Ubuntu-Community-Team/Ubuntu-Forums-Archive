---
title: "[SOLVED] Will Wubi Work on Software-Raid Partitions?"
date: 2007-08-05
forum: General Help
---

### Post by quda on 2007-08-05
Hi there,

I'd love to install ubuntu via wubi, there's just one question that keeps bothering me:

I have a software raid-0 setup on my two sata drive (via chipset), from which windows boots.

I'm quite certain, that there are no drivers for linux for this cheap raid implementation. But as windows works flawlessly, i couldn't help but wonder, if I could install ubuntu as a file on a raid-0 partition nonetheless?

And if not: would it help to have an additional non raid drive?

any ideas?

---

### Post by tuxcantfly on 2007-08-05
> I'm quite certain, that there are no drivers for linux for this cheap raid implementation.

In that case, Wubi probably won't work since it needs to mount the host NTFS partition before it can loopmount the virtual disk file, but just to be sure, you could always try and see (if it doesn't work you can just uninstall), also you might want to see [https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

---

