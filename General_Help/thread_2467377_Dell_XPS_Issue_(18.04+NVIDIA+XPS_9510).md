---
title: "Dell XPS Issue (18.04+NVIDIA+XPS 9510)"
date: 2021-09-24
forum: General Help
---

### Post by klaxmaster on 2021-09-24
I have:
XPS 9510 w/ rtx 3050TI
Ubuntu 18.04.6 Desktop

And I can ***not*** get the desktop environment to work, and it seems to be something with the NVIDIA drivers.

As soon as the NVIDIA proprietary drivers are installed, the Desktop environment fails. I install Ubuntu with a USB Live environment, boot, install NVIDIA drivers, GUI freezes at boot. At this point I can use "Ctrl+Alt+F2" to enter TTY, and everything works

I have tried:
-Early driver versions (everything from 415 on seems to just install 460, until 470, which install 470)
-Driver Version 390 installs version 390, but does not work, requires nomodeset to boot, and the drivers dont load according to nvidia-smi
-Kernel versions from 5.4.0 and up. And also 5.8 Version. (note, network drivers dont function on 5.8)
-I have tried ubuntu 20.04, and had same result (i HAVE to have ubuntu 18,04 anyway, but it was an attempt)
-The workaround listed In [Reddit/r/DellXPS]("https://www.reddit.com/r/DellXPS/comments/p79ig3/nvidia_driver_issues_on_xps_15_9510_running/he4krlv/?context=3") (like i said earlier, version 450 just installs 460, and still GUI doesnt load)
-I used 390 to select performance like that workaround suggests. And it did not help when i then installed 470 afterwards.
-Reinstalling gnome-shell/desktop
-Installing alternate desktop environments (KDE, Unity)
-Messing with bios settings (mainly those that say pcie in it)
-BIOS has been updated to most recent version, was also tested on older BIOS versions

All results in the same thing. view pictures [HERE,]("https://imgur.com/0KeWsqx") [HERE,]("https://imgur.com/jQRq3ai") and [HERE]("https://imgur.com/vEHVgrx"). In each one, I am in TTY, with the drivers WORKING. but I CAN'T get GUI to run. Each one looks different because its either a different version of Ubuntu, or different shell, etc.

Company bought 100s (~$500k worth) of these when the XPS 9500 order could not be filled. Took us months to get them. I am the companies Linux Support, And I can't get this **** to work. I swear to god I HOPE I'm missing something stupid and easy that someone here can point out. but I've been run dry at the company, and been working many 12-14 hour days the past couple weeks (not just on this) so I beg someone, please help.

FYI, 9500 worked with 0 issues or workarounds required.
desktops with rtx 30xx work with 0 issues or workarounds required.

Posted this in reddit/r/ubuntu and /r/DellXPS and /r/ITdept. thanks guys for your time.

---

### Post by tea for one on 2021-09-25
Does your device have 11th Generation Intel Processor?

You may need to install a later kernel?

I noticed that you need to use 18.04 but why not try 21.04 just to see if it works?

---

### Post by klaxmaster on 2021-09-27
> **tea for one said:**
> You may need to install a later kernel?
I installed many different kernels. lol
However, In a past issue on the 9570 line when they were BRAND NEW, there was ONE single kernel that worked. so I went ahead and just continued trying every kernel.
I got to 5.11.0-051100-generic.. and after fixing OTHER issues (default network drivers didnt work) it seems this, with NVIDIA driver 4.70.63.01 is the winning combo.
woohoo
Hopefully, also like when the 9570 line was new, the next release of 5.4 kernel will work with the new hardware.

---

