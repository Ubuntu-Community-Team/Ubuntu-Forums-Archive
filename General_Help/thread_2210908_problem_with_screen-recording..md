---
title: "problem with screen-recording."
date: 2014-03-13
forum: General Help
---

### Post by TheUninvited on 2014-03-13
so whetever program i installed or run through online it records the video but not the audio...

I am trying to record some anime...

---

### Post by TheUninvited on 2014-03-17
just a small bump.

---

### Post by ralph-beeby on 2014-03-17
Any idea what this program is? I've no experience with screen-recording, but I have done a bit of audio recording in Ubuntu. You may want to check your audio settings, and make sure the computer's recording input and your video software are both connected to the same device! Bring up a terminal and head to
```
$ alsamixer
```
Have a look at the different levels it brings up and see what the recording input is set to:
- one possibility is that the recording level is turned off (for whatever reason). 
- another is if your soundcard can switch between Mic and Line level recording inputs - you should be able to toggle this in alsamixer if it can. It's worth comparing that to the audio settings in your video software. E.g., if you're recording at Line level, but your software is expecting a Mic level signal, it may just be receiving an incredibly weak audio signal.

---

### Post by monkeybrain20122 on 2014-03-17
What program do you use? Did you try kazam? It is in the repository for 13.10 +, for 12.04 from ppa [https://launchpad.net/~kazam-team/+archive/stable-series](https://launchpad.net/~kazam-team/+archive/stable-series) 
It records audio and video and works very well in Ubuntu.

You may also want to install pavucontrol (pulse audio volume control) and look at the audio settings.

---

