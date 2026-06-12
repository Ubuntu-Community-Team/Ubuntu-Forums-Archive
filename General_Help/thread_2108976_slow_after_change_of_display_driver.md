---
title: "slow after change of display driver"
date: 2013-01-26
forum: General Help
---

### Post by DrScum on 2013-01-26
After serius trouble with the NVIDIA display driver (see thread #2107969) is switched to the open source nouveau driver. Since I switched I find the performance of the machine significantly slower when opening text files and so on. Also there is a long delay after entering the login password before the desktop becomes available for working.

Here my questions: are these symptoms caused by the different driver or is it more likely that I changed settings in the course of dealing with the driver problems?

How can I diagnose and possibly fix the problem?

Thanks for your consideration.

---

### Post by jorok_tupur on 2013-01-27
If you have any problems with Nouveau, it does not work, it is slow, Xv  is not available, or whatever, check the [Troubleshooting Nouveau]("http://nouveau.freedesktop.org/wiki/TroubleShooting") page.

---

### Post by HiImTye on 2013-01-27
Nouveau generally doesn't support hardware acceleration for nVidia cards, so it will be a lot slower than the proprietary ones 99% of the time. even on cards it does support acceleration on, it may not support all features, so it will still likely be slower.

---

### Post by DrScum on 2013-01-28
Thanks for the input. In conclusion it would be either the slower nouveau driver or the NVIDIA driver having serious problems once in a while. If there is another option, I'd be happy to learn about them.

---

