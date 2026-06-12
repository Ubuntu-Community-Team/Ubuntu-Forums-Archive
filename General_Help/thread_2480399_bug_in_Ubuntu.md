---
title: "bug in Ubuntu"
date: 2022-10-28
forum: General Help
---

### Post by zevsua on 2022-10-28
There is such a problem. UPSs are not working. Powercom and East - also.
He began to find out what was the matter. If you enter once a second, the **lsusb** command, then we get the following:
[https://ibb.co/y0nfqMQ](https://ibb.co/y0nfqMQ)


it turns out that he sees UPS in USB, then he does not see.
The output of **sudo dmesg | grep usb** is as follows:
[URL="https://ibb.co/mRG548r"]https://ibb.co/mRG548r
[/URL]

Here we also see the problem.
The fact is that there used to be Ub16 and there were no such problems. Installed 18 - and started. Put 16 again - no problem again.
I began to find out in more detail. It turned out that on the kernel 4.11.12 - UPS work clearly, but as soon as the kernel 4.12-rc3 was installed. Everything. problems began.

What have you done with the kernel since version 4.12? That some UPS are now down??** Would they fix it?**

---

### Post by ian-weisser on 2022-10-28
Kernels 4.11 and 4.12 were not used in releases of Ubuntu.

Ubuntu 16.04 = Linux kernel (base) 4.4 or (HWE) 4.15
Ubuntu 17.04 = Linux kernel 4.10
Ubuntu 17.10 = Linux kernel 4.13

Seems like you have been bisecting kernels to identify the build where the bug first appeared. Keep it up!

Will the Ubuntu Kernel Team patch an old kernel that was never used in a release of Ubuntu? Unlikely.

Will the Ubuntu Kernel Team patch newer kernels that are used in supported releases of Ubuntu? Likely.

---

### Post by zevsua on 2022-10-29
> **ian-weisser said:**
> Kernels 4.11 and 4.12 were not used in releases of Ubuntu.

I found just a specific  place where the changes were made - which is why USB with UPS connected -  doesn't work as it should. AND here what and where was used???
I  will explain in your opinion:). ON Ubuntu 16 - worked clearly. On the  Ubuntu17 - does not work. And I pointed out the cores, simply because I  found a specific place where the bug was added. And by the way, Ubuntu  18 and Ubuntu 20 has the same problem!!! This stretches from kernel 4.12 and so on.  4.13, 4.14, 4.15 .....
So clearer?

> **ian-weisser said:**
> Will the Ubuntu Kernel Team patch newer kernels that are used in supported releases of Ubuntu? Likely.
I'm just in favor. Therefore, he wrote. For that problem stretches from there. Let at least for U18 fix, in the core 4.15 - and then bread

---

### Post by ian-weisser on 2022-10-29
Once your bisection determines when the bug was introduced, please file a bug report.

Do keep in mind that this is not the bug tracker, and that kernel developers are unlikely to see this thread. A proper bug report is how you get the problem addressed by the right people on the Kernel Team.

The fastest way to get the bug addressed is to demonstrate that it still exists in the Ubuntu 22.10 kernel, and also in the Kernel Team PPA testing version. Then you mention that you also happened to discover when it was introduced.

---

