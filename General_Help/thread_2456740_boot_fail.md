---
title: "boot fail"
date: 2021-01-18
forum: General Help
---

### Post by yeshua-1 on 2021-01-18
System is 18.04
Has been running for 2 years, logged out as normal yesterday. 
Today it failed to boot as normal but opened the GRUB screen.
First choice is Ubuntu, with Linux 5.4.0-62-generic (Recovery), next choices are two previous kernals with or without recovery.
First 2 choices, runs several lines of boot and after Busybox v1.27.2 it hangs as blinking cursor
Finally on the 3rd option, which is kernal 5.4.0-56 it booted.
Now in Ubuntu as 'normal'.
Would really appreciate any suggestions on how should I look through the system to discover the source of this problem before logging out?

---

### Post by grahammechanical on 2021-01-18
If you can successfully boot into kernel 5.4.0-56 then continue doing so. Wait for an update to fix those possibly faulty kernels. Update/upgrade through the terminal. If you use Software Updater and it brings in a new kernel it might remove the 5.40.0-56 kernel. And if the new kernel is broken then you may not get to a desktop at all.

Are you using a proprietary video driver. Try reverting to the open source video driver.

Regards

---

