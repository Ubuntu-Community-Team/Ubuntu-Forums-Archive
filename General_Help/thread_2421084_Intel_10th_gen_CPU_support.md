---
title: "Intel 10th gen CPU support?"
date: 2019-06-16
forum: General Help
---

### Post by ProDigit on 2019-06-16
What will be the first version of Ubuntu supporting intel 10th gen CPUs?
Or will older versions of Ubuntu (with Kernel 4.x) support this CPU as well?

---

### Post by CatKiller on 2019-06-16
I'm pretty sure that Intel got support into the 5.0 kernel, so 19.04 and onwards. I'd imagine that it will come to 18.04 via the Hardware Enablement Stack, probably with 18.04.3.

---

### Post by Doug S on 2019-06-17
I think, but am not certain, the Intel marketing name for the 10th gen is "IceLake". I am still seeing upstream commits as recently as today continuing to add support for "more Icelake platforms". (Note that I am only on 1 of about 200 upstream e-mail lists). At best, a patch set submitted today would be in kernel 5.3, which is about 2 or 3 months out.

---

### Post by ProDigit on 2019-11-30
Thanks for the thoughts.
5 months later, and Linux kernel 5 is available also on 18.04.

---

### Post by Doug S on 2019-11-30
> **ProDigit said:**
> Thanks for the thoughts.
5 months later, and Linux kernel 5 is available also on 18.04.You didn't mention if your 10th gen processor now works with Ubuntu or not? If not try the [latest mainline kernel, 5.4.1]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4.1/")

---

