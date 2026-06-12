---
title: "Zenbook dual boot"
date: 2023-09-10
forum: General Help
---

### Post by capemayal on 2023-09-10
I have windows 11 and have dual booted back as far as 16.04. 

 But have not been able to install on this laptop.  It's an Intel I-5, plenty of ram and SSH.  I can install 22.04 But prefer 16.04. 

 I have not any problems with 16.04. When trying to install 16.04 it only goes so far and the screen fonts become very large then stops.  I must then do a hard reset.

I have disabled fast boot, secure boot.  The laptop does have uefi.  I don't know if I can disable it if that would be necessary.

Thanks
Al

---

### Post by Rubi1200 on 2023-09-10
16.04 reached end of life more than 2 years ago. Running it puts your system at serious risk and is not recommended at all.

Please post the full system specs. so we can get a better idea of what might be going on, especially graphic card.

Have you tried first running a liveUSB session to see if everything functions?

Perhaps something lighter, like Lubuntu or Xubuntu is also worth considering.

---

### Post by oldfred on 2023-09-10
Also distribution needs to be newer to have updated kernel & drivers for new hardware, often a year newer to have everything.
Many new systems after about 2020 are UEFI only, no CSM/Legacy/BIOS boot mode at all.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Lenovo announced all 2020 products will be UEFI only (UEFI Class 3 or no CSM).
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)
My Dell with Intel gen 11 chip also is UEFI only and 22.04 installed without issue, even with Secure boot on. But Windows 11 fast boot & bitlocker had to be off.

Is it the gui that you like?
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

[https://ubuntuunity.org/blog/ubuntu-unity-22.04/](https://ubuntuunity.org/blog/ubuntu-unity-22.04/)

I changed to flashback (more like old gnome2) when Ubuntu changed to Unity. And then more recently changed to Kubuntu.
Unity was a separate unoffical gui for a while but with 22.10, it became an official flavor.

---

### Post by capemayal on 2023-09-10
Thank you both for your replies. I have I-5, 8gb ram & 512mb ssd.

---

