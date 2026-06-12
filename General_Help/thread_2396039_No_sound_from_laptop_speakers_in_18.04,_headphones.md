---
title: "No sound from laptop speakers in 18.04, headphones work fine"
date: 2018-07-10
forum: General Help
---

### Post by TigrisAltaica on 2018-07-10
Hello!

I recently installed 18.04 on an HP Pavilion Laptop and I can't get any sound from speakers. Headphones work just fine however. I also have Windows 10 on the machine and the speakers work just fine. Any help would be greatly appreciated.


Thank you.

---

### Post by ardouronerous on 2018-07-10
If it is installed, check PulseAudio Volume Control, it should in available in the Applications Menu.
In PulseAudio, go to Output Devices and check if Line Out is either muted or set to 0%.

---

### Post by TigrisAltaica on 2018-07-10
> **ardouronerous said:**
> If it is installed, check PulseAudio Volume Control, it should in available in the Applications Menu.
In PulseAudio, go to Output Devices and check if anything either muted or set to 0%.

I checked with pavucontrol and nope, nothing is muted.

---

### Post by ardouronerous on 2018-07-10
Did you check Line Out in Output Devices?
If yes, the volume isn't set to 0%?

Weird.

---

### Post by ardouronerous on 2018-07-10
Found something on AskUbuntu: [https://askubuntu.com/questions/1029403/no-sound-in-ubuntu-18-04-lts-after-upgrade-from-16-04-lts](https://askubuntu.com/questions/1029403/no-sound-in-ubuntu-18-04-lts-after-upgrade-from-16-04-lts)

---

### Post by TigrisAltaica on 2018-07-10
> **ardouronerous said:**
> Did you check Line Out in Output Devices?
If yes, the volume isn't set to 0%?

Weird.


Output devices lists "Headphones" and "Speakers", no Line Out option.

---

### Post by #&amp;thj^% on 2018-07-10
Check the Configuration Tab and Look at the Built-in Audio>>>should be set to "Analog Stereo Duplex" 
If still no joy run this:
```

pulseaudio -k && rm -r ~/.config/pulse/*
```

---

### Post by TigrisAltaica on 2018-07-10
> **ardouronerous said:**
> Found something on AskUbuntu: [https://askubuntu.com/questions/1029403/no-sound-in-ubuntu-18-04-lts-after-upgrade-from-16-04-lts](https://askubuntu.com/questions/1029403/no-sound-in-ubuntu-18-04-lts-after-upgrade-from-16-04-lts)

Tried that, it killed sound from headphones. After rebooting the headphones work again but no change to speakers.

---

### Post by TigrisAltaica on 2018-07-10
> **1fallen said:**
> Check the Configuration Tab and Look at the Built-in Audio>>>should be set to "Analog Stereo Duplex" 
If still no joy run this:
```

pulseaudio -k && rm -r ~/.config/pulse/*
```

It is indeed set to "Analog Stereo Duplex". Ran the command but no change.

---

### Post by #&amp;thj^% on 2018-07-10
We have a stubborn one then do we? :)
Run this and paste back the output:
```
inxi-xxx -A
```
You may need to install inxi with:
```
sudo apt install inxi
```
Mine shows:
```
inxi -xxx -A
Audio:
  Card-1: Intel Sunrise Point-H HD Audio driver: snd_hda_intel v: kernel 
  bus ID: 00:1f.3 chip ID: 8086:a170 
  Card-2: NVIDIA GF114 HDMI Audio driver: snd_hda_intel v: kernel 
  bus ID: 01:00.1 chip ID: 10de:0e0c 
  Sound Server: ALSA v: k4.17.4-1-ARCH 

```

---

### Post by TigrisAltaica on 2018-07-10
> **1fallen said:**
> We have a stubborn one then do we? :)
Run this and paste back the output:
```
inxi-xxx -A
```
You may need to install inxi with:
```
sudo apt install inxi
```
Mine shows:
```
inxi -xxx -A
Audio:
  Card-1: Intel Sunrise Point-H HD Audio driver: snd_hda_intel v: kernel 
  bus ID: 00:1f.3 chip ID: 8086:a170 
  Card-2: NVIDIA GF114 HDMI Audio driver: snd_hda_intel v: kernel 
  bus ID: 01:00.1 chip ID: 10de:0e0c 
  Sound Server: ALSA v: k4.17.4-1-ARCH 

```

Alright, installed inxi and I got:

```
Audio:     Card Intel CM238 HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1f.3 chip-ID: 8086:a171
           Sound: Advanced Linux Sound Architecture v: k4.15.0-23-generic

```

Thanks for all your help, this is indeed a tricky one!

---

