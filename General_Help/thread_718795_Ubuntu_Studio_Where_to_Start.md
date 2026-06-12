---
title: "Ubuntu Studio: Where to Start"
date: 2008-03-08
forum: General Help
---

### Post by Th3Professor on 2008-03-08
Hi all!

I have a fresh install of Ubuntu Studio and am wondering if anybody out there, who has used the applications that are in it, if anybody can give pointers on where to start?

I know I can just dig in and randomly start discovering new programs and such. However, I'd like to hear from you, from your experience, a possible plan of attack for getting acquainted with the system.

I'm interested in, at some point, using all of the features, including graphics and video.

My main interest is in the music/audio features, which I will be spending a lot more time with.

I'll list everything that I currently have in audio production.
(Applications --> Sound & Video --> Audio Production)

If you were to put these in an order, like "familiarize yourself with the applications in this order" (perhaps some are more important to learn first), what order would you put them in?

Here's my current list, in alphabetical order (as is in the menu)...

[list]
[*]Aconnectgui
[*]Aeolus
[*]Ardour GTK2
[*]Audacity Sound Editor
[*]BEAST
[*]Bitscope
[*]Creox c
[*]Freebirth
[*]GNU Denemo
[*]Gtick
[*]HDSPConf (I don't think this one works on my pc)
[*]HDSPMixer (I don't think this one works on my pc)
[*]Hydrogen
[*]Jackbeat
[*]JACK Control
[*]JackEQ
[*]JACK Rack
[*]JACK Timemachine
[*]JAMin
[*]Meterbridge
[*]Mixxx
[*]MusE
[*]Patchage
[*]PureData
[*]QAMix
[*]QSynth
[*]Rosegarden
[*]Seq24
[*]SooperLooper
[*]Sound Recorder
[*]terminatorX
[*]Virtual MIDI Keyboard
[*]ZynAddSubFX Software Synthesizer
[/list]

Thanks!
:guitar:

---

### Post by Stochastic on 2008-03-08
hmm well as with all areas of software each tool is designed for a different task therefore the ones you should get to know first would be the ones that help more with the tasks you're looking to work on...

but in order of importance for myself here's a shorter list:

-JACK Control (get to know jack, it's god)
-Ardour GTK (multitrack DAW)
-Audacity (this program I never use, but it's the only wave editor in your list.  I always work in Rezound, but it's not part of your list right now)
-JAMin (mastering tool)
-Hydrogen (drum machine)
-JACK Rack (realtime effects)
-ZynAddSubFX (synth)
-QSynth (soundfont synth)
-Mixxx (I prefer XWAX, but I'm a dj with turntables - not for everyone)
-PureData (this takes a while to get to know, but it's REALLY POWERFUL!!!)
-Rosegarden (okay, most people would have this higher on their list, it's a midi/audio composition tool, similar to Cuebase.  I just rarely use it)


the rest do have great features but it comes down to what you want to do as to how useful they'll be

---

### Post by Th3Professor on 2008-03-08
...hmm... this thread has been moved from "Multimedia Production" to "General Help".

Any input (on suggestions, recommended order to get familiar with the apps, etc.) is welcome. Thanks! :)

---

### Post by Th3Professor on 2008-03-08
> **Stochastic said:**
> 
-Audacity (this program I never use, but it's the only wave editor in your list.  I always work in Rezound, but it's not part of your list right now)


Hmm, I installed ReZound... it crashes when I try to use it (after setting up a couple tracks and hitting record). Any ideas? [confuzzled]

---

### Post by Stochastic on 2008-03-09
start it from a terminal and then check the terminal after the crash to see what error message it gave you.  It's probably something to do with which temp directory you have selected, or maybe a soundcard i/o issue.

---

### Post by Th3Professor on 2008-03-10
> **Stochastic said:**
> start it from a terminal and then check the terminal after the crash to see what error message it gave you.  It's probably something to do with which temp directory you have selected, or maybe a soundcard i/o issue.

Ah okay... for some reason it's attempting to write to / (or so it appears).

Here's what turned up:
```

$ rezound 
using path '/usr/share/rezound' for share data directory
'lame' executable not found in $PATH -- mp3 support will be disabled
If rezound dies unexpectedly while seeking with the keyboard, auto-repeat may be disabled.. if this happens run 'rezound --fix-auto-repeat'
cannot write to working directory candidate: / -- Permission denied
cannot write to working directory candidate: / -- Permission denied
Segmentation fault (core dumped)
$ 
```

On a side note, I thought I had "LAME" but it turns out not, so I went ahead and did an install on it. Though, I'm guessing that's not what caused the crash.

I don't presently have a keyboard connected - is it required to even record?

Thanks again! :)

---

