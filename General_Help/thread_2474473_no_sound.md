---
title: "no sound"
date: 2022-04-30
forum: General Help
---

### Post by cmcanulty on 2022-04-30
I yesterday added some new sound themes trying to get system sounds to work with no luck. But now I get no sound whatsoever. I have given up on system sounds and just want my sound back! I have tries uninstalling and reinstalling every alsa and pulse apps I could find with no luck. Everything worked perfectly before i starting messing with sound themes. I am using a TV monitor and get my sound through HDMI. I also tried an external speaker with no luck. When I type alsamixer I get the following error
Even the volume icon is gone from my panel.


```
cmcanulty@Dell660s:~$ alsamixer
cannot open mixer: No such file or directory

```

If I type alsa I get this:

```
cmcanulty@Dell660s:~$ alsa
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
```

I sure hope I don't have to reinstall due to this as I have a ton of customized things set up. Thank you

---

### Post by SeijiSensei on 2022-04-30
Are you really still on 14.04? If so, I don't think many people here can help.

First, what graphics adapter are you using? If it's NVIDIA, do you have the driver installed?  If so, have you selected HDMI output? It often takes me a couple of tries to get HDMI output running correctly. I'm using KDE Neon which is Ubuntu 20.04 at base.  Sometimes installing pavucontrol can help with this, but that relies on pulseaudio being installed.

---

### Post by cmcanulty on 2022-04-30
I am on Xubuntu 20.04

---

### Post by cmcanulty on 2022-04-30
I am on Xubuntu 20.04. I didn't realize the distro info was old on my profile. I just updated it. There is no where to edit the config to HDMI as I can't even get to audio settings not even the volume icon is there. I have pavucontrol but the config tab is empty and pulse audio is also installed.

```
cmcanulty@Dell660s:~$ pulseaudio
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
```

---

### Post by cmcanulty on 2022-05-01
OK I have purged and reinstalled pulse and alsa and still no luck however I have no info. Alsa finds no sound card driver

```
 sudo alsa force-reload
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

```

also my sound card is

from lspci command

Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)

so how do I install or reinstall that driver? To be clear sound worked perfectly until I decided to try to get a sytsem sound theme to work which I never did and have given up on that. I just want sound back.

---

