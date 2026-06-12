---
title: "Probably a pulseaudio/alsa question: sound card to sound card?"
date: 2022-11-12
forum: General Help
---

### Post by Rocket J Squirrel on 2022-11-12
Ubuntu 20.04 running Pulseaudio and Alsa, not running JACK

So I have two USB audio interfaces. One ("soundcard_1") has an FM tuner connected to it. The other ("soundcard 2") drives my external speakers. With applications like Audacity I can capture the FM tuner's audio from soundcard_1 and record it. And likewise, applications like Audacity will cheerfully play back audio to my speakers through soundcard_2. Pavucontrol's "Input Devices" tab shows the FM tuner audio coming into soundcard_1, and it shows the audio going to soundcard_2  in the "Playback" tab when I use it to play back from applications.

I'd like to listen to the FM broadcast on my speakers. How can I pipe soundcard_1's Input Device directly to soundcard_2's Output Device. Possible without JACK?

Thank you.

---

### Post by &amp;KyT$0P# on 2022-11-12
I'd start with running this in Terminal
```
pactl load-module module-loopback
```
then tweaking stuff in pavucontrol if needed

---

### Post by Rocket J Squirrel on 2022-11-12
Sweet. So

```
$ pactl load-module module-loopback
30


```

Not very exciting, but let's see if anything new is available in pavucontrol ... hm, not seeing anything useful. It still shows the audio on the Input Device, but no monitor for it. I'm not sure where to go from here to pipe soundcard_1's Input Device to soundcard_2 as an output device so I can hear soundcard_1 on soundcard_2. I'm probably overlooking something simple. 

Thank you!

---

### Post by HermanAB on 2022-11-13
I would use sox for this. Google will quickly find millions of sox tutorials

---

