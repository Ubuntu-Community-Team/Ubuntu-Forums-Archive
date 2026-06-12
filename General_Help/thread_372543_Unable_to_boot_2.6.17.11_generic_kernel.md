---
title: "Unable to boot 2.6.17.11 generic kernel"
date: 2007-02-28
forum: General Help
---

### Post by EvilRusk on 2007-02-28
Hello

First let me outline my system briefly:

I have an AMD64 3200 cpu based system and was previously using a clean install 6.06 version of ubuntu. I upgraded this system to 6.10 using synaptic, without a 6.10 cd. Like many people I was initially confused by the lack of a k7/686 kernel but understand the generic kernel to be acceptable as an alternative.

On the boot menu for ubuntu I am presented with an option to boot either the 2.6.17.11-386 or 2.6.17.11-generic kernels in normal or recovery mode as well as an older k7 kernel from my 6.06 installation.

By default my system boots into the .11-386 kernel and all is fine, but I would really like to be able to use the generic kernel. If I attempt to boot the generic kernel, the boot hangs quite early on with a message:

> [17179576.268000] ACPI: Getting cpuindex for acpiid 0x1

and a blinking cursor. If I boot the generic (recovery mode) kernel it gets slightly further and stops at "loading root filesystem" or something similar I forget exactly what.

Does anyone have any ideas what might be preventing my system from booting the generic kernel whilst the 386 kernel works fine? With 6.06 I did not have a problem with using either the 386 or k7 kernel from the ubuntu repository.

---

### Post by Malakia on 2007-02-28
Read this thread it might be able to help you, if not let us know and maybe we can figure it out.

[http://ubuntuforums.org/showthread.php?t=261586](http://ubuntuforums.org/showthread.php?t=261586)

---

