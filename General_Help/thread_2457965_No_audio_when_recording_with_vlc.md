---
title: "No audio when recording with vlc"
date: 2021-02-13
forum: General Help
---

### Post by t0p on 2021-02-13
I am checking out video recording with my laptop's built in webcam. I can get video okay, but I am getting no sound. I have tried the built in mic, and also an external mic that plugs into the 3.5mm headphone socket.  Neither seems to be recording.

In the setup for recording with vlc I have tried all the audio device names offered: hw:1,0 doesn't work at all, just gives me an error message:

[QUOTEYour input can't be opened:
VLC is unable to open the MRL 'screen://'. Check the log for details.
Your input can't be opened:
VLC is unable to open the MRL 'alsa://hw:1,0'. Check the log for details.
Your input can't be opened:
VLC is unable to open the MRL 'alsa://hw:1,0'. Check the log for details.][/QUOTE]

If I use the others offered - hw:2,0 and  hw:2,1 - the webcam records the video but there is no audio.

It seems that I could type in an audio device name, but I don't know how to find the device names for the built in mic or external mic. There is no /dev/audio in /dev, and the files in /dev/snd don't seem to be related to microphones - nothing there changes when I plug in my external mic.

Does anyone know what I need to do to get audio with my vlc recorded videos? I am using Ubuntu 18.04.5 LTS

Cheers,

t0p

---

