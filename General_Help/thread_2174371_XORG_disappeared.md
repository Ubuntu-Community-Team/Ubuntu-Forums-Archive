---
title: "XORG disappeared"
date: 2013-09-14
forum: General Help
---

### Post by lonekingc4 on 2013-09-14
Hi,

I am using Ubuntu 12.04 32 bit. This morning it ran perfectly and I turned my PC off normally. But just now, I turned it on and Ubuntu booted normally, but there was no GUI. There was only a login prompt like a terminal. I logged in and tried to reconfigure xorg but it said xorg was not installed. So I had to install xorg again and now it works. But I was wondering, why did xorg disappear automatically? Can it happen again?

And by the way, the graphics on the new installation of xorg seems a bit lower than that of a fresh Ubuntu setup. And I checked the update manager and it said no update is needed.

Thanks. Cheers.

---

### Post by Bucky Ball on 2013-09-14
*Thread moved to **General Help**.*

---

### Post by ajgreeny on 2013-09-14
Have you recently removed some package or other that also took with it xorg, and perhaps other packages as well?

You can always use command ```
sudo apt-get install --reinstall ubuntu-desktop
``` to get back the full ubuntu system if that should happen again.

---

### Post by grahammechanical on 2013-09-14
Xorg was still there otherwise you would not be getting even a Linux Command line prompt (like a terminal). What was missing was an Xorg configuration file that set the screen resolutions. This is not needed in Ubuntu because Ubuntu gets the screen resolutions directly from the monitor every time it boots and does not need a configuration file to set screen resolution.

If there was no GUI then it may be because of something to do with Compiz the windowing/composition manager or Unity the user interface or with whatever user interface you were using.

You may find that you are now running on Nouveau the open source video driver and that you may need to activate a proprietary video driver. Video drivers can also cause this problem.

Regards.

---

### Post by lonekingc4 on 2013-09-14
> **ajgreeny said:**
> Have you recently removed some package or other that also took with it xorg, and perhaps other packages as well?

You can always use command ```
sudo apt-get install --reinstall ubuntu-desktop
``` to get back the full ubuntu system if that should happen again.

Well the last time I booted the PC before the problem occured, I am sure I did not remove anything.

Anyways, thanks for the command :D

---

### Post by lonekingc4 on 2013-09-14
> **grahammechanical said:**
> Xorg was still there otherwise you would not be getting even a Linux Command line prompt (like a terminal). What was missing was an Xorg configuration file that set the screen resolutions. This is not needed in Ubuntu because Ubuntu gets the screen resolutions directly from the monitor every time it boots and does not need a configuration file to set screen resolution.

If there was no GUI then it may be because of something to do with Compiz the windowing/composition manager or Unity the user interface or with whatever user interface you were using.

You may find that you are now running on Nouveau the open source video driver and that you may need to activate a proprietary video driver. Video drivers can also cause this problem.

Regards.

Well the video driver is working just fine I think. I have tried the proprietary driver, but the open source one works way better (except gaming, which I don't do much).

Anyways, everything seems ok now after reinstalling xorg. Hopefully the problem won't occur again.

Thanks :)

---

