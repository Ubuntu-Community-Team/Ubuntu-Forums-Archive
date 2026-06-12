---
title: "Is there a dedicated Ubuntu Sound Guide?"
date: 2021-02-28
forum: General Help
---

### Post by AR_Kozz on 2021-02-28
Broken sound is one of the worst recurring problems I've had in 15 years of ubuntu use. Currently I've had to restart Alsa after booting for the past year since upgrading to 20.04 and have yet to solve the issue.

This would be much easier to deal with if there were a manual. The Ubuntu wiki doesn't seem to feature one. There are a couple of troubleshooting guides, focusing on the usual restart-this and reconfigure-that remedies, bug reporting instructions, fixes for known issues that aren't mine. I just need to know how the whole thing works, where to look to see what it's doing wrong.

---

### Post by TheFu on 2021-02-28
There is a sound troubleshooter .... but the first things are:
a) post in the correct sub-forum - hopefully a moderator will move this post there.
b) run the sound info capture script that is linked near the top of the Multimedia subforum. This script will capture all the audio-related information about the system.

Since 18.04, I haven't needed to touch or even know that ALSA is underneath PulseAudio.  There is a GUI for PulseAudio - pavucontrol.  It shows all the inputs, all the outputs and which programs are currently using each.  About once a week, I have to restart the pulseaudio daemon because it crashes about every 8-14 days. But if you reboot weekly, that should keep it running sufficiently.  I've only needed 1 change to the "client.conf" file. .... 
```
$ more ~/.config/pulse/client.conf
enable-shm = no
```
That's it.  Before I disabled shared memory use, crashes happened much more often.

This assumes normal motherboard, standard, audio chips, no bleeding edge stuff or any high-end audio needs.  If you need those, look up jack-audio and follow those guides. That's my guess.

My needs are pretty simple.  I want speakers and my webcam mic to be used for meetings.  I want the speakers used for videos and music.  I avoid having multiple inputs and multiple outputs available to pulse.  But ....

Pulse wants to use the last audio output and input devices that it sees. Often, this means that by re-plugging a headset, both the headphones and microphone connected will be auto-selected for use by pulse. It can be a pain, if you want to use a different input or output than the last ones connected, but pavcontrol allows that control.  I work from the far-right tab towards the left to enable only the devices and modes for which I want used.

So ... run the audio-data-gathering script. It will post some output to a pastebin somewhere. Provide the link here. Wait a day and hope someone who can interpret it, does.

---

### Post by CatKiller on 2021-02-28
> **TheFu said:**
> Pulse wants to use the last audio output and input devices that it sees. Often, this means that by re-plugging a headset, both the headphones and microphone connected will be auto-selected for use by pulse. It can be a pain, if you want to use a different input or output than the last ones connected, but pavcontrol allows that control.

In case you're interested, that's configurable behaviour. The assumption of the default is that you're plugging something in because you want to use it, so there's a module that moves the streams to the new device when the new device appears. If you don't want to do that, you can just tell that module not to load by commenting out the line in the config file.

---

### Post by AR_Kozz on 2021-03-09
I see one stickied troubleshooting thread in that subforum. Is the script in there somewhere?

---

