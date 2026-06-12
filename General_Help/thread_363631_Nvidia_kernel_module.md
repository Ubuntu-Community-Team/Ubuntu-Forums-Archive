---
title: "Nvidia kernel module"
date: 2007-02-17
forum: General Help
---

### Post by meanmrmustard on 2007-02-17
I just ran the update mgr and it broke X and beryl.  After reconfiguring and getting X running again,  beryl manager is running but there are no effects, I found dmesg telling me that the kernel module was a different version than the client had installed.

The message was:

[17180585.960000] NVRM: API mismatch: the client has the version 1.0-9746, but
[17180585.960000] NVRM: this kernel module has the version 1.0-8776.  Please
[17180585.960000] NVRM: make sure that this kernel module and all NVIDIA driver
[17180585.960000] NVRM: components have the same version.

I believe this is telling me that the newest nvidia driver is installed but the kernel module is wrong.
How do I update the kernel module to match the nvidia driver?... or have I got it wrong?

---

### Post by highneko on 2007-02-17
I had the same or similar problem. You can get into a terminal and upgrade to fix(sudo apt-get update; sudo apt-get dist-upgrade). Or maybe use grub to select the old kernel?

---

### Post by meanmrmustard on 2007-02-17
Well.... dist-upgrade didn't add anything new.

I'd rather upgrade the module than downgrade the kernel.

---

### Post by meanmrmustard on 2007-02-18
> **meanmrmustard said:**
> I just ran the update mgr and it broke X and beryl.  After reconfiguring and getting X running again,  beryl manager is running but there are no effects, I found dmesg telling me that the kernel module was a different version than the client had installed.

The message was:

[17180585.960000] NVRM: API mismatch: the client has the version 1.0-9746, but
[17180585.960000] NVRM: this kernel module has the version 1.0-8776.  Please
[17180585.960000] NVRM: make sure that this kernel module and all NVIDIA driver
[17180585.960000] NVRM: components have the same version.

I believe this is telling me that the newest nvidia driver is installed but the kernel module is wrong.
How do I update the kernel module to match the nvidia driver?... or have I got it wrong?

Well I finally gave up and reverted to the -10 kernel which got beryl running again but there's no window decorations now. Grab bar, minimize, close, etc.

What now?

---

### Post by highneko on 2007-02-18
Usually when you don't have the borders it's because the xorg was edited by something and you have to re-add stuff.
[http://wiki.beryl-project.org/wiki/Main_Page](http://wiki.beryl-project.org/wiki/Main_Page)

Sorry I wasn't any help last time, maybe it's because you don't use the nvidia-glx package like I do. You manually installed the nvidia driver maybe?

---

### Post by meanmrmustard on 2007-02-19
Unfortunately, those tips didn't do the trick either.

---

