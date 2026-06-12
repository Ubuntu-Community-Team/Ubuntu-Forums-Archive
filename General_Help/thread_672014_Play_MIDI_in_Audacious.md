---
title: "Play MIDI in Audacious"
date: 2008-01-19
forum: General Help
---

### Post by Sonja on 2008-01-19
Can somebody tell me step by step exactly how to set up Audacious to play MIDI files?

---

### Post by Sonja on 2008-01-19
I typed:

```
sudo apt-get install audacious-plugins-extra
```

And now MIDIs can open with Audacious and appear to be playing, but zero sound comes from them.

---

### Post by Melcar on 2008-01-22
I can't get it to work either.  I can use Timidity thought.  In Kubuntu I managed to get Kmid and Timidity working, but I really don't want to resort to KDE apps. for my Gnome PC.

---

### Post by FuturePilot on 2008-01-22
What is your sound card and what backend to AMIDI are you using?

---

### Post by Melcar on 2008-01-22
Mine is an Audigy2 Value, so I need software synthesis.  Audacious seems to only work with Fluidsynth, but it doesn't work for me.

---

### Post by Dr Small on 2008-01-22
Here is FuturePilot's guide on how to do it, from his blog;
[http://linuxtechie.wordpress.com/2008/01/22/how-to-ubuntu-midi-playback-with-audacious/](http://linuxtechie.wordpress.com/2008/01/22/how-to-ubuntu-midi-playback-with-audacious/)

Dr Small

---

### Post by Melcar on 2008-01-22
Thanks, that worked.  According to that guide my card (Audigy2 Value) should be able to do hardware MIDI decoding, but I can't get it to work.  Doesn't really matter though, since my CPU is beefy enough to handle it.  One thing though, playback seems choppy; that doesn't happen with Timidity

---

### Post by FuturePilot on 2008-01-22
Yes, the choppy playback may be normal with FluidSynth
> Q. 
I'm using the FluidSynth backend and I noticed that the song skips once in a while (or even often)... how can I prevent this?

A. 
Since FluidSynth is a software synth and it uses your CPU, the first thing to do is to ensure that your system is not doing other CPU-intensive tasks during playback. That said, you can use change the FluidSynth backend buffer parameters in the preferences dialog. Try to move the "handy buffer tuner" some steps to the right until playback is fluid again.

[http://www.develia.org/projects.php?l=2&p=amidiplug#faq]("http://www.develia.org/projects.php?l=2&p=amidiplug#faq")

@ Dr Small Thanks  ;)

---

### Post by Melcar on 2008-01-22
Yeah.  After some tweaking of the "handy" bar I got it to work.

---

