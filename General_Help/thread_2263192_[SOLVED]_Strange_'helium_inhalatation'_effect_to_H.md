---
title: "[SOLVED] Strange 'helium inhalatation' effect to HDMI output sound in laptop"
date: 2015-01-30
forum: General Help
---

### Post by Nunyah on 2015-01-30
Hey guys!

So I have this laptop where the output sound is completely normal when I use the builtin laptop speakers, but if I connect it to a TV through HDMI, the sound gets distorted in a way that is distinctly similar to how human voices gets distorted when inhaling helium gas  before speaking. Alsamixer tells me I have Intel Haswell HDMI. If it matters, my graphics card is a Nvidia 860M using the 340.65 driver.

I tried googling it but 'helium distorted HDMI output sound' is either a terrible description to this problem or there's just a ton more of people who gets no HDMI output sound. :)

Any ideas?

---

### Post by Impavidus on 2015-01-30
You mean that the high frequencies are to strong in the output? It could result from saturation of the amplifier or DA converter. I don't know about your problem, but maybe this helps you getting more search results.

---

### Post by Nunyah on 2015-01-30
Thank you for your input. I googled some more and came across the exact problem. It appears to be a kernel bug with Haswell drivers.

Adding ```
i915.disable_power_well=0
``` to kernel boot parameter should solve the issue for kernel versions < 3.16.
[http://forums.fedoraforum.org/showthread.php?t=299850](http://forums.fedoraforum.org/showthread.php?t=299850)

But as the bug is fixed in kernel 3.16 I just upgraded to it and the issue has indeed been fixed!
[https://bugs.launchpad.net/system76-driver/+bug/1356507](https://bugs.launchpad.net/system76-driver/+bug/1356507)

For people (like me) who think upgrading kernel versions manually seem a little scary, this article explained the process really well:
[http://www.linuxbsdos.com/2014/12/06/how-to-upgrade-the-linux-mint-17-1-kernel-from-version-3-13-to-3-16/](http://www.linuxbsdos.com/2014/12/06/how-to-upgrade-the-linux-mint-17-1-kernel-from-version-3-13-to-3-16/)

---

