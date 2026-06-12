---
title: "Lunar kernel on Jammy"
date: 2023-04-25
forum: General Help
---

### Post by bimblesticks on 2023-04-25
Hello,

There are a couple features in Linux 6.2 that I'd like to have on Jammy, but I don't want to install an unsigned mainline kernel or upgrade to Lunar. I know the kernel will trickle down via HWE in August, but I'm looking to install it sooner. I checked the package [linux-image-generic-hwe-22.04-edge]("https://packages.ubuntu.com/eo/jammy-updates/linux-image-generic-hwe-22.04-edge"), which gets newer kernels before the regular HWE package, but it appears this is still 5.19. Does anyone know when this package will get the bump to 6.2?

Does anyone have any other methods for getting the Lunar kernel on Jammy?

Thanks

---

### Post by mendres82 on 2023-04-26
Based on [this]("https://ubuntu.com//blog/canonical-livepatch-gets-even-better-now-supporting-hardware-enablement-kernels") article, the 6.2 kernel will be available in july. I only know the two options you already mentioned.

---

### Post by Impavidus on 2023-04-26
Normally, the hwe kernel would jump to a new version just before 22.10 reaches end of life, and the edge kernel would jump just after the release of 23.04. Which was 6 days ago, so it shouldn't take much longer.

---

