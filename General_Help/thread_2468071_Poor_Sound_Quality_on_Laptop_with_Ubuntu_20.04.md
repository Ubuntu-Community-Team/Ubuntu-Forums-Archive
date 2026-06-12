---
title: "Poor Sound Quality on Laptop with Ubuntu 20.04"
date: 2021-10-17
forum: General Help
---

### Post by bicycleshow on 2021-10-17
I have Ubuntu 20.04 installed on a Dell Inspiron 15 3000 laptop. I get poor, tinny, blown-out sound quality at all volume levels whenever I try to play a video on Brave browser or whenever I play a video on Firefox other than on Youtube or whenever I play a downloaded webm or mp4 or such. Very occasionally those videos will play fine, but rarely.
I can, however, get the audio to sound good if I play a youtube video, then switch to the other video I want to play and play it simultaneously with the youtube video. After I pause the youtube video, the other video plays with good sound until I pause it.

Fixes that I've tried so far from searching online that haven't worked include downloading PulseAudio to check if the configuration is correct. I believe it is. The only two options that work with my laptop speakers are Analog Stereo Duplex and Analog Stereo Output and both still produce the tinny sound. I also tinkered with the output levels to make sure it wasn't set too high.

I've also tried editing the config file on pulseaudio following this guide:
[https://askubuntu.com/questions/1108825/laptops-speakers-sound-bad-poor-sound-quality](https://askubuntu.com/questions/1108825/laptops-speakers-sound-bad-poor-sound-quality)
It also didn't fix the problem.
Any suggestions?

---

### Post by bicycleshow on 2021-10-18
I've also attempted to use PulseEffects to mess with the audio. It seems like the primary source of the tinny sound is from the bass, however PulseEffects doesn't seem to actually fix the sound quality but simply make it quieter. Laptop is Inspiron 3501 with Realtek ALC3204 sound card.

---

### Post by robingarner on 2021-10-18
I'm an article writer and I've been using ubuntu for quite awhile but never experienced anything like this ever before, If anyone finds a solution to the bad sound quality pls help!!

---

### Post by bicycleshow on 2021-10-19
What's really strange is that I can "fix" the issue by playing a video that gets good sound quality over top of a video that has terrible sound quality. (Almost always a youtube video, but very rarely webms or mp4s will play normal audio as well) I'm not very adept with computers but this leads me to believe it's something to do with how the sound card is processing the audio signal perhaps? And for whatever reason, playing a video with good sound and then the video with bad sound in a way forces the sound card to play both correctly? It's very strange. None of the other typical fixes for similar issues that I've found online have helped at all.

---

### Post by bicycleshow on 2021-10-25
Edit: So after doing more digging, I finally found something that seems to address my issue, but doesn't help right now.
It seems that the current kernel 5.11 doesn't play nice with my audio card and many other people's on other dell and lenovo laptops. Hopefully a future kernel update will resolve this issue for us.

---

### Post by tea for one on 2021-10-26
In order to verify your research, it's probably expedient to download Ubuntu 21.10 which uses a later kernel 5.13.
Boot into a live session and test?

---

### Post by ActionParsnip on 2021-10-26
What is the output of:
```

wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh && chmod +x ./alsa-info.sh && ./alsa-info.sh

```
Thanks

---

### Post by bicycleshow on 2021-10-28
> **tea for one said:**
> In order to verify your research, it's probably expedient to download Ubuntu 21.10 which uses a later kernel 5.13.
Boot into a live session and test?
Thanks for the advice, I'll give that a try as soon as I'm able to.

Output of ALSA information: [http://alsa-project.org/db/?f=362f9572760d390f71a1c31199bce974376c57b1](http://alsa-project.org/db/?f=362f9572760d390f71a1c31199bce974376c57b1)
Appreciate you taking a look at it.

---

### Post by bicycleshow on 2021-11-29
Just to give an update. I finally got around to trying out Ubuntu 21.10 on a live install this weekend and that seems to have fixed the issue.

---

