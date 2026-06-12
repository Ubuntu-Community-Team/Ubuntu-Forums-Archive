---
title: "Crash when copying from host drive to Xubuntu user's home drive"
date: 2007-11-17
forum: General Help
---

### Post by daspooky on 2007-11-17
Hello there,

First of all thank you very much for this wonderful product!

I installed Xubuntu Gutsy using **Wubi-7.10-alpha-rev386.exe** on my windows xp laptop succesfully. I'm however experiencing the following problem: when copying (even small files) from the partition containing the wubi installation, my xubuntu freezes. Only a reboot seems to help get the system usable again. More details:

- wubi is installed on the D partition of my laptop
- the C partition contains windows xp

- copying from C to wubi install freezes xubuntu only sometimes
- copying from D (partition containing wubi installation) freezes xubuntu all the time
- my laptop has a SATA drive: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)

Is this a known issue?

---

### Post by ago on 2007-11-19
Yep it's a known issue (that's the main reason why I can't release 7.10 in fact...)

---

### Post by daspooky on 2007-11-19
Okido. Thanks for your response! I will keep using 7.04 in the meantime.

---

