---
title: "Ubuntu kernels delete or change the deault kernel"
date: 2022-01-18
forum: General Help
---

### Post by jamesyuan on 2022-01-18
Hi,

I used Ubuntu 20.04 meanwhile I can see 5.13 and 5.11 kernels installed in my laptop. However. 5.13 does not work for my laptop, it always leads me to the Busybox(initramfs).

Therefore, I would like to delete the 5.13 or change the default kernel for booting.  I tried apt-get uninstall and update-grub, however, 5.13 is still in my grub entries. Any suggestions?

---

### Post by &amp;KyT$0P# on 2022-01-18
If the 5.11 kernel still boots normally, you could try switching to the stock 5.4 kernel.  I don't have a system that came with a HWE kernel, so can't check details of the steps involved, so **make sure you verify that every command does what you expect before proceeding** (note that you can replace [FONT=Courier New]sudo apt-get[/FONT] with [FONT=Courier New]apt-get -s[/FONT] to check what it *would* do before actually going ahead).  You could also back up your data first just to be safe.

It would go something like the following:

1) Make sure you're booted into the 5.11 kernel that works.

2) Install the non-HWE kernel -
```
sudo apt-get install linux-generic linux-libc-dev
```

3) Reboot, pulling up the GRUB menu and ensure you boot into the latest 5.4 kernel, that you just installed.

4) If the 5.4 works for you, uninstall the HWE kernel meta-packages -
```
sudo apt-get purge linux*hwe*
```
... then purge all installed HWE kernels, to ensure that the 5.4 kernel you just installed & are now running is the highest version kernel you have installed.

5) Verify that GRUB now boots the latest 5.4 kernel by default.

---

### Post by jamesyuan on 2022-01-18
Hi,

Many thanks for your suggestions,

Howvever, I would like to elaborate my plan, I want to stay with 5.11, howvever, everytime the system will boot with 5.13 kernel, I tried to uninstall  5.13 but it alwasy appear in the grub. Do you have any suggestions?

---

### Post by ActionParsnip on 2022-01-19
What is the output of
```

dpkg -l | grep linux-image

```
Thanks

---

### Post by &amp;KyT$0P# on 2022-01-19
> **jamesyuan said:**
> Howvever, I would like to elaborate my plan, I want to stay with 5.11, 

It's possible, but the problem with keeping the 5.11 kernel long term is that series is no longer updated, so your system may become increasingly vulnerable to known vulnerabilities over time.  Does the 5.4 kernel not work well for you either?

---

### Post by jamesyuan on 2022-01-19
rc  linux-image-5.11.0-27-generic              5.11.0-27.29~20.04.1                            amd64        Signed kernel image generic
rc  linux-image-5.11.0-40-generic              5.11.0-40.44~20.04.2                            amd64        Signed kernel image generic
rc  linux-image-5.11.0-41-generic              5.11.0-41.45~20.04.1                            amd64        Signed kernel image generic
rc  linux-image-5.11.0-43-generic              5.11.0-43.47~20.04.2                            amd64        Signed kernel image generic
rc  linux-image-5.11.0-44-generic              5.11.0-44.48~20.04.2                            amd64        Signed kernel image generic
ii  linux-image-5.11.0-46-generic              5.11.0-46.51~20.04.1                            amd64        Signed kernel image generic
rc  linux-image-5.13.0-25-generic              5.13.0-25.26~20.04.1                            amd64        Signed kernel image generic
rc  linux-image-5.13.0-27-generic              5.13.0-27.29~20.04.1                            amd64        Signed kernel image generic
rc  linux-image-unsigned-5.13.0-25-generic     5.13.0-25.26~20.04.1                            amd64        Linux kernel image for version 5.13.0 on 64 bit x86 SMP
ii  linux-image-unsigned-5.13.0-27-generic     5.13.0-27.29~20.04.1                            amd64        Linux kernel image for version 5.13.0 on 64 bit x86 SMP

---

### Post by jamesyuan on 2022-01-19
> **halogen2 said:**
> It's possible, but the problem with keeping the 5.11 kernel long term is that series is no longer updated, so your system may become increasingly vulnerable to known vulnerabilities over time.  Does the 5.4 kernel not work well for you either?
Hi,

5.4 kernel may not well support CUDA, cuz I am a deep learning practitioner, I really need highly compatiable kernel for Pytorch, Tensorflow, and CUDA.

I think Ubuntu is still maintain 5.11 right?

---

### Post by &amp;KyT$0P# on 2022-01-19
> **jamesyuan said:**
> I think Ubuntu is still maintain 5.11 right?

