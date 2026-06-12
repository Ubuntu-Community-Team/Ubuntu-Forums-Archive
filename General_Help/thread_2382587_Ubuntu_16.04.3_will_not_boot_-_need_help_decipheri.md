---
title: "Ubuntu 16.04.3 will not boot - need help deciphering error"
date: 2018-01-15
forum: General Help
---

### Post by verymadpip on 2018-01-15
Hi everybody.
I went to boot my Ubuntu 16.04.3 install a day or two ago & got the following error message, which I can't make heads or tails of.
Sorry it's a photo, but it seemed like the easiest way of grabbing the whole thing

Rig specs:[ATTACH=CONFIG]278204[/ATTACH]
Sabertooth Z77 mobo
Nvidia GTX760 GPU
i52500k CPU
8Gb RAM

It's a dual boot with Win 7 on seperate HDDs.  Ubuntu occupies a partition on a HDD with the second partition being NTFS shared data.
The data is accessible from Win as it always has been.
The HDD is pretty old & I was going to replace it when 18.04.1 is released anyway (& rejig a couple of other HDDs too).

Any help/insight greatly appreciated.

---

### Post by Impavidus on 2018-01-15
There has been a faulty kernel upgrade on 16.04 a couple of days ago. Maybe that's it. Can you use the grub menu to boot an older kernel? If so, try to install all available updates. That may fix it.

---

### Post by verymadpip on 2018-01-16
Hi Impavidus.
That's worked a treat.
I was able to boot the 104 kernel & do an update, normal boot resumed thereafter.
Thanks very much :)

---

