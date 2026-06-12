---
title: "No sound in games via Wine"
date: 2007-05-16
forum: General Help
---

### Post by just_jeepin on 2007-05-16
I'm running a clean install of Ubuntu 7.04, installed Wine (via Synaptic), and installed 'Tonka Town' (a Windows game) for my son. It works great except there's no sound! Does anyone have any ideas?

Thanks for any help!
Danny

---

### Post by iheartme on 2007-05-17
Try running winecfg and check the Audio tab and see if an appropriate driver is selected. On my system Alsa is checked, and sound is working just fine,

The [Audio Faq]("http://www.winehq.org/site/docs/wineusr-guide/config-wine-main#AEN305") on winehq.org says this:

>  Wine can work with quite a few different audio subsystems which you can choose under the "Audio" tab. winecfg figures out all available drivers for you, but you can manually select which driver will be used. Older Linux distributions using the 2.4 kernel or earlier typically use the "OSS" driver. Usually 2.6 kernels have switched to "ALSA". The "aRts" driver was recently deactivated due to the general lack of maintenance of the "aRts" subsystem. If you're using GNOME you can probably use EsounD. The OSS and ALSA audio drivers get the most testing, so it's recommended you stick with them if possible. If you need to use "Jack", "NAS" or "CoreAudio" you probably already know why.

DirectSound settings are primarily used by games. You can choose what level of hardware acceleration you'd like, but for most people "Full" is fine. 

---

