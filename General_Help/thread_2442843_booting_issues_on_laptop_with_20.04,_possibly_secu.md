---
title: "booting issues on laptop with 20.04, possibly secure boot related"
date: 2020-05-08
forum: General Help
---

### Post by s-chrzs-q on 2020-05-08
Morning all, so ever since i performed the 20.04 upgrade on my alienware m15r3, I've encountered a weird issue. It wont boot normally. The only way to boot, is go into bios, and change secure boot to the opposite to what it is. 

Thats right, if it worked on secure boot enabled before, next time it needs to be disabled, and so on and so forth. Otherwise just after selecting Ubuntu on grub, it either goes blank screen (so im assuming some issue with loading nvidia drivers/fb?) or locks up and laptop starts heating up. I've tried to enable/disable secure boot in the OS once im in, sometimes nvidia drivers wont load because of secure boot and unsigned keys, other times everything i fine and i can use my laptop normally.

I figured maybe I did a bad upgrade, okay so ill reinstall, and first boot on new install? same problem, so here I am. Anyone have any ideas on what I can try? Otherwise im just going to have to put 19.10 back on, but rather see if this can be fixed first. 

Cheers all.

---

### Post by dino99 on 2020-05-08
Check that the shim/shim-signed  package is installed   [https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)

---

### Post by s-chrzs-q on 2020-05-08
Yeah theyre both installed. This happened on a fresh install as well, so would hope they came as standard if they helped. Need some logs, see whats up.

---

### Post by s-chrzs-q on 2020-05-08
Right, so I believe its solved now. Whilst secure boot is enabled you have access to secure boot keys, now before this release Ubuntu didnt seem to care about previously enrolled keys (With secure boot off, it always worked), this one seems to ignore secure boot somehow. So i cleared all the enrolled keys, disabled secure boot and its now working as expected. Screenshot included for any future sufferers of this. 

[IMG]https://lh3.googleusercontent.com/hqkgFxQ4qWZxuqJhHsrkjpiUdEHUikLGMOu3yeDuSI0fML6etOUwPLEHgE5YHCpZTTVIysFv6_qgpKlLrFyoB7SirkkV8i4tL4d2GoHyR9g1y6byW_KS_WO3AOx3LYm9Nkp7XKeiaQkRynyrrQ5jJLJEQMbQlJh2Qg_F4Qlng0wupvJuOKcWACKY5iA1TCsTASVFdi6aMrY-AOKloI0v30QxEs9CQPYlFwkvY2xwkvinrOg2r4FAZsZxg5zOsbCSSrHuJlq4d0rLqnb8Ne1yz_i7DuPQacBUgyj3sGRaa73aLwdG_nalP3vMsiWC-HxLN6EYi5dOSUzy6Qf8Vt5985NwUFeDFUirOevK38LRsBF47ddbmWbM2RyWNazCsxGKTjZYX6ydU6DFLsu4fj2to2VSnS9Zr9m1OsYRi3zj897BCiGFDsyjaY-BD1Hd8N3etAc646zs_D-itcL5FetRgACE2A1xTY58sb4gPrjk8Wy1t9NHU3zHXxsFl377mnHPGQgRcE70Xa51_NHk7UqJ35beNiljREZmIjO7SwIBRkRI9hX6stbzReHLaXBvdAByKF2C3qDOcfONI3tO0ZWECecZTeDt9lHOJFOueUp6STYLaOJRTwzQT06AHRtehX9S0ROxM5CJBEoKtf_sDqAr9VLyyp1SH5Ow8LKtSacpQ-kMwyFD3p3_X6OAaP_1UQ=w1135-h851-no?authuser=0[/IMG]

---

### Post by s-chrzs-q on 2020-05-09
Okay this happened again, I also this time disabled my laptops 'TPM' in the bios. Also seems to have helped

---

