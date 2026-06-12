---
title: "Nvidia Geforce GTX 550 Ti - doesnt work (20.04)?"
date: 2020-06-20
forum: General Help
---

### Post by aquascrotum on 2020-06-20
I have a clean install of 20.04 on an old Dell workstation with a Nvidia Geforce GTX 550 Ti.  There is no onboard graphics.

Graphics were fine during the installation, however after booting to the installed version I initially could only get 600x800 4:3.

I changed the driver to X.Org Nouveau with no change and followed the advice at another thread on here install a proprietary driver but best result so far is 1024x768 and again limited to 4:3.

Device information shows graphics as llvmpipe.  This is my first liaison back with Ubuntu after a 5 yr hiatus back to Win 10 after I just got tired of this kind of thing...I was lead to believe this kind of stuff was sorted out of the box now!

Can anyone lend advice on a fix?  Any advice appreciated

---

### Post by CelticWarrior on 2020-06-20
> Device information shows graphics as llvmpipe.

This means you AREN'T using the Nvidia drivers.
A Nvidia Geforce GTX550ti is currently supported by the 390 driver version only.
If your "old Dell workstation" is new enough to have UEFI instead of BIOS then OSes should be installed in that mode but also, for convenience, Secure Boot should be disabled as it prevents unsigned drivers from loading even when correctly installed.

---

### Post by aquascrotum on 2020-06-20
> **CelticWarrior said:**
> This means you AREN'T using the Nvidia drivers.
A Nvidia Geforce GTX550ti is currently supported by the 390 driver version only.
If your "old Dell workstation" is new enough to have UEFI instead of BIOS then OSes should be installed in that mode but also, for convenience, Secure Boot should be disabled as it prevents unsigned drivers from loading even when correctly installed.

Thanks for the reply! Workstation is a Precision T3500 which I understand doesnt have UEFI.

When I go to software and updates (previous driver version used before I started playing with it was -440), the currently selected option is "Continue using a manually installed driver".  I'm unable to select the other proprietary driver options though I do see -390 listed.  How can I revert to a different driver?

---

### Post by CelticWarrior on 2020-06-20
```
sudo apt-get purge nvidia*
```
Reboot and try again.

---

### Post by aquascrotum on 2020-06-20
Had to revert to a fresh install as removing the drivers somehow caused failure to boot, but now running smoothly on 390 drivers.

Why is Ubuntu recommending -440 if people know that this version isn't supported by that driver?

---

### Post by Yellow Pasque on 2020-06-21
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1874874](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1874874)

---

