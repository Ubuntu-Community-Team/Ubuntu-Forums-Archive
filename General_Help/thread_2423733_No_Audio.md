---
title: "No Audio"
date: 2019-07-28
forum: General Help
---

### Post by danielsender on 2019-07-28
I have 18.04 on a Lenovo Thinkpad 11e. I was having problems with no audio coming from websites such as youtube. On the other hand if I went to Sound Settings to test the speakers I would get the audio out. So I started playing a bit with alsamixer and pavucontrol with no luck. Furthermore, now after that exercise, there is no audio at all, not even in the Sound Settings->Test Speakers. Even the volume control on the top panel disappeared (I'm using Gnome flashback). I followed some recommendations such as:

[B][I]sudo apt remove --purge alsa-base pulseaudio
sudo apt install alsa-base pulseaudio
sudo alsa force-reload
[/I][/B]
to no avail.

I will appreciate any help.

---

### Post by danielsender on 2019-07-29
Any suggestions?

---

### Post by danielsender on 2019-07-30
Did I post on the right forum group?

---

### Post by dino99 on 2019-07-30
First glance at 'system settings' to know if the hardware is well identified; then also see warnings/errors from 'journalctl -b' about hardware/alsa/sound
Did that trouble came after an upgrade ?

---

### Post by danielsender on 2019-07-30
> **dino99 said:**
> First glance at 'system settings' to know if the hardware is well identified; then also see warnings/errors from 'journalctl -b' about hardware/alsa/sound
Did that trouble came after an upgrade ?

The trouble came after playing with pavucontrol because I wasn't getting sound from websites such as youtube - as I said in my posting, the speaker test was working but now it is not and I don't even have the volume control anymore on the top panel.

---

### Post by danielsender on 2019-07-30
Any ideas?

---

### Post by mastablasta on 2019-07-31
what is the hardware - the sound chip?

what happens if you try 
```
sudo alsa reload -c
```

---

### Post by danielsender on 2019-07-31
> **mastablasta said:**
> what is the hardware - the sound chip?

what happens if you try 
```
sudo alsa reload -c
```

```
Unloading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-seq snd-rawmidi snd-seq-device snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer).Loading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-seq snd-rawmidi snd-seq-device snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer.

```

---

### Post by mastablasta on 2019-08-01
just unloading? does it load them back, does the sound work?

also sound chip is what? : [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by danielsender on 2019-08-01
Sound is back, thanks!

---

