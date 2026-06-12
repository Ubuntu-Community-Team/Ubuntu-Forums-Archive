---
title: "First time compile - version question"
date: 2008-02-11
forum: General Help
---

### Post by mgranet on 2008-02-11
I decided to learn how to compile the kernel, so I downloaded the 2.6.22-14 source from the repos. But when I run menuconfig, it shows the version as 2.6.22-9. This is the version that's listed in the makefile. Did I screw something up; is the makefile old; or does it even matter?

Any other advise for a first time kernel compiler also welcome!

---

### Post by mgranet on 2008-02-11
Anyone?

---

### Post by MighMoS on 2008-02-11
I'd be interested in seeing this too, as I've noticed the differences in version numbers between "apt-get source linux-image" and apt-get install linux-source.

Either way you should be fine, but -14 probably contains more miscalanious bug fixes.

---

### Post by MighMoS on 2008-02-11
Also, some advice for a first time kernel compiler: you get extra points if it works on the first try. Don't feel bad if it doesn't boot the first time, and if it does, congrats. Be wary of taking out drivers, and make sure that you have an updated initramfs file for your new kernel when you reboot.

---

### Post by mgranet on 2008-02-12
Well, it worked. The first time. And, against logic and your advice, I gutted the kernel of everything I didn't think I needed.(I learn by breaking). xorg.conf needed to be reset, but that's it.. I think I got off lucky...

It did compile as -9, even though the source directory says -14. Package was **linux-source-2.6.22**. Adept says installed version of the source is the latest -14.51.

Go figure. :confused:

Anyway, thanks for the advice!

---

