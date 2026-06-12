---
title: "Upgrading kernel gives Xorg gfx glitches?"
date: 2006-12-13
forum: General Help
---

### Post by MWP on 2006-12-13
Hi all,

I need to recompile my kernel to get the latest ipw2200 drivers working.

I tried recompiling the orginal Xubuntu patched kernel source, but that gives errors 1/2 way through "make bzImage".

So, im now trying to get the new 2.6.19 kernel working.
It compiles and boots fine, but X windows has lots of graphics glitches that cant be ignored.

Im using the stock Xubuntu installed "radeon" Xorg driver.

Ive tried with and without DRM enabled in the kernel.
With DRM enabled, X only shows a black screen... without DRM enabled, i get the glitches.

Anyone know what i need to do to get this working properly?
Do i need to recompile the radeon xorg drivers against the new kernel?

Thanks.

---

