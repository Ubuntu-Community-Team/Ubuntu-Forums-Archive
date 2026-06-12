---
title: "Intel 82801 Audio Driver Problem"
date: 2008-03-16
forum: General Help
---

### Post by zywang519 on 2008-03-16
Hi, I have installed Linux a couple days ago, and it's pretty good except that I just can't seem to get the audio card to work properly. My laptop has built-in speakers and a headphone jack. The speakers are working but the headphone jack don't do anything.

My card's model is Intel 82801H (ICH8 Family) HD Audio Controller

Thanks.

---

### Post by danwood76 on 2008-03-16
What laptop do you have?
It might be a simple case of specifying a different model type in the alsa config.

Need a little more info to be able to help.
could you post the output of these in the terminal:
```

aplay -l
lspci -v | grep -i 'audio'

```

---

### Post by zywang519 on 2008-03-16
My laptop is a Sony Vaio vgn fz140e

Output of aplay -l:

**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:1588:(snd_config_load1) /home/ziying/.asoundrc.asoundconf:8:1:Unexpected char
ALSA lib conf.c:2849:(snd_config_hook_load) /home/ziying/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2713:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3076:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:213: control open (0): Invalid argument

Output of lspci -v | grep -i 'audio':
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


Thanks for the help.

---

### Post by zywang519 on 2008-03-19
danwood76,
Did you just like forgot about this or assumed that I figured it out eventually?
Cuz, i didn't...

---

### Post by FuturePilot on 2008-03-19
Run
```
gnome-volume-control
```
And try muting the Master channel when you plugin the headphones.

---

### Post by mali2297 on 2008-03-19
> **zywang519 said:**
> 
Output of aplay -l:

**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:1588:(snd_config_load1) **/home/ziying/.asoundrc.asoundconf**:8:1:Unexpected char
ALSA lib conf.c:2849:(snd_config_hook_load) **/home/ziying/.asoundrc** may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2713:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3076:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:213: control open (0): Invalid argument


Try renaming those files, and check again. Have you edited the files yourself? Post their content.

---

### Post by danwood76 on 2008-03-19
Sorry I forgot to post a reply.

You need to add some options to the alsa config.
could you post your alsa config file please?
```

cat /etc/modprobe.d/alsa-base

```
will dump it to the terminal.

---

