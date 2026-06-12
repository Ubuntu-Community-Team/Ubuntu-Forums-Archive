---
title: "Why so very few 16:9 aspect ratio resolutions."
date: 2018-06-16
forum: General Help
---

### Post by debderivs on 2018-06-16
Hi guys,

Xubuntu, Nvidia card, 23" Full HD Asus monitor.

On Linux why do I have just one 16:9 resolution? 1920x1080. The next lower res is 1680x1050, which
seems not to be 16:9; the videos on VLC and Kaffeine are displayed stretched and with black borders 
on full screen. On Windows with this same machine, there is another in between resolution which 
seems to be 16:9, 1600x900. 

Why this other res at 1600x900 is not available on Linux? And, is there a way to add it? forcing it,
perhaps? I don´t know if a resolution can be forced, but if so, and it is save to not cause any
problem to the monitor, I could try it...

Thanks.

Cheers.

---

### Post by Dennis N on 2018-06-16
> On Linux why do I have just one 16:9 resolution? 1920x1080.
Can be more than that; depends on graphics system. One of my computer monitors has 1600x900 native resolution, and that's supported by the integrated Intel graphics.

---

### Post by SeijiSensei on 2018-06-16
Are you using the NVIDIA settings app to change the resolution?  Look under Settings in the main menu.

---

### Post by Autodave on 2018-06-16
Go to Settings -> Additional Drivers. It should search and find an Nvidia driver. Let it install the recommended one for now.

---

### Post by debderivs on 2018-06-16
> **Dennis N said:**
> Can be more than that; depends on graphics system. One of my computer monitors has 1600x900 native resolution, and that's supported by the integrated Intel graphics.

Native on mine is 1920x1080, but through System/monitor and Nvidia´s app 1600x900 is not there... 
I´d like to use 1600x900 and, more often, because the fonts and everything is not so small.

---

### Post by debderivs on 2018-06-16
> **SeijiSensei said:**
> Are you using the NVIDIA settings app to change the resolution?  Look under Settings in the main menu.

Yes, but 1600x900 is not there, neither through System/monitor...

---

### Post by debderivs on 2018-06-16
> **Autodave said:**
> Go to Settings -> Additional Drivers. It should search and find an Nvidia driver. Let it install the recommended one for now.

It´s already installed, the correct version for my card, but Nvidia´s settings doesn´t show the 1600x900 mode.
Perhaps there could be a solution forcing it, but never did this, so I prefer to see some experience on this
before touching anything.

Here you can see it:

---

### Post by SeijiSensei on 2018-06-17
In the NVIDIA settings app, is the monitor correctly identified? Maybe the monitor's complete list of specifications is not available to the card.

You might be able to add the resolution manually by adding a "ModeLine" to /etc/X11/xorg.conf.  If you don't have one of those, you should create it by running "sudo nvidia-xconfig".  You can then follow the instructions here:  [https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

---

### Post by debderivs on 2018-06-17
> **SeijiSensei said:**
> In the NVIDIA settings app, is the monitor correctly identified? Maybe the monitor's complete list of specifications is not available to the card.

You might be able to add the resolution manually by adding a "ModeLine" to /etc/X11/xorg.conf.  If you don't have one of those, you should create it by running "sudo nvidia-xconfig".  You can then follow the instructions here:  [https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)


Yes, it is identified but the app nor the OS monitor´s settings show that resolution, 1600x900.

Thanks for that guide, I´ll give it a try, though I didn´t want to force a resolution like this. Hope it works and have no problem.

Cheers, mate.

---

