---
title: "Intel® Haswell Mobile causing system to freeze after suspend"
date: 2015-07-03
forum: General Help
---

### Post by sn0m on 2015-07-03
Hello
I bought a new laptop, it is a Lenovo Z50-70.
It had intel all over, so I thought it would ok with linux so installed Ubuntu 14.04, no problems there.
However I found out that the system freezes up after suspend and apparently this is quite a common problem with Intel® Haswell Mobile graphic card, which I found out that it is not just intel, it also has a nvidia in it.
I've tried changing the graphic driver to NVIDIA binary drivers, both the proprietary tested and the one untested with updates but no luck. Even worse, the system freezes at random with those drivers not just after suspending, so I reversed back to the xorg driver (nouveou one).
I have submitted the bugs to Ubuntu to look at but I was wondering if any of you has found out any work around.
Many thanks
Sokol

---

### Post by sn0m on 2015-07-08
Found a work aroundish so far. Go to BIOS and change Video card from Discrete to UMA only. This forces the system to use Intel VGA only and suspension works fine. I guess I have to check the NVIDIA over with every major update, till then no fancy graphics for me.

---

