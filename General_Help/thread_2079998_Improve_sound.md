---
title: "Improve sound?"
date: 2012-11-02
forum: General Help
---

### Post by ryanyeah on 2012-11-02
So when i listen to audio through headphones on a 12.04 install, it sounds very bland and if I try the same music on a Windows machine, it sounds a lot better. What are the things I can try to do to improve this?

I'm not sure what alsa is (it came up in a few google searches), but it seems like I may not be compatible with that due to my kernel version of 3.2.0-32-generic. Ideas?

---

### Post by gerowen on 2012-11-02
Alsa is one of the commonly used sound back-ends.  Ubuntu uses pulseaudio I believe as a front-end since there's a few different sound backends (alsa, oss, etc.).  There are a few different control applications for Pulseaudio, but I don't seem to see any of them that have mixer controls to adjust the quality of the audio.  Does audio sound better if you play it from a different program?  For example if you're using banshee or rhythmbox, does the sound improve if you use VLC or something else to play the same file?  How was the sound quality on this computer before Ubuntu, better, worse or the same?

---

### Post by ryanyeah on 2012-11-02
> **gerowen said:**
> Alsa is one of the commonly used sound back-ends.  Ubuntu uses pulseaudio I believe as a front-end since there's a few different sound backends (alsa, oss, etc.).  There are a few different control applications for Pulseaudio, but I don't seem to see any of them that have mixer controls to adjust the quality of the audio.  Does audio sound better if you play it from a different program?  For example if you're using banshee or rhythmbox, does the sound improve if you use VLC or something else to play the same file?  How was the sound quality on this computer before Ubuntu, better, worse or the same?

Thanks for the reply. Now that you mention it, I think I can notice a difference between rhythmbox and VLC. VLC seems to have more clarity and bitrate to it, even though it's playing the same file. I think the ability for me to add bass to the windows audio settings seems to improve the impression of quality, while ubuntu doesn't seem to let you adjust much. 

I've only had a high quality set of headphones since I've been running linux on my primary PC. But I have both ubuntu and Windows on my laptop, and there was a big difference in audio there (although, I only tested it with rythmbox on ubuntu).

---

