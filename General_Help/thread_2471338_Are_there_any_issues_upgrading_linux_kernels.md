---
title: "Are there any issues upgrading linux kernels?"
date: 2022-01-27
forum: General Help
---

### Post by username2758 on 2022-01-27
Well I just recently purchased a new laptop with the AMD Ryzen 5 5500u APU and noticed incompatibility between current version of linux kernels and video drivers.


Found out that Ubtuntu 20.04 has kernel 5.8 whereas Ryzen 5500u requires kernel 5.10+, so I upgraded the kernel version using mainline software.


My question is are there any issues doing linux kernel upgrades?

---

### Post by schragge on 2022-01-27
> **username2758 said:**
> Found out that Ubuntu 20.04 has kernel 5.8
That was true for Ubuntu 20.04.02 LTS. Ubuntu 20.04.03 LTS provided kernel 5.11. Currently, there's kernel 5.13 in **linux-generic-hwe-20.04-edge**. See [https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle](https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle)

---

### Post by mastablasta on 2022-01-27
no. you just upgrade the HWE (hardware enablement) kernel. it is there for precisely this reason.

mine was 4.18 (or wa sit 4.15?!) before, but i bought a "new" CPU ryzen 5 3600, so i had to load HWE Kernel to get version 5.4 

more info here: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by username2758 on 2022-01-27
Thank you for the info.

I didn't try Ubuntu on this laptop yet, but tried Mint and upgraded to kernel version 5.16.2 and video driver is working fine now.

May I ask why do Linux distros take so long to implement newer kernel releases into their products?

---

### Post by Impavidus on 2022-01-27
The kernel version for each release of Ubuntu is frozen a short time before release date. That provides stability. Newer kernels occasionally break things. Important bugfixes get backported.

On the latest Ubuntu release, 21.10, released October 2021, you get kernel 5.13, which should be good enough for your. After 21.10 was released, this kernel was also made available on 20.04 through the linux-generic-20.04-hwe-edge package. With the end of life of 21.04, support for 5.11 was dropped and all users of that kernel were automatically upgraded to 5.13. The 20.04.4 live disk image with 5.13 will be released soon, but you can still use the 20.04.3 live disk with kernel 5.11, which will be upgraded to 5.13 right after installation.

---

