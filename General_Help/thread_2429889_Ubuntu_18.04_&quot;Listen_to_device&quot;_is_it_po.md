---
title: "Ubuntu 18.04 &quot;Listen to device&quot; is it possible?"
date: 2019-10-24
forum: General Help
---

### Post by dycilia on 2019-10-24
Hi, I'm coming from windows 7 and didn't wanna go to 10.
 So my question is, I play a lot of nintendo switch and like to listen to music as well, so on windows I used to "listen to device"   I had an audio cable plugged from my tv to my computer mic socket, and then I listened to that device and all the sound went through my computer so I could use my wireless headset and have all sounds, is it possible? c:
SO in other words I wont to listen to the audio from the mic device that is actually the sound from my nintendo switch c:

Thank you

---

### Post by CatKiller on 2019-10-24
Audio stream routing in Ubuntu is done by **PulseAudio**. The terms that you want to be looking for are that you want to **loopback** the input so that you can **monitor** it. You'll be able to set the volumes independently.

Gnome's built-in configuration options are quite limited, which is why I don't use Gnome, but there should be some PulseAudio utilities in the repositories that will help you set it up. Failing that, it's all ultimately controlled by text files.

---

### Post by dycilia on 2019-10-24
OKii, thank you, I got the loopback to work, but the sound is all distorted, any tips ? c:
 I'm Foruming as well ofc c:

---

### Post by Skaperen on 2019-10-24
try running [COLOR=#0000cd][FONT=courier new]**pavucontrol**[/FONT][/COLOR].  it gives you various GUI volume controls.  the output may be too high.  but you can adjust the input device or the main output depending on whether the mic source is too high or not.  i hope that your physical source is not overdriving the mic input.

---

### Post by dycilia on 2019-10-24
I fixed it, it had to do with mic boost, I had to turn it off as instructed in:
[https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Microphone_distorted_due_to_automatic_adjustment](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Microphone_distorted_due_to_automatic_adjustment)

Thank you for the help everyone c:

---

