---
title: "How do kernel updates happen when you install a mainline kernel?"
date: 2019-01-06
forum: General Help
---

### Post by Mogul345 on 2019-01-06
I recently upgraded my server running Ubuntu 18.04.1 LTS with a new motherboard and a Ryzen 3 2200G CPU. The hardware upgrade went fine, but I found that if I use the kernel that comes w/ 18.04.1 (I think at this time its 4.15.something) I get a bunch of errors constantly in my dmesg logs regarding the GPU, and I was unable to update my motherboard's BIOS to the newest version. Googling the issues indicated that updating to a newer kernel would solve the problem, so following [this]("http://ubuntuhandbook.org/index.php/2018/06/install-linux-kernel-4-17-ubuntu-18-04/") blog post I figured out how to install the 4.20 kernel (which apparently has a bunch of AMDGPU driver updates in it for Ryzen) from the mainline PPA repository. After doing this, the errors went away, and I am happy.

But, being new to this, I am wondering, what happens now regarding kernel updates? Since I'm running the LTS version of Ubuntu, every few weeks it seemed I'd get updates to the 4.15 kernel. So I am wondering:

[LIST=1]
[*]Will the system still notify me about updates with the currently supported kernel in 18.04 LTS?
[*]I assume apt won't tell me about updates to the 4.20 kernel, and I will have to monitor the mainline PPA for updates to the 4.20 kernel?
[*]In the unlikely event that the 4.20 kernel becomes the supported kernel in 18.04, I can switch back to the supported kernel, right?
[/LIST]

---

### Post by deadflowr on 2019-01-07
As long as you have the linux-generic or linux-image-generic and/or linux-headers-generic packages installed you'll get kernel updates.
Remove those to stop getting updates for the regular kernels.

> In the unlikely event that the 4.20 kernel becomes the supported kernel in 18.04, I can switch back to the supported kernel, right?
Not just not unlikely, but should be here in sometime around August through [hardware enablement stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"), currently it's tbd.
I expect the kernel should be at least 4.20 if not higher. It will be whichever kernel is locked down for Ubuntu 19.04.

---

### Post by Mogul345 on 2019-01-07
> **deadflowr said:**
> Not just not unlikely, but should be here in sometime around August through [hardware enablement stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"), currently it's tbd.
I expect the kernel should be at least 4.20 if not higher. It will be whichever kernel is locked down for Ubuntu 19.04.

Cool! TIL. Did not realize that point releases get kernel updates. So in about 8 months when that point release drops (or whenever the LTS kernel overtakes the mainline one I just installed), I just install the package updates as normal, and then do the work to update grub to boot the kernel that comes with the update, and then once it boots remove the mainline kernel I just installed?

---

