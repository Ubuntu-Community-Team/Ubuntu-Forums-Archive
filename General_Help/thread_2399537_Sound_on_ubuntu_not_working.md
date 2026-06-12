---
title: "Sound on ubuntu not working"
date: 2018-08-26
forum: General Help
---

### Post by austincibulka on 2018-08-26
Hello,

I am very new to ubuntu and would appreciate any help for my problem. Thank you.

I am running ubuntu 16.04 on a dell inspiron laptop. My sound was initially only working with headphones in (speakers/headphones were both playing), I followed the following advice:

[https://askubuntu.com/questions/276170/speakers-and-headphones-at-the-same-time-when-using-a-dv6-2170](https://askubuntu.com/questions/276170/speakers-and-headphones-at-the-same-time-when-using-a-dv6-2170)

And now my speakers don't work at all. There are zero sound outputs on the system sound settings and my pavucontrol will not load.

See below for screenshots of my alsamixer and sound settings.
[ATTACH=CONFIG]280862[/ATTACH][ATTACH=CONFIG]280863[/ATTACH]

---

### Post by Yellow Pasque on 2018-08-26
There  are multiple suggestions on the link you gave. Which one did you follow?

---

### Post by austincibulka on 2018-08-26
[COLOR=#242729][FONT=Arial]Sorry for the confusion. These are the suggestions I followed.

The solution was to do the following:[/FONT][/COLOR]

[LIST=1]
[*][FONT=inherit]In the terminal type: sudo gedit /etc/modprobe.d/alsa-base.conf[/FONT]

[*][FONT=inherit]At the end of the file paste the following:[/FONT]
alias snd-card-0 snd-hda-intel  
options snd-hda-intel model=dell-m4-1 enable_msi=1

[*][FONT=inherit]Save and Reboot.[/FONT]

[*]

[/LIST]

---

### Post by Yellow Pasque on 2018-08-26
So did you try to delete the lines you added (and reboot)?

And after you do that, try and get more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by austincibulka on 2018-08-26
> **Temüjin said:**
> So did you try to delete the lines you added (and reboot)?

And after you do that, try and get more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)


Yes, I deleted the lines, reboot my system and nothing changed with my sound settings.

This is what my alsa-base looks like:

[ATTACH=CONFIG]280864[/ATTACH]

---

### Post by austincibulka on 2018-08-26
> **Temüjin said:**
> So did you try to delete the lines you added (and reboot)?

And after you do that, try and get more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Here is my information after following the instructions in the link you provided:

[http://www.alsa-project.org/db/?f=126897a9579f30c388f08d92b88687a41618e7f8](http://www.alsa-project.org/db/?f=126897a9579f30c388f08d92b88687a41618e7f8)

---

### Post by Yellow Pasque on 2018-08-26
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 111 [87%] [-12.00dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 127 [100%] [0.00dB] [off]
```

It looks like you need to unmute these controls in alsamixer (using 'm' key).

---

### Post by austincibulka on 2018-08-27
> **Temüjin said:**
> ```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 111 [87%] [-12.00dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 0 [0%] [-99999.99dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 127 [100%] [0.00dB] [off]
```

It looks like you need to unmute these controls in alsamixer (using 'm' key).

Thank you for the continuous reply, but it appears this did not solve the problem.

I have unmuted these controls and here is my liink: [http://www.alsa-project.org/db/?f=419902a97f827d1c04ff5f711714fda2d0c27fd8](http://www.alsa-project.org/db/?f=419902a97f827d1c04ff5f711714fda2d0c27fd8)

The link shown is for when there are no headphones plugged in.

The sound icon on the top right is still grayed out. I did notice that when I re-boot the machine, before logging in it shows sound. But once I log out, it goes back to being grayed out.

---

### Post by Yellow Pasque on 2018-08-27
Try this:
```
rm -rf ~/.config/pulse*; pulseaudio -k
```

---

### Post by austincibulka on 2018-08-27
> **Temüjin said:**
> Try this:
```
rm -rf ~/.config/pulse*; pulseaudio -k
```

I get the following error when I run that in the terminal:

```
E: [pulseaudio] main.c: Failed to kill daemon: No such process
```

---

### Post by austincibulka on 2018-08-28
Are there any other suggestions for my issue?

---

### Post by austincibulka on 2018-08-30
Bump

---

