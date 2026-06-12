---
title: "OpenGL broken on Lubuntu 20.04"
date: 2021-09-09
forum: General Help
---

### Post by daisond on 2021-09-09
Hello, some time ago I installed Lubuntu 20.04.02 on notebook Lenovo 3000 N200 with Intel Core2 Duo T8300 2400MHz, 4GB RAM, Nvidia G72M graphics card, 256GB SSD... Linux kernel 5.11.0-27-generic x86_64, LXQt 0.14.1,  X.Org 1.20.11, OpenGL: renderer: NV46 v: 2.1 Mesa 21.0.3 . It was running pretty good all applications even on nouveau graphic card driver. Since Nvidia dropped support of old graphics card drivers for newer Linux kernels, I used what I had. Used SweetHome3D application for drawing some sweet homes :), watching movies, installing updates, etc. Then, one day, I tried to start SweetHome3D application, and it started with weird look in general view window. I tried in terminal glxgears and it was awful view like in attachment. 
Question is: how can I repair this?

---

### Post by guiverc on 2021-09-09
> **daisond said:**
> Hello, some time ago I installed Lubuntu 20.04.02 on notebook Lenovo 3000 N200 with Intel Core2 Duo T8300 2400MHz, 4GB RAM, Nvidia G72M graphics card, 256GB SSD... Linux kernel 5.11.0-27-generic x86_64, LXQt 0.14.1,  X.Org 1.20.11, OpenGL: renderer: NV46 v: 2.1 Mesa 21.0.3 . It was running pretty good all applications even on nouveau graphic card driver. Since Nvidia dropped support of old graphics card drivers for newer Linux kernels, I used what I had. Used SweetHome3D application for drawing some sweet homes :), watching movies, installing updates, etc. Then, one day, I tried to start SweetHome3D application, and it started with weird look in general view window. I tried in terminal glxgears and it was awful view like in attachment. 
Question is: how can I repair this?

The Lubuntu bugs wiki can be found at [https://phab.lubuntu.me/w/bugs/](https://phab.lubuntu.me/w/bugs/)

I suspect your issue though is related to the linux kernel (`linux-hwe-5.11`)

ie. did the issue exist when you were on the older 5.8 kernel?  if not, and it only appeared when your 20.04.2 system upgraded to 20.04.3 (ie. the 5.8 kernel was replaced with the 5.11 one), your issue is with the kernel modules (*drivers*) included with 5.11

The wiki page for all Ubuntu bug reporting can be found at [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

To file the bug, you can use (if you agree with me) `ubuntu-bugs linux-hwe-5.11`.

If that fails; I'd just file it with `ubuntu-bug linux` (ie. file against the linux kernel and let it be changed to HWE post-filing by a bug triager).

Also note:  I suspect your issue will be resolved easiest by switching from the HWE kernel stack, to the GA kernel stack. Ubuntu LTS releases have two stack choices; GA which is supported the life of the release (ie. remain on 5.4), or HWE (hardware-enablement) which upgrades during the first ~two years of life (ie. *5.4 became 5.8, became 5.11, will next move to 5.13 etc*)

To switch to the GA kernel stack (if you agree with me), you can look at [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) and search for "*To downgrade from HWE/OEM to GA kernel:*".  Note: you can have both stacks installed; so I'd install GA, reboot & select it at grub, and only later when completely happy think about removing the HWE stack.  Both stacks can be installed.


Please note:   *I misread your question as how do I report this... thus why I've answered it this way (ie. how to file a bug report about Lubuntu).  I'm tired and just had a QA-test muck up a system I use; so i'm distracted sorry. I mention the repair at the end; ie switching to GA stack*,  *as it's what I believe will fix the issue, but as I misread that detail, I may have missed other key details.*

---

### Post by daisond on 2021-09-10
Thank you, Guiverc, I don't know what was kernel when I just installed it, but I remember one upgrade mentioned kernel.

Yeah, switching to kernel 5.4.0-84-generic did nothing. Same problem.

---

### Post by Yellow Pasque on 2021-09-10
Try a LiveUSB to see if the same thing happens. It could be the GPU failing..

---

