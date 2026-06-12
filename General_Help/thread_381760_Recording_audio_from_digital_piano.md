---
title: "Recording audio from digital piano"
date: 2007-03-11
forum: General Help
---

### Post by TheKingofZZT on 2007-03-11
Hi all,

Recently I got an X30 Kawai Piano. This model is kinda old, and doesn't have USB/Seriel/MIDI out, instead it has 1/4" out. Yesterday I went to RadioShack and got the 1/4" to 1/8" converter and enough wire to connect the two machines.

My computer is an HP S4000V and I have the Piano attached to "Line In" and my Microphone attached to "Microphone" - The Mic has OK quality (it's kinda cheap anyways)

Now, when I try to record audio from my keyboard, this is where the problem is: Horrible quality. When I plug my headphones directly into the keyboard it's fine, but when I connect the keyboard to the computer, we get pretty bad quality. (It has the bad quality over the headphones as it's played live and worse when I record via Audacity)

I can try to get you all a sample file, settings, etc, I don't really know what to provide right now since I don't have much experience with this.

Thanks,
Isaac.

Edit: Bad quality is only when recording in Audacity

---

### Post by chocolatemintmocha on 2007-03-28
I had a similar issue. When I tried to record in audacity it would have crappy quality and a hiss. It took me forever to figure it out, but I eventually found a link on the audacity site which explained it. My understanding is that audacity uses OSS sound driver by default and ubuntu uses ALSA by default. Assuming this is the problem, all that you have to do is go to synaptic and search "aoss", without quotes. Then download alsa-oss.
Then go to your terminal and type "aoss audacity". Then double click on the volume control, which is on the top bar of the screen by default. then click on the capture tab, and make sure the recording volume is up. Then test out recording in Audacity![http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by TheKingofZZT on 2007-03-28
> **chocolatemintmocha said:**
> I had a similar issue. When I tried to record in audacity it would have crappy quality and a hiss. It took me forever to figure it out, but I eventually found a link on the audacity site which explained it. My understanding is that audacity uses OSS sound driver by default and ubuntu uses ALSA by default. Assuming this is the problem, all that you have to do is go to synaptic and search "aoss", without quotes. Then download alsa-oss.
Then go to your terminal and type "aoss audacity". Then double click on the volume control, which is on the top bar of the screen by default. then click on the capture tab, and make sure the recording volume is up. Then test out recording in Audacity![http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

Hm, I've tried aoss audacity, but now I can't seem to record anything - Do I have to double click some special place? I can hear the audio from "line" playing through my headphones, probably via ALSA, so I know I'm getting a signal.

---

