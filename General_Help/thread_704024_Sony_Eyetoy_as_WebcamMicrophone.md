---
title: "Sony Eyetoy as Webcam/Microphone"
date: 2008-02-21
forum: General Help
---

### Post by sharpnotflat on 2008-02-21
I have gotten my eyetoy to work on my Ubuntu Gutsy. I use the program "Cheese" and my webcam works. On audacity, my eyetoy acts like a microphone and works too. However, I cannot do multitrack recording. 

In the I/O Preferences, playback is set to ALSA: default. Recording is set to OSS: /dev/dsp1
and 2 channels (stereo). 

I start recording and finish recording successfully. It can playback loud and clear too. However, when I want to record again, it says:

Error while opening sound device. Please check the input device settings and the project sample rate.

So basically, I can't harmonize or rerecord over a recording, which makes the program very limited. I don't think I've configured my settings correctly, but setting the Recording device to my USB eyetoy won't record at all.

Can someone please help me so I can be like this dude: :guitar:

thanks.

---

### Post by chipants on 2008-02-22
sounds like your soundcard is not capable of full-duplex operation. meaning, it can't playback and record at the same time. or, at least, audacity thinks so. the first recording was just audio in, so it was fine. when playing back the first track, audio-in is disabled. this is fairly common with budget/integrated soundcards.

the confusing part is that the eyetoy is technically a separate audio interface, so it really shouldn't matter if your actual soundcard is full-duplex or not.

btw, doesn't your actual soundcard have a line/mic-in? multitracking with an eye-toy couldn't possibly sound too nice. right? even a cheap desktop microphone would probably be a better solution.

---

