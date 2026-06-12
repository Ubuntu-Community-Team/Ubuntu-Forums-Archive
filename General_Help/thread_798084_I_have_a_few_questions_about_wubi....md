---
title: "I have a few questions about wubi..."
date: 2008-05-17
forum: General Help
---

### Post by Sega dude on 2008-05-17
Hi! I have been using ubuntu on my gateway 6022GZ laptop via wubi and I LOVE IT! Here are my questions. 

1. Can I upgrade from 7.04 to 7.10 using the software update?

I want to install ubuntu on my Dell Dimension 4300s. But I have a concern. Back when I couldn't get my broadcom to work I wanted to try the wireless USB adaptor that I use for that pc. I plugged it in and a got a CPU lockup error. So I rebooted and the dual-boot was gone. When my laptop loaded XP it would blue screen almost instantly. I had to restore the laptop. I don't want that to happen with my Dell. I use it as my gaming pc and I don't to lose all my games. 2. Do you think that will happen?

3. Will a USB wireless adaptor even work in the first place?
4. Is there a driver for the NVIDIA Geforce 5550?

---

### Post by ago on 2008-05-18
> **Sega dude said:**
> Hi! I have been using ubuntu on my gateway 6022GZ laptop via wubi and I LOVE IT! Here are my questions. 

1. Can I upgrade from 7.04 to 7.10 using the software update?
No

> 2. Do you think that will happen?
That most likely was due to a hard reboot. Use chkdsk /r to fix it from windows (also available via windows CD rescue console). You can avoid hard reboots using [https://wiki.ubuntu.com/WubiGuide#head-3daaf6dbfcade2cd0a9b85b8ca00590ecb91426a](https://wiki.ubuntu.com/WubiGuide#head-3daaf6dbfcade2cd0a9b85b8ca00590ecb91426a)

> Will a USB wireless adaptor even work in the first place?
It should, but it depends on your model. No harm in trying I guess

> Is there a driver for the NVIDIA Geforce 5550?
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

---

### Post by Sega dude on 2008-05-18
If I want to upgrade to 7.10 do I have to uninstall wubi and then get a 7.10 iso and reinstall? Do I really have to upgrade anyways? I'm going to install ubuntu on the dell now. I'll tell you how it goes later. Thanks ago!

---

### Post by ago on 2008-05-18
> **Sega dude said:**
> If I want to upgrade to 7.10 do I have to uninstall wubi and then get a 7.10 iso and reinstall?
Yes, but once you are there you can use 8.04

> Do I really have to upgrade anyways?
No, you need DIST-upgrades only if you want newer versions of the various apps
Upgrades (same version) are always a good idea though since they may fix security vulnerabilities

---

### Post by abn91c on 2008-05-18
[QUOTE=Sega dude;4983361]Hi! I have been using ubuntu on my gateway 6022GZ laptop via wubi and I LOVE IT! Here are my questions. 

1. Can I upgrade from 7.04 to 7.10 using the software update?

Yes you can, you have to update your software repositories and reload them. you will see a new option to upgrade, go here for more info and directions [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by ago on 2008-05-19
hmm no, that will not work too well on wubi 7.04
dist-upgrades work from 7.10 onward

---

### Post by abn91c on 2008-05-20
> **ago said:**
> hmm no, that will not work too well on wubi 7.04
dist-upgrades work from 7.10 onward

not true, that is what ubuntu website recommends and that is how i upgraded my wubi install on my dell desktop, he just needs to update the repositories in adept-manager go to the updates tab and check the top 3 boxes then reload. see attached photo. I am using kubuntu  but the process is the same for ubuntu

---

### Post by ago on 2008-05-21
you can dist-upgrade ubuntu (any version) but not wubi (at least for 7.04), unless you migrated to a real partition before.

---

### Post by abn91c on 2008-05-21
> **ago said:**
> you can dist-upgrade ubuntu (any version) but not wubi (at least for 7.04), unless you migrated to a real partition before.

Dude, with wubi install you have the full functionality of ubuntu/kubuntu etc for all updates including dist-upgrade.IT DOES NOT matter how you installed

---

