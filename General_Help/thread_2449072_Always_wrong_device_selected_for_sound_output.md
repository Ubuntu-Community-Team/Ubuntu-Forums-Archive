---
title: "Always wrong device selected for sound output"
date: 2020-08-19
forum: General Help
---

### Post by psiie on 2020-08-19
I have a Yeti USB Microphone. In the sound preferences pane, I always change the output away from yeti (it has a headphone plug in the device) to my "built-in audio analog stereo". However, no matter how many times I change this, it always sets itself to Yeti on boot.

I would like to blacklist this device (only from output) or force select a output on startup.

The issue this causes is that any video player that initialized when Yeti was selected, must be killed and restarted. It will NOT pick up the change. It just so happens I remember after trying to play something and going through the motions of debugging.

---

### Post by TheFu on 2020-08-20
Set the default output device:

```
$ pactl list short sinks
0       **alsa_output.pci-0000_00_1f.3.analog-stereo**      module-alsa-card.c     s16le 2ch 44100Hz        IDLE

#   Use the "name: xxxxxxx" part
$ pactl set-default-sink      **alsa_output.pci-0000_0a_00.3.analog-stereo**
```

Obviously, change the sink name in the 2nd command based on the first command output.

---

### Post by psiie on 2020-08-30
I thought this did the trick but it turns out that Its back to the same issue. (I could have sworn it fixed it when I did a reboot). 
So my Yeti microphone is still selected as default on a fresh boot even though we tell pactl to use "built-in audio analog stereo". Here is a screenshot of pactl fresh after boot. (and yes, when I use "pactl set-default-sink", "pactl info" does show the default sink to be the correct one. It seems the setting does not persist reboots)

[IMG]https://dl.dropboxusercontent.com/s/9si9pq26oce3k32/20-08-30_at_12-04-29.png[/IMG]

---

### Post by TheFu on 2020-08-30
Does running 
```
$ pactl set-default-sink ....
```
again fix it?
If so, add that to your startup programs.  There are probably 10 other, better ways to do this.

---

### Post by psiie on 2020-09-01
running the command didn't fix it permanently, only for that session. Adding it to the startup programs work XD. Seems hacky, but here we are :P. Thanks! ^_^

---

### Post by TheFu on 2020-09-01
> **psiie said:**
> running the command didn't fix it permanently, only for that session. Adding it to the startup programs work XD. Seems hacky, but here we are :P. Thanks! ^_^

100% agreed. Major hack.  You can look for pulse.client file and put that in the expected place with the expected setting, if you like. The directory is probably ~/.config/pulse/   An example "client file" is /etc/pulse/client.conf - at the top there appear to be default settings.  Only those you want to be different from the system-wide should be uncommented in your ~/.config/pulse/client.conf file.

On a few of my systems, I have to set 
```
enable-shm = no
```
or audio never works.

Sorry, I didn't remember this earlier.

---

