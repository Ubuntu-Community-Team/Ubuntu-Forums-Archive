---
title: "[SOLVED] Re-installing XP on other hard drive"
date: 2008-04-17
forum: General Help
---

### Post by Aled Y Cymro on 2008-04-17
I'm planning soon on performing an install over the top (a repair install - done by pressing R somewhere in the install process) of XP soon, as it is really starting to play up (handy I have ubuntu too!). A few questions:

1) I can't boot from the CD. It's set to boot from CD in the BIOS, but that simply gets rid of the “Loading GRUB” message and goes straight into the GRUB loader. Is there a command to boot from the CD in GRUB itself?

2) Will doing a repair install delete GRUB from the bootup process? If it does, how do I reinstall it?

3) Is there a way of forcing Ubuntu to start (tapping an F key, for example), without GRUB, so if it all goes wrong, the computer can be used?

---

### Post by bodhi.zazen on 2008-04-17
In terms of booting to the CD, set you BIOS to boot the cd first, before your hard drive. If that fails, check the integrity of you CD ...

After installing Windows you will need to restore grub. This is fairly easy and is done with the Ubuntu Live CD.

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by Aled Y Cymro on 2008-04-17
Alas, the CD boots fine on my other systems. The BIOS is set to CD, and then either floppy or HDD (in different combinations).

Thanks for the guide, though. That will prove useful :)

---

### Post by bodhi.zazen on 2008-04-17
Just have to ask the obvious ...

Does the CD drive work ? Will it boot the Ubuntu Live CD ?

---

### Post by lswest on 2008-04-17
and yeah, i also wrote a how-to on restoring GRUB after installing windows (second link in my sig) if you want to take a look.  Feel free to PM me/reply on my how-to if you need help or have any questions.  And about the CD not working...i'm with bodhi on this one, but i'll look into booting to a CD from GRUB.

*EDIT* just saw [this]("http://btmgr.sourceforge.net/download.html") supposedly it can be used to boot to a CD (however, it's a different boot manager all together, so maybe read up on it properly first)

---

### Post by Aled Y Cymro on 2008-04-18
> **bodhi.zazen said:**
> Just have to ask the obvious ...

Does the CD drive work ? Will it boot the Ubuntu Live CD ? Yes, now that I have set it as the default CD drive. I always manage to miss the painstakingly obvious stuff :oops:

---

