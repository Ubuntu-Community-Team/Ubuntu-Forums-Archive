---
title: "[SOLVED] CONFIG_FB_VESA help"
date: 2007-02-27
forum: General Help
---

### Post by unebaguettesvp on 2007-02-27
i apologize in advance. i am a total linux newbie.

running this in a terminal:

grep CONFIG_FB_VESA /boot/config-$(uname -r)

gives me this:

CONFIG_FB_VESA=m

i need it to say:

CONFIG_FB_VESA=y

how do i do that? this is related to installing splashy. i am running 6.10 with AMD 64 architecture.

thanks in advance!!!

---

### Post by erkki70 on 2007-02-27
Hi,
You need to recompile your kernel and add vesa support as built-in not module as it is now.
To recompile you can follow this guide:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
It takes some time to do it but it's an advantage to have a custom kernel as it can make your box faster...
Good luck!

Cheers,

---

