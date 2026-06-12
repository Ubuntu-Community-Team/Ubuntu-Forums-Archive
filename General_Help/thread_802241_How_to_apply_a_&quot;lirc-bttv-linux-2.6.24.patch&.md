---
title: "How to apply a &quot;lirc-bttv-linux-2.6.24.patch&quot;"
date: 2008-05-21
forum: General Help
---

### Post by BXCracer on 2008-05-21
Hello
I need help applying a patch, it gives you the ability to use lirc_gpio drivers with 2.6.24 kernel. Discusions about it:

[http://sourceforge.net/mailarchive/message.php?msg_id=20080203211219.d5060925.ldarby%40tuffmail.com](http://sourceforge.net/mailarchive/message.php?msg_id=20080203211219.d5060925.ldarby%40tuffmail.com)

Patch:
[http://lirc.sourceforge.net/software/snapshots/lirc-bttv-linux-2.6.24.patch](http://lirc.sourceforge.net/software/snapshots/lirc-bttv-linux-2.6.24.patch)

Any help about how to apply it will be appreciated

---

### Post by danwood76 on 2008-05-21
You need to get the kernel source (available through synaptic) and the related build tools, then use the patch command to patch the source tree.
Im not 100% sure if this will pacth the ubuntu pre patched kernel source so you may need to patch a vanilla kernel from kernel.org.

Then compile the kernel and install.

Compile instructions can be found here:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by BXCracer on 2008-05-21
thanks

---

### Post by BXCracer on 2008-05-21
> **danwood76 said:**
> You need to get the kernel source (available through synaptic) and the related build tools, then use the patch command to patch the source tree.
Im not 100% sure if this will pacth the ubuntu pre patched kernel source so you may need to patch a vanilla kernel from kernel.org.

Then compile the kernel and install.

Compile instructions can be found here:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

And if its patches the ubuntu pre patched kernel then i wont need to compile kernel at all? Or still the ubuntu one ?

---

