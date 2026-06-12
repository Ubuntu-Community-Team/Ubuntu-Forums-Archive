---
title: "what is livepatch and is it implemented on my system?"
date: 2018-11-29
forum: General Help
---

### Post by ardouronerous on 2018-11-29
I'm running Lubuntu 18.04.1.

I got this message from Software Updater:
[ATTACH=CONFIG]281823[/ATTACH]
What is livepatch? And is it already implemented on my system?

When I click on Settings & Livepatch, there seems to be no additional options for livepatching as I can see.

---

### Post by deadflowr on 2018-11-30
livepatch is an Ubuntu kernel patching system that allows for some patches to be integrated without the need to reboot.
This allows you to keep a system up longer. Reducing downtime, which can be a huge thing for systems that need to be up as much as possible.
[https://wiki.ubuntu.com/Kernel/Livepatch]("https://wiki.ubuntu.com/Kernel/Livepatch")
[https://www.ubuntu.com/livepatch]("https://www.ubuntu.com/livepatch")

Settings (aka software and updates aka software-properties-gtk) should have an option line in the Updates tab for it:
[https://www.omgubuntu.co.uk/2018/04/enable-live-patch-kernel-updates-in-ubuntu-18-04]("https://www.omgubuntu.co.uk/2018/04/enable-live-patch-kernel-updates-in-ubuntu-18-04")

---

### Post by ardouronerous on 2018-11-30
Livepatch option isn't available on mine though
[ATTACH=CONFIG]281827[/ATTACH]

---

### Post by PaulW2U on 2018-11-30
> **ardouronerous said:**
> Livepatch option isn't available on mine though
[ATTACH=CONFIG]281827[/ATTACH]
I don't see it in Xubuntu 18.04 either.

I think the option was disabled for Kubuntu, Lubuntu and Xubuntu as they don't ship with gnome-online-accounts. I'm not sure about Ubuntu Budgie and Ubuntu MATE.

See this bug report: [Hide livepatch widgets in flavors without an online account panel in gnome-control-center]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1770686") and the test case in comment #7.

---

### Post by ardouronerous on 2018-11-30
> **PaulW2U said:**
> I don't see it in Xubuntu 18.04 either.

I think the option was disabled for Kubuntu, Lubuntu and Xubuntu as they don't ship with gnome-online-accounts. I'm not sure about Ubuntu Budgie and Ubuntu MATE.

See this bug report: [Hide livepatch widgets in flavors without an online account panel in gnome-control-center]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1770686") and the test case in comment #7.

Thanks for clarifying this! :)
Merry Christmas.

---

