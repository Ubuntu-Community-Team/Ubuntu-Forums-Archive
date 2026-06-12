---
title: "Need help with Xonar DGX sound card"
date: 2020-02-11
forum: General Help
---

### Post by ancapistan on 2020-02-11
Hello everybody. I've been using various Ubuntu and Kubuntu installs for a few years now and I love them. I just installed Kubuntu 19.10 on a computer that uses a Xonar DGX sound card plugged into a PCI-E slot. I've never tried any linux install before on a computer that didn't use an integrated sound card. The Xonar DGX card gets recognized by the OS but it wasn't playing any sound. So I DuckDuckGo'd a bit and found info on how to get it to work from this link:

[https://xatom.dev/2018/05/03/xonar-dgx-ubuntu-18-04.html](https://xatom.dev/2018/05/03/xonar-dgx-ubuntu-18-04.html)

Here are the relevant steps:

> 
Launch alsamixer in a terminal, select the right sound card (F6), go to &#8220;Analog Output&#8221; (arrow right) and select &#8220;Multichannel&#8221; (arrow up)


The thing is that I need to do these steps every time I boot up the OS. I have to open a terminal, run alsamixer, choose the DGX card, and then select the Multichannel option every time. 

Is there a way to set this up so that the sound card works upon bootup without having to manually do the above steps? 

Thank you!

---

### Post by bcschmerker on 2020-02-12
**I have experience with the ASUS® XONAR® Series under ubuntu®.**  The driver ye want from the [Advanced LinUX Sound Architecture Project](https://www.alsa-project.org/) is **snd-virtuoso**, specifically written for the ASUS AV-100 as diffused and assembled by C-Media International Inc.; the [LinUX Kernel Project](https:///www.kernel.org/) is incorporating the ALSA drivers into the Kernel Modules (packages: linux-modules-*).

I suspect that the Kernel is seeing whatever planar sound chip your system has and setting that chip as default during startup.  Most motherboard manufacturers have their BIOS vendors include a set-up utility in which the various planar components can be enabled and/or disabled.  Disabling the planar audio (both Realtek® and VIA® manufacture DSP's around the intel® High Definition Audio specification) may enable automatic selection of the AV-100 as default.

---

### Post by ancapistan on 2020-02-13
Thank you for the informative reply! I will look into the driver and also disabling the MB audio device.

---

### Post by Yellow Pasque on 2020-02-13
The correct driver/module should be used by default.

You should be able to make an amixer command that is equivalent to using alsamixer to change the setting. And then you could run the command at each start (/etc/rc.local)
or
Maybe you could change the setting in alsamixer and run 'alsactl store' to save it. [https://linux.die.net/man/1/alsactl](https://linux.die.net/man/1/alsactl)

---