Unfortunately not.

Ubuntu maintains two "lines" of kernels for LTS releases.  One line sticks to the kernel version series the LTS was initially released with.  The other line, the HWE line, tracks the kernel version of the latest non-LTS releases until the next LTS release, where it then sticks to *that* LTS release's initial kernel version series.  See the graphic [here]("https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle")

---

### Post by jamesyuan on 2022-01-19
thanks, got u.

I think I installed HWE by[COLOR=#333333][FONT=&amp] sudo apt install --install-recommends linux-generic so, I think 5.11 will be updated in case of vulnerability.

BTW, do you have any idea for me to completely delete other kernels, 5.13 is still in grub and I can't find it via apt-get remove[/FONT][/COLOR]

---

### Post by jamesyuan on 2022-01-19
Meanwhile, I saw hwe-support-status --verboseYou are not running a system with a Hardware Enablement Stack. Your system is supported until April 2025.

---

### Post by jamesyuan on 2022-01-19
> **halogen2 said:**
> Unfortunately not.

Ubuntu maintains two "lines" of kernels for LTS releases. One line sticks to the kernel version series the LTS was initially released with. The other line, the HWE line, tracks the kernel version of the latest non-LTS releases until the next LTS release, where it then sticks to *that* LTS release's initial kernel version series. See the graphic [here]("https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle")


May I ask you a little bit more? I found the page which shows 20.04 LTS is supported from 2020 to 2030 with extented security maintenance. Does it say 20.04 with kernel 5.1 or any 20.04.x with any kernels will be supported until 2030?


Thanks for your explanation, HWE and GA are two lines of kernels, they have their supported life. Therefore, I guess the support to 20.04LTS is different to the kernel one right?

---

### Post by jamesyuan on 2022-01-19
> **halogen2 said:**
> Unfortunately not.

Ubuntu maintains two "lines" of kernels for LTS releases.  One line sticks to the kernel version series the LTS was initially released with.  The other line, the HWE line, tracks the kernel version of the latest non-LTS releases until the next LTS release, where it then sticks to *that* LTS release's initial kernel version series.  See the graphic [here]("https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle")


That really hits me. I checked CUDA, it only supoort 5.11 kernel with Ubuntu 20.04 . Meanwhile, 5.11 has ended the life. In addition, my laptop is quite new, some of device requires new kernels.

Do u have any suggestions lol?

BTW, I  see 5.13 and 5.11 in grub, however, I can't delete 5.13 by apt-get remove. 

This is output of dpkg -l | grep linux-image

[COLOR=#000000]rc linux-image-5.11.0-27-generic 5.11.0-27.29~20.04.1 amd64 Signed kernel image generic[/COLOR]
[COLOR=#000000]rc linux-image-5.11.0-40-generic 5.11.0-40.44~20.04.2 amd64 Signed kernel image generic[/COLOR]
[COLOR=#000000]rc linux-image-5.11.0-41-generic 5.11.0-41.45~20.04.1 amd64 Signed kernel image generic[/COLOR]
[COLOR=#000000]rc linux-image-5.11.0-43-generic 5.11.0-43.47~20.04.2 amd64 Signed kernel image generic[/COLOR]
[COLOR=#000000]rc linux-image-5.11.0-44-generic 5.11.0-44.48~20.04.2 amd64 Signed kernel image generic[/COLOR]
[COLOR=#000000]ii linux-image-5.11.0-46-generic 5.11.0-46.51~20.04.1 amd64 Signed kernel image generic[/COLOR]
[COLOR=#000000]rc linux-image-5.13.0-25-generic 5.13.0-25.26~20.04.1 amd64 Signed kernel image generic[/COLOR]
[COLOR=#000000]rc linux-image-5.13.0-27-generic 5.13.0-27.29~20.04.1 amd64 Signed kernel image generic[/COLOR]
[COLOR=#000000]rc linux-image-unsigned-5.13.0-25-generic 5.13.0-25.26~20.04.1 amd64 Linux kernel image for version 5.13.0 on 64 bit x86 SMP[/COLOR]
[COLOR=#000000]ii linux-image-unsigned-5.13.0-27-generic 5.13.0-27.29~20.04.1 amd64 Linux kernel image for version 5.13.0 on 64 bit x86 SMP[/COLOR]

---

### Post by ActionParsnip on 2022-01-20
OK, run:
```

sudo dpkg -P `dpkg -l | grep linux-image | grep ^rc | awk {'print $2'}`

```
This will clean up the config from the removed kernels and may clean up /boot some

---

