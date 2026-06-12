---
title: "Firmware update to kernel 5.13.0-23-lowlatency stalled my system"
date: 2022-01-04
forum: General Help
---

### Post by eloctogono on 2022-01-04
Hi everyone!

I just updated the kernel through the **Ubuntu Studio 21.10 Update Manager from 5.13.0-22-lowlatency to 5.13.0-23-lowlatency**. After the update, the system becomes extremely slow at startup and general use like opening the apps menu, the tskbar, etc. It takes around 30 seconds for every action. I'm currently booting with the previous version of the Kernel but wanted to share the issue and maybe get a workaround. Thanks !

---

### Post by rattskjelke on 2022-01-04
Do you have a AMD processor or graphics?
This morning a kernel or linux-firmware update from Ubuntu broke my Linux Mint 20.2 installation but only when using kernel 5.13.
As far as I can tell it only affects AMD.
I had no problems on 5.11 or 5.4 kernels. You might have to go back to one of those until they fix it.

---

### Post by eloctogono on 2022-01-04
Yes! I have a AMD Ryzen. That's exactly my situation. Thanks!

---

### Post by rattskjelke on 2022-01-04
> **eloctogono said:**
> Yes! I have a AMD Ryzen. That's exactly my situation. Thanks!
Mine is also a Ryzen with onboard graphics.
It's probably the same problem as this.
[https://forums.linuxmint.com/viewtopic.php?f=46&t=364729](https://forums.linuxmint.com/viewtopic.php?f=46&t=364729)
I messed around all afternoon trying different grub settings but nothing worked.
I think the only way to fix it is roll back the kernel to the previous version of 5.13 which is probably not a good idea because there  were several security patches or use the latest 5.11 or 5.4 kernel. Both of those worked for me.

---

### Post by eloctogono on 2022-01-04
Yes, that seems to be the same issue. I also noticed now that Youtube videos suffer from heavy (and quite annoying) horizontal tearing, even if I use the previous working Kernel version, something that didn't happen yesterday for sure... :'(

---

### Post by benighted8393 on 2022-01-08
Similar problems on an Acer A515 laptop with 5.13.0-23-generic: Only fix is to go back to 5.13.0-22...

---

