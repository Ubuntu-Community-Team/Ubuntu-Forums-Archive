---
title: "Lubuntu"
date: 2022-07-01
forum: General Help
---

### Post by geordiejohn on 2022-07-01
Hello I have burnt Lubuntu 18.04 to a cd but before I install it on my 32 bit laptop is there a 19.04 version please? 
Thank you.

---

### Post by yancek on 2022-07-01
The latest release which supports 32bit is 18.10, the latest release which supports only 64bit is 22.04.

---

### Post by geordiejohn on 2022-07-01
Thank you.

---

### Post by guiverc on 2022-07-01
Lubuntu 18.04 LTS is no longer supported; refer [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/) or [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/) where you'll note only Ubuntu Server, Ubuntu Desktop & Ubuntu Cloud come with 5 years of support; *flavors such as Lubuntu* had shorter lives.

I'd suggest using `ubuntu-support-status` to assess the security status of your actual install.

Lubuntu 18.10 was available, but being a non-LTS its [support ended 9 months after release]("https://fridge.ubuntu.com/2019/07/19/ubuntu-18-10-cosmic-cuttlefish-end-of-life-reached-on-july-18-2019/"). Installs could be forced to upgrade to Lubuntu 19.04.

Lubuntu 19.04 was available in the *alpha *stages (*as ISO for install*); and installs received upgrades for the life of that release; but it's [EOL now too]("https://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/").

Both 18.10 & 19.04 (*or in fact all releases beyond 18.04 of Lubuntu*) use the more modern LXQt desktop, and upgrades from LXDE releases to LXQt were only supported via re-install.

The last *i386* release supported was Lubuntu 18.04 LTS which ended its support in April 2021, three years after its release.  You can use `ubuntu-support-status` to see what portions of the 18.04 product are still receiving security fixes (ie. no LXDE packages; only packages that are in common with Ubuntu Desktop 18.04 LTS still receive fixes).

If you want more information; I wrote about it [here]("https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/4") on Lubuntu's discourse site.

I know where 18.10 is available, but I don't believe 19.04 is available online (*I've still got it on a thumb-drive, but that was only because I didn't re-use the thumb-drive as I only used it for i386 non-LTS images of Lubuntu & 19.04 was the last*).

---

