---
title: "Nividia driver issue when Ubuntu 18.04 suspends on Aero 15x Gigabyte Laptop"
date: 2019-03-22
forum: General Help
---

### Post by willsut on 2019-03-22
Hello,

I am running Ubuntu 18.04.2 LTS on a Aero 15x Gigabyte Laptop, with a GTX 1070 gpu and have installed Nvidia driver 418.43 (I have also tried older versions). When resuming from suspension I encounter the screen is black with the following errors and I can not access a terminal window must force a shut down with the power button:

[   741.827636] nvidea-nodeset: ERROR: GPU:0: Failed to allocate DMA context
[   741.827636] nvidea-nodeset: ERROR: GPU:0: Notifier DMA allocation failed
[   741.827636] nvidea-nodeset: ERROR: GPU:0: Failed to allocate display engine core DMA push buffer
[   741.827636] nvidea-nodeset: ERROR: GPU:0: Failed to allocate DMA context
[   741.827636] nvidea-nodeset: ERROR: GPU:0: Notifier DMA allocation failed
[   741.827636] nvidea-nodeset: ERROR: GPU:0: Failed to allocate display engine core DMA push buffer

After encountering this I was also getting issues rebooting but overcame these by adding nomodeset to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset". Right now to circumvent the problem I have disabled my computer from suspending when I close the screen but would like to have a proper fix if possible. Does anyone have any insight on this issue? And thanks in advance!

---

