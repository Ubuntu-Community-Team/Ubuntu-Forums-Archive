---
title: "Help with Kernels?"
date: 2018-05-29
forum: General Help
---

### Post by sunnyard5666 on 2018-05-29
I have 16.04 and it updates Linux 04.04 and 04.10 and 04.13.  Can I delete the others? - I presume 04.13 is the newest?

Thanks!

---

### Post by deadflowr on 2018-05-29
It should be able to update 2 kernels, 4.4 and 4.13.
4.10 has no meta package to get updated with.
What you should do is open a terminal andrun
```
sudo apt autoremove --purge
```
then remove the packages linux-generic linux-image-generic linux-headers-generic
```
sudo apt purge linux-generic linux-image-generic linux-headers-generic
```
Those apply for the 4.4 kernels.
it should keep you at the 4.13 kernels.
You should have the linux-generic-hwe-16.04 packages, which correspond to the 4.13 kernels.
[What is HWE?]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

(apt autoremove should leave you with only 2 kernels, the newest and the second newest; the --purge option adds the benefit of also removing leftover crud that autoremove will not touch.)


After that you can research multiple ways to remove kernels as you go.
Some tips here:
[https://help.ubuntu.com/community/RemoveOldKernels]("https://help.ubuntu.com/community/RemoveOldKernels")

I'm sure if you wait, others will post of their own ways of cleaning out them old kernels.

Hope it helps

---

### Post by raleigh3 on 2018-05-29
I use UKUU. Ubuntu Kernel Update Utility

It uses a GUI and it will show you which kernels are running and those that are installed.

You can manually remove kernels or you can use purge which removes all kernels except the current one running.

I strongly recommend having at least 2 kernels because I have had cases where a new kernel would not boot up.(kernel panic)

---

