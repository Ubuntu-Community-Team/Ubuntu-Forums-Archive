---
title: "Sound/ALSA issue in Wine and Firefox"
date: 2007-10-28
forum: General Help
---

### Post by oneoverzero on 2007-10-28
I run Gutsy (AMD64) on a Macboo.  Sound works with everything except for Wine and Firefox, When I run winecfg from the terminal I get
```
ALSA lib ../../src/conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib ../../../src/pcm/pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave

```
Initially I thought this was completely unrelated to my firefox sound problem, but when I run firefox from the terminal and go to a webpage with embedded sound, I get the following error repeated very quickly until either I leave the page or the sound stops (I can't tell which, as after it goes to the top of the term window I can't tell if it's moving or not)
```
ALSA lib ../../../src/pcm/pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
```
Sound works in all of my other applications, and I am pretty sure that they use ALSA... 

Can anybody help?  Please?

---

### Post by oneoverzero on 2007-10-28
I just tried reinstalling several ALSA libraries (even ones I knew couldn't effect it), ALSA itself, Wine, and Firefox, all to no avail.  

In the past I know that Firefox has worked with sound, and I cant think of anything I have installed or changed that should change that...  

Also, while wine has never had sound, until yesterday hitting the test sound button _before opening any wine applications (Steam is really the only one I use that has sound)_ would cause it to make a noise. 

However, after I would open Steam, clicking test sound would make winecfg tell me "Test sound failed!".  But today it won't make the test sound no matter what the circumstances are.   Phooey. 

Does anyone have any ideas?

---

### Post by oneoverzero on 2007-10-30
Things just got a lot worse.  

I searched my error on Google and saw someone saying that a solution was to install the 1.0.15 ALSA drivers, firmware, and others from source. I did that, and now I have NO SOUND WHATSOEVER.  I tried uninstalling it, and then using apt-get to reinstall the thngs from the repositories, that doesn't work either!  I tried reinstalling from source again, then modprobing "alsa-base", (and other things), but all i get is "FATAL" because it can't find the module

I hate to sound desparate, but...
PLEASE HELP!

EDIT:  I fixed this by arbitrarily messing with the modules... but I still have the original problem... so still please help

---

### Post by tagno25 on 2008-01-31
I get this problem in fire fox and when I search for the answer on Google all I come  up  wit are this post and one talking about wine

---

### Post by fatbuttlarry on 2008-02-07
What fixed mine was:

```
sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
sudo apt-get install --reinstall lib32asound2
```

======================================================================





I'm a fellow Steam, Wine, and Firefox user.  I have sound issues.  My issues started the day after I upgraded my graphics drivers with Envy.

Sound was still working at that point, but Half-Life would no longer load using OpenGL.

In my troubleshooting, I removed and reinstalled many applications.  Usually with apt-get.  My sound and graphics work great in everything but Wine and Firefox.

I have uninstalled and reinstalled items until I was blue in the face, without much luck.  I'm not sure what I changed either.  Can't find much online.  Best of luck!

I am running the KDE desktop.

Error: 

```
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint
ALSA lib ../../../src/pcm/pcm_hw.c:1423:(_snd_pcm_hw_open) Unknown field hint

```
Probably very simple fix, but I can't figure it out!

Linux Ubuntu 7.10 AMD64
wine-0.9.54
AMD64 1800+
GeForce FX 5600 128MB (Driver 169.09)
Onboard VIA Sound Controller, using "Default" or "ALSA"

-Tres

---

