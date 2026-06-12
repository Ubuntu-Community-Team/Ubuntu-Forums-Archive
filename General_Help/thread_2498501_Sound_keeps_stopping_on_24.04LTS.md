---
title: "Sound keeps stopping on 24.04LTS"
date: 2024-06-16
forum: General Help
---

### Post by andymccall2 on 2024-06-16
Hi,

I've recently reinstalled my machine with a clean install of Ubuntu 24.04LTS. Everything is working perfectly except for the sound.  My sound sound be output over HDMI to the display then my speakers plug into the display.  This is so I can swap between my PS5 and my PC with sound via the channel selector on the display. The sound works for while, but after a bit it will stop. I could be watching a YouTube video, pause the video, do something else, then when I go back to play the video I'll have no sound.  After this no sound works from any/all applications so I couldn't listen to Spotify etc either so it's system wide, not just Chrome that's the issue.  I've done all the usual checks - I've checked the output device is the correct one, the volume is correct etc.  If sound is supposed to be playing I can see the bar bounce up and down in the Settings -> Output page, so I know sound should be playing. While I'm perfectly comfortable with Linux, most of my experience is server side and I've done practically nothing with audio, so I'm a little bit stuck as to how to debug this issue.  Here's as much information as I can think of providing and if anyone is able to help me I can can run whatever commands I need to to give more info.

Here are the things I've tried to do. Force reloading ALSA doesn't help:

```

root@earth:/var/log# alsa force-reload
Unloading ALSA sound driver modules: snd-seq-dummy snd-hrtimer snd-soc-avs snd-soc-hda-codec snd-hda-ext-core snd-soc-core snd-hda-codec-realtek snd-compress snd-hda-codec-generic snd-hda-codec-hdmi snd-pcm-dmaengine snd-hda-intel snd-intel-dspcfg snd-intel-sdw-acpi snd-usb-audio snd-hda-codec snd-hda-core snd-usbmidi-lib snd-ump snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hrtimer snd-hda-codec-realtek snd-hda-codec-generic snd-hda-codec-hdmi snd-hda-intel snd-intel-dspcfg snd-intel-sdw-acpi snd-usb-audio snd-hda-codec snd-hda-core snd-usbmidi-lib snd-ump snd-hwdep snd-pcm snd-rawmidi snd-seq snd-seq-device snd-timer).
Loading ALSA sound driver modules: snd-seq-dummy snd-hrtimer snd-soc-avs snd-soc-hda-codec snd-hda-ext-core snd-soc-core snd-hda-codec-realtek snd-compress snd-hda-codec-generic snd-hda-codec-hdmi snd-pcm-dmaengine snd-hda-intel snd-intel-dspcfg snd-intel-sdw-acpi snd-usb-audio snd-hda-codec snd-hda-core snd-usbmidi-lib snd-ump snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.

```

Reloading pipewire also doesn't resolve it:

```

andymccall@earth:~$ systemctl --now --user restart pipewire pipewire-pulse

```


System:

```
root@earth:/var/log# lsb_release -a | grep Description
Description:    Ubuntu 24.04 LTS

```

Devices:

```
root@earth:~# lspci | grep udio
00:1f.3 Audio device: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31)
01:00.1 Audio device: NVIDIA Corporation GP107GL High Definition Audio Controller (rev a1)

```

List of devices under aplay:

```

root@earth:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [LC27G5xT]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


```

andymccall@earth:~$ cat /proc/asound/cards 
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xdf320000 irq 132
 1 [Kiyo           ]: USB-Audio - Razer Kiyo
                      Alpha Imaging Tech. Corp. Razer Kiyo at usb-0000:00:14.0-4, high speed
 2 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdf080000 irq 17

```

At the moment the only way I can get sound working again is to restart the machine, which kinda sucks!

Please help!

---

### Post by currentshaft on 2024-06-16
Anything in the output of "sudo dmesg" or /var/log file contents when this happens?

---

### Post by andymccall2 on 2024-06-17
There's nothing of note in dmesg or any of the log files.

How do I restart the full audio system without rebooting? Maybe that will get it working. I think I might have been doing it wrong.

---

### Post by kprist on 2024-10-21
> **andymccall2 said:**
> There's nothing of note in dmesg or any of the log files.

How do I restart the full audio system without rebooting? Maybe that will get it working. I think I might have been doing it wrong.

I have almost the same issue with my setup, I have found that is  specific to my monitor setup at work, which is connected via USB-C, as I  don't have this issue with my home setup, where I use the HDMI  connection. However I don't have to restart my computer to get it fixed  when it happens. What I do instead is lock the session using Super+L,  then it automatically redirects the sound to speakers as the monitors  enter sleep mode, and then when they get back up, it works. Have you  tried that?

---

### Post by sben1783 on 2024-11-18
I also have this or a very similar problem. For me it helps to add a second device, and, when sound stopped playing, switch the output device to the second one which immediately works, and when switching back to the original device, this also works again!

When running `systemctl status --user pipewire` I'm seeing such messages (which are also in syslog, pls excuse the german parts I'm not sure why it's using this in syslog...):
```

[FONT=monospace]spa.alsa: front:1p: (125 suppressed) snd_pcm_avail after recover: Datenübergabe unterbrochen (broken pipe)
[/FONT]
```[FONT=monospace]
Any help is much appreciated. Thx!
[/FONT]

---

### Post by sben1783 on 2024-11-18
Looks like I found a solution (?), you will find plenty of pages around the "headroom" setting. For me, it looks like the problem is gone after increasing this headroom by editing /usr/share/wireplumber/main.lua.d/50-alsa-config.lua, uncomment the [FONT=monospace][COLOR=#000000]["api.alsa.headroom"][FONT=arial] line and adjust the setting to a higher value (I chose 2048 for now but have also seen values like 8192 as well). Good luck![/FONT][/COLOR]
[/FONT]

---

### Post by ubto66 on 2024-11-30
I do not have a solution for the error. On debian 12 a similar error occurred. Playing a video in a browser and the speakers would at some point stop working. The sound error never occurred on previous versions of debian. In sound preferences -> hardware the profile would be something analog stereo. You would then select
another profile. Then again select an analog stereo profile. Speaker sound would then return
for a couple of minutes. And you would have to do the sound profile jumping again. Hdmi sound would
always work. And headphones too. Asking around I noticed that disappearing sound was a known
error. And it could take many variations. Sometimes people had no hdmi sound, sometimes no external speaker
sound. All kind of sound errors. I tried different sound settings and sound server software. Nothing
worked. At some point speakers on the computer worked again when playing videos in
the browser. I am not able to say why. I suspect it was a browser update or kernel update. Why
else would the speakers work again?

---

