---
title: "How to disable microphone gain auto adjust?"
date: 2015-01-18
forum: General Help
---

### Post by gd-comptes on 2015-01-18
Hello,

I am new to ubuntu and linux in general, and I am experiencing a very frustating issue with audio input gain level stability for which I could not find any real answer on the web.

I have plugged an audio device in the line-in connector of my soundcard. I am using pulseaudio loopback module in order to listen to this stream through my computer.
Very often the gain on this source just increases by itself. I have tried different settings in pulseaudio volume control, including unchecking "define as an alternative" for this source (as I thought maybe some application was trying to listen to it and might be tweaking the levels), but none seem to solve this issue.

Any idea of what I could try next?

---

### Post by tgalati4 on 2015-01-19
Sometimes "autogain" is a switch that can be found in Sound Preferences.  You will have to search for it.  Sometimes there is a setting in BIOS to define how the input works, Line, Mic, or Auto.

Install *pavumeter* so you can watch the sound levels.  Using loopback mode can increase the chance of feedback, since most computers have the speakers close to the microphone.  What is the audio device that you are using?  What are the output levels of this device?

---

