---
title: "Firefox no sound - youtube - HDMI implications?"
date: 2017-08-23
forum: General Help
---

### Post by candtalan on 2017-08-23
Ubuntu 16.04, 32bit, updated including firefox. Problem is there is no sound from youtube videos recently. Sound is ok from chromium browser, and opera browser. Sound tests in system are ok, mp3, mp4 files - sound ok via VLC. 
I have uninstalled & reinstalled firefox after removing the profile files. no improvement.
Flash is enabled, and there is no blocking of 'dangerous' stuff even.

I saw in AskUbuntu something which rang a bell for me. An unanswered question said he had used HDMI settings and following that a sound problem seemed to exist. 
I recall that I also had recently hooked up hdmi to a tv display and in order to get hdmi sound on the tv I had to set the laptop sound settings to hdmi not internal stereo.
IIRC the problem I now face is the fisrt time the laptop has been used to play youtube video since then, so I did not notice the problem earlier maybe.

from askubuntu: Sandeep Shiraskar:I had connected my laptop to PC. After changing the default sound settings from HDMI back to inbuilt speakers, I can play videos on laptop properly. However, the videos on youtube play with no sound. Please help. I have installed adobe flash plugins and codecs in ubuntu.

The only response in askubuntu is my reply: I find I have the same problem. I recall recently playing via hdmi & setting sound  for hdmi. Ubuntu 16.04, 32bit, firefox. All other audio ok - including youtube via chromium browser, and Opera browser

I would be grateful for suggestions, tia

---

### Post by candtalan on 2017-08-23
Solved
I found a clue in 
[https://askubuntu.com/questions/151870/no-sound-through-hdmi-to-tv](https://askubuntu.com/questions/151870/no-sound-through-hdmi-to-tv)

It pointed to Pulseaudio Volume Control, particularly noticing there were multiple Sound Profiles.

I saw the pulseaudio volume control was avilable via the Dash, and used it:

(sound profiles - pulseaudio volume control)

'configuration' tab, 
turn profile hdmi 'off'
built in audio:
profile:
analog stereo output
Just restarting Firefox I think was not sufficient.
finally restart machine

---

