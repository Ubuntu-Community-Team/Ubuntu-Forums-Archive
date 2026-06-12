---
title: "Multiple programs running multiple sounds at once?"
date: 2005-10-19
forum: General Help
---

### Post by KevRus on 2005-10-19
I constantly get errors saying "Cannot access sound card, it may currently be in use" when I try to run XMMS or any other audio player while using another program that uses sounds.....And when I quit the other application and run XMMS, when I reopen the application I quit that application no longer makes sounds.....So is there a way I can run multiple programs and hear all of their sounds at once?

---

### Post by xMetaRidley on 2005-10-20
Yes, you must configure everything to use ALSA's mixer.

[LIST=1]
[*]System->Preferences->Multimedia Systems. Select ALSA for both options (Sink and Source).
[*]sudo gedit /etc/libao.conf . Set "default_driver=alsa".
[*]Now sudo gedit /etc/esound/esd.conf. Make it look like this:
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```
[*]Now for OSS emulation: Install AOSS (alsa-oss) with synaptic and do this:
```

sudo gedit /etc/asound.conf

```
Now add this to the end:
```

########default
pcm.default {
     type plug
     slave.pcm "dmixer"
}

########AOSS
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

ctl.mixer0 {
        type hw
        card 0
}
########

```
You may need to change "dmixer" to something else, depending on how the rest of asound.conf is set up. I think "dmixer" is the default in breezy though. The mixer itself is already set up in Breezy.  After doing all of the above, reboot.
[*]Finally set all applications to use ALSA if possible. In XMMS, you must go to the audio output plugins tab and select ALSA. MPlayer, VLC etc. have similar options. For Firefox, you have to sudo gedit /etc/mozilla-firefox/mozilla-firefoxrc and set it to use "aoss". For SDL programs you need to create a script to run the program with the environmental variable "SDL_AUDIODRIVER=esd".
[/LIST]

---

### Post by Doc.Caliban on 2005-11-02
[QUOTE=xMetaRidley]
[*]Now for OSS emulation: Install AOSS (alsa-oss) with synaptic and do this:
```

sudo gedit /etc/asound.conf

```
Now add this to the end:
```

########default
pcm.default {
     type plug
     slave.pcm "dmixer"
}

########AOSS
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

ctl.mixer0 {
        type hw
        card 0
}
########

```[/QUOTE]

I installed alsa-oss, but when I run sudo gedit /etc/asound.conf I get a blank file.

-Doc

---

### Post by Swoop on 2005-11-02
I get the same... so i dont know what else to do ;)

---

