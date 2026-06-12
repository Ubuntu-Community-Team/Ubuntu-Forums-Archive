---
title: "What is loaded as default?"
date: 2008-04-06
forum: General Help
---

### Post by Old_Grey_Wolf on 2008-04-06
Is Windows or Ubuntu loaded as default by the boot loader?

---

### Post by SunnyRabbiera on 2008-04-06
depends, mostly though ubuntu boots by default.

---

### Post by opossumjack on 2008-04-06
You can choose it... 
I think Linux is loaded by default...

You can edit **/boot/grub/****menu.lst **to choose the default OS loaded by the bootloader...

Hope it will help :)

---

### Post by Bruce M. on 2008-04-06
> **Old_Gray_Wolf said:**
> Is Windows or Ubuntu loaded as default by the boot loader?

Windows is on your machine and then you install Ubuntu.
"Grub" will load Ubuntu by default, but it can be edited so Windows is the default.

Grub (by default) gives you 10 seconds to make the change to load Windows if you wish.

---

### Post by Old_Grey_Wolf on 2008-04-06
I thought it would probably be Ubuntu. Thats the default for a traditional install of Grub. However, I thought that Wubi may be modifying the Windows boot loader and have Window as the default.

If I have to explain to a potential Linux user about modifying the boot loader to make Windows the default, they may not want to try it :(

---

### Post by Bruce M. on 2008-04-06
> **Old_Gray_Wolf said:**
> I thought it would probably be Ubuntu. Thats the default for a traditional install of Grub. However, I thought that Wubi may be modifying the Windows boot loader and have Window as the default.

If I have to explain to a potential Linux user about modifying the boot loader to make Windows the default, they may not want to try it :(

If you use Wubi, it's NOT a problem... it installs Ubuntu **into** Windows as if it was just another program.

From the website [Wubi]("http://wubi-installer.org/"):

> Wubi is a Ubuntu installer for Windows users that will bring you into the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other application. If you heard about Linux and Ubuntu, if you wanted to try them but you were afraid, Wubi is for you.

Wubi is Safe

It does not require you to modify the partitions of your PC, or to use a different bootloader.

Wubi is Simple

Just run the installer, no need to burn a CD.

Wubi is Discrete

Wubi keeps most of the files in one folder, and If you do not like, you can simply uninstall it.

Wubi is Free

Wubi (like Ubuntu) is free as in beer and as in freedom. You will get this part later on, the important thing now is that it costs absolutely nothing, it is our gift to you...

---

### Post by FrostiEE on 2008-04-07
With Wubi, the default is Windows unless you change it yourself.

---

