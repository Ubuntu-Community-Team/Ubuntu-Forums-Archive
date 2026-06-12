---
title: "Ubuntu will not boot"
date: 2007-09-09
forum: General Help
---

### Post by Skia_42 on 2007-09-09
I recently ran a bunch of updates on my 7.04 laptop. When I restart the startup screeen with the status bar below Ubuntu stops while it is still a sliver. It stalls for around 5 minutes and I get a screen with Busybox and command line interface. Anyone know how I can get my system working without doing a reinstall? Thanks in advance.

---

### Post by confused57 on 2007-09-09
> **Skia_42 said:**
> I recently ran a bunch of updates on my 7.04 laptop. When I restart the startup screeen with the status bar below Ubuntu stops while it is still a sliver. It stalls for around 5 minutes and I get a screen with Busybox and command line interface. Anyone know how I can get my system working without doing a reinstall? Thanks in advance.
You could try booting into an older kernel.  When the busybox error occurs, does it mention anything about a device not being found?

Also, you could try booting the newest kernel, but first remove the quiet & splash options...you can do this by highlighting the latest Ubuntu entry, press "e", then highlight your kernel line, press "e" again, remove quiet & splash, press "enter", then press "b" to boot...this is temporary so it won't change your settings, but you might be able to see where the problem is with the newest kernel.

---

### Post by Skia_42 on 2007-09-09
> **confused57 said:**
> You could try booting into an older kernel.  When the busybox error occurs, does it mention anything about a device not being found?

Also, you could try booting the newest kernel, but first remove the quiet & splash options...you can do this by highlighting the latest Ubuntu entry, press "e", then highlight your kernel line, press "e" again, remove quiet & splash, press "enter", then press "b" to boot...this is temporary so it won't change your settings, but you might be able to see where the problem is with the newest kernel.
Thanks for the quick response, I tried 2 kernels and got the same error. After Busybox is shown I see the error:
/bin/sh: can't access th: job control turned off.
I'll try turning of quite&splash

---

### Post by fragos on 2007-09-09
If you installed video card driver like for Nvidia in any way other than using the Ubuntu repository this can happen whenever the kernel is updated.  Problem in that case is that driver must be specifically compiled for the kernel it's used with.

---