### Post by #&amp;thj^% on 2018-07-10
Well that card is definitely supported :[https://certification.ubuntu.com/catalog/category/AUDIO/?&page=2](https://certification.ubuntu.com/catalog/category/AUDIO/?&page=2)
I need to think here for a minute>>>not enough coffee in me yet. :D
Try in the same Configuration Tab and selecting if any HDMI devices shown, and I'll be back.

---

### Post by TigrisAltaica on 2018-07-10
> **1fallen said:**
> Well that card is definitely supported :[https://certification.ubuntu.com/catalog/category/AUDIO/?&page=2](https://certification.ubuntu.com/catalog/category/AUDIO/?&page=2)
I need to think here for a minute>>>not enough coffee in me yet. :D
Try in the same Configuration Tab and selecting if any HDMI devices shown, and I'll be back.


That also kills audio from the headphones until I change it back to Stereo Duplex AND fiddle with the volume. Thanks, I will also attempt to up the caffeine levels and see if that works.

---

### Post by #&amp;thj^% on 2018-07-10
That's what I had hoped for, I have run across in my travels where somehow they got reversed but I have not seen this on Ubuntu though.
I have a question though when you first boot up are the headphones plugged in?
Also after UN-plugging the headphones it might be worth checking if both Output Devices and playback devices are set to the speakers.
And more tip is to check:
```
alsamixer
```
To be sure nothing is muted there also.

---

### Post by TigrisAltaica on 2018-07-10
I just re-booted with the headphones unplugged just to be sure. No change and alsamixer shows nothing muted (auto-mute is enabled though). Output devices is set to speakers but I don't see anything relating to speakers in playback devices.

---

### Post by renatoazevedoes on 2018-07-10
I had this problem just now.
It happened cause I was watching a movie on VLC using HDMI. I disconnected the cable while audio was being played and then this happened.
I just reconnected the HDMI cable, played a video on YouTube and then changed the output from HDMI to Speakers. Solved the problem for me.

---

### Post by #&amp;thj^% on 2018-07-10
> **TigrisAltaica said:**
>  but I don't see anything relating to speakers in playback devices.

The only time anything is shown in the Playback tab is when something like a player or browser is using the Audio.
My screenshot will help make sense of this.
Now you won't see the FFT based EQ as i have but you get the idea.
I'm running out if ideas here.
**EDIT: Just for fun run this in terminal, and check the volume is at a level you can hear this test.**
```
 speaker-test -c 2
```

---

### Post by TigrisAltaica on 2018-07-10
> **1fallen said:**
> The only time anything is shown in the Playback tab is when something like a player or browser is using the Audio.
My screenshot will help make sense of this.
Now you won't see the FFT based EQ as i have but you get the idea.
I'm running out if ideas here.
**EDIT: Just for fun run this in terminal, and check the volume is at a level you can hear this test.**
```
 speaker-test -c 2
```

Yup, I can see which applications are playing sound but nothing in that area where you drew the red arrow.

---

### Post by ardouronerous on 2018-07-10
[https://askubuntu.com/questions/1034187/ubuntu-18-04-no-audio-from-speakers-headphones-working](https://askubuntu.com/questions/1034187/ubuntu-18-04-no-audio-from-speakers-headphones-working)

Similar problem to yours, updated to 18.04, no sound in speakers but headphones are working, hope this helps.

I suggest you backup /etc/modprobe.d/alsa-base.conf before attempting this, so can easily restore it if this doesn't work.

---

### Post by TigrisAltaica on 2018-07-10
> **ardouronerous said:**
> [https://askubuntu.com/questions/1034187/ubuntu-18-04-no-audio-from-speakers-headphones-working](https://askubuntu.com/questions/1034187/ubuntu-18-04-no-audio-from-speakers-headphones-working)

Similar problem to yours, updated to 18.04, no sound in speakers but headphones are working, hope this helps.

I suggest you backup /etc/modprobe.d/alsa-base.conf before attempting this, so can easily restore it if this doesn't work.

Tried this as well, no change.

---

### Post by ardouronerous on 2018-07-10
I found a bug report for this issue: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1770429](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1770429)
I added in your issue to the bug report and have linked this thread to it. Hope this issue gets fixed.

Since you said headphones are working, the only other solution is a workaround, plug in some USB mini speakers.

---

### Post by Yellow Pasque on 2018-07-11
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

> I found a bug report for this issue: [https://bugs.launchpad.net/ubuntu/+s...r/+bug/1770429](https://bugs.launchpad.net/ubuntu/+s...r/+bug/1770429)

Same symptom, but a different system (and probably a different codec). Linux audio fixes tend to be system-specific, which is one of the things that makes them difficult to troubleshoot.

---

### Post by johnneydarkness on 2018-12-20
Same problem: [COLOR=#000000]HP Pavilion Laptop Bang & Olsen Built In Speakers[/COLOR]

    ```
inxi -xxx -A
    Audio:     Card-1 Advanced Micro Devices [AMD] Device 157a
               driver: snd_hda_intel bus-ID: 00:09.2 chip-ID: 1022:157a
               Card-2 Advanced Micro Devices [AMD/ATI] Kabini HDMI/DP Audio
               driver: snd_hda_intel bus-ID: 00:01.1 chip-ID: 1002:9840
               Sound: Advanced Linux Sound Architecture v: k4.15.0-42-generic
```

This configuration was working a few days ago is the strange part. My speakers *stopped* working.

---

