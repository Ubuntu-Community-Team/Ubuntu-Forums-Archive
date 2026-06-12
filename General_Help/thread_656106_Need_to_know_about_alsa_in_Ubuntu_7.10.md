---
title: "Need to know about alsa in Ubuntu 7.10"
date: 2008-01-02
forum: General Help
---

### Post by rakris on 2008-01-02
In ubuntu 7.10 how is the pre-built alsa installed by default? 

Does it come configured in Kernel or is it installed seperately? Please let me know this info. I need this.

---

### Post by fenixartzz on 2008-01-02
alsa comes preinstalled i guess
check synaptic, search for alsa will show you whats installed
if issue is regarding no sound then i installed backport generic package and it worked

---

### Post by danwood76 on 2008-01-02
I think its installed as a kernel module by default, when compiling and installing the latest version the standard alsa install overwrites previous versions.

regards,
Danny

---

### Post by rakris on 2008-01-02
OK thanks. So alsa is kernel module by default in Ubuntu.? 

I just wanted to know this because i am working on some kernel customization...

---

### Post by danwood76 on 2008-01-03
you can see the default kernel config in ubuntu in the /boot dir.
named something like config-kernel-version.
that will show you how the alsa is pre built into the kernel for sure.

regards,
Danny

---

