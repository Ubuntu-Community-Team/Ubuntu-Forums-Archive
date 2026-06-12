---
title: "skype"
date: 2013-05-07
forum: General Help
---

### Post by iuval on 2013-05-07
My synaptic package manager didn't have skype, so I tried downloading from the skype website Ubuntu 10.04 distribution, but it didn't work when trying to install. Then I tried downloading lubuntu 12.04 (upgrading from the Update Manager, hoping that skype would work with the newer version), but my connection was too slow and I interrupted it. It restored the old distribution and said I could resume later. But when I open the Update Manager, it thinks that everything is up to date. Suggestions? The ultimate goal is to have skype, not upgrade. Also, when I tried google voice, my microphone wasn't working.

---

### Post by Impavidus on 2013-05-07
10.04 is end of live (except for the server edition, but I don't know whether skype is included in the server edition). Skype is available in the repositories for 12.04, and also in the newer versions (at least, for the time being. With skype being owned by microsoft it may end one day). Lubuntu doesn't have LTS versions, so no reason to stay with 12.04, unless your hardware is too old. It's best to use a supported version anyway.

You interrupted the upgrade whilst it was still downloading packages, before installation started. Therefore nothing has happened to your computer. You still have a clean up-to-date 10.04 installation, for as far as an end-of-live version can be up-to-date.

---

### Post by iuval on 2013-05-07
So how do I get skype? I don't know how to upgrade to 12.04 now (I don't understand what you said. On one hand, skype is available in 12.04, on the other hand no reason to switch to 12.04?)

> **Impavidus said:**
> 10.04 is end of live (except for the server edition, but I don't know whether skype is included in the server edition). Skype is available in the repositories for 12.04, and also in the newer versions (at least, for the time being. With skype being owned by microsoft it may end one day). Lubuntu doesn't have LTS versions, so no reason to stay with 12.04, unless your hardware is too old. It's best to use a supported version anyway.

You interrupted the upgrade whilst it was still downloading packages, before installation started. Therefore nothing has happened to your computer. You still have a clean up-to-date 10.04 installation, for as far as an end-of-live version can be up-to-date.

---

### Post by monkeybrain2012 on 2013-05-07
Open Synaptic, go to Settings > Repositories > Other Software and check the box that says Canonical Partner, Reload Synaptic and you will find Skype.

---

### Post by iuval on 2013-05-07
> **monkeybrain2012 said:**
> Open Synaptic, go to Settings > Repositories > Other Software and check the box that says Canonical Partner, Reload Synaptic and you will find Skype.

I did that, but there was only earcandy, pidgin-skype, and pidgin-skype.dbg, all of which I already installed. I don't see skype anywhere.

---

### Post by iuval on 2013-05-07
> **iuval said:**
> I did that, but there was only earcandy, pidgin-skype, and pidgin-skype.dbg, all of which I already installed. I don't see skype anywhere.
pidgin-skype doesn't work...

---

### Post by monkeybrain2012 on 2013-05-07
Did you reload synaptic? (I mean clicking the "reload" button on the upper left corner, not restarting synaptic) It has to update the information about repositories. This is the same as typing "sudo apt-get update" in the terminal.

---

### Post by dandroid13 on 2013-05-07
pidgin-skype is a plugin to enable to connect to Skype using Pidgin, it's not a program itself.

---

### Post by iuval on 2013-05-07
> **iuval said:**
> I did that, but there was only earcandy, pidgin-skype, and pidgin-skype.dbg, all of which I already installed. I don't see skype anywhere.


Thanks very much! But now the mic doesn't work in skype. It works in other programs such as Sound Recorder. I tried fiddling with the Alsa gui, but no luck. Any suggestions?

---

### Post by dandroid13 on 2013-05-08
I'm afraid Lubuntu doesn't use Alsa, but I may be wrong. If you want to upgrade, use an USB stick, install```
usb-creator-gtk
```and choose to upgrade, it's easier than download everything.

---

### Post by iuval on 2013-05-08
> **dandroid13 said:**
> I'm afraid Lubuntu doesn't use Alsa, but I may be wrong. If you want to upgrade, use an USB stick, install```
usb-creator-gtk
```and choose to upgrade, it's easier than download everything.

I am able to adjust sound properties with ALSA, so that means Lubuntu uses ALSA? As far as using a USB stick, do you mean the one that has Lubuntu OS on it? And then type the line above into terminal window? I know that when I was trying to use recordmydesktop, the mic wasn't working because it was set to single channel input instead of dual, or something like that, but I didn't find a similar setting in skype. Is it looking for input from a jack?

---

### Post by dandroid13 on 2013-05-08
I'm sorry, It's been a while since I used Lubuntu for the last time, so I don't know exactly. I mean, you install that package, and use it to make a bootable usb stick. Then you use it to upgrade to 12.04 without having to download all the packages.

---

### Post by iuval on 2013-05-08
> **dandroid13 said:**
> I'm afraid Lubuntu doesn't use Alsa, but I may be wrong. If you want to upgrade, use an USB stick, install```
usb-creator-gtk
```and choose to upgrade, it's easier than download everything.
I also tried fiddling with the pulse audio volume control program.No luck.

---

### Post by dandroid13 on 2013-05-08
I think you should try upgrading before installing Skype, just follow the steps I posted above.

---

