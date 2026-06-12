---
title: "No sound in Battle for Wesnoth 1.4.3"
date: 2008-06-28
forum: General Help
---

### Post by billdotson on 2008-06-28
I downloaded and installed the necessary packages for Wesnoth 1.4.3.  I started the game and everything appears to work fine except there is no sound at all.  I looked at the sound settings and they were all the same and it wouldn't let me change any of them.  I tested my sound by watching a youtube video and it works fine.

Thanks.

---

### Post by ajmorris on 2008-06-29
hi there,
if you start wesnoth from a terminal, what errors do you get? just post the output here... Wesnoth probably uses OSS and your pulseaudio is not routing OSS to alsa properly.

AJ

---

### Post by billdotson on 2008-06-29
> bill@Bill:~$ wesnoth
Battle for Wesnoth v1.4.3
Started on Sun Jun 29 14:06:27 2008

Checking video mode: 800x600x32...
setting mode to 800x600x32
set locale to ''
set locale to ''
loadscreen: filesystem counter = 107
loadscreen: binarywml counter = 31998
loadscreen: setconfig counter = 44
loadscreen: parser counter = 240

I don't see anything fishy about that output (scratches head).

---

### Post by ajmorris on 2008-06-30
> **billdotson said:**
> I don't see anything fishy about that output (scratches head).


Damn, i still think pulseaudio is at fault... i have never used PulseAudio before, and dont really know much about it... but if pulseaudio is at all decent, there should be some sort of tool to force alsa instead of OSS, perhaps contained in the alsa-plugins-pulseaudio package? You could also look through the commands if you run the pulseaudio binary with --help after it, however, someone else here will know how to force alsa instead of OSS.

AJ

---

### Post by billdotson on 2008-06-30
Everything with commands/lines, etc. is talking about default.pa located in /etc/pulse

I tried two sets of lines for ALSA:


First one:
> load-module module-alsa-sink device=default
load-module module-alsa-source device=default


along with commenting out these lines

> load-module module-hal-detect
load-module module-detect

and:

> load-module module-alsa-sink
load-module module-alsa-source device=hw:1,0
without commenting the lines mentioned earlier.  

With both of those setups I tried having the mixer be the ALSA one and the OSS one.  No luck with either.  The sound test worked, but Wesnoth won't even let me change the sound levels; I don't think it detects a sound device or something.

I also tried these lines for OSS:
> 
load-module module-oss device="/dev/dsp" sink_name=output source_name=input
load-module module-oss-mmap device="/dev/dsp" sink_name=output
again without commenting the lines mentioned earlier (the HAL one and the other one).  I also tried the OSS mixer and the ALSA mixer with this as well.

If I change my sound output, recording stuff, etc. to pulseaudio in the sound settings (System > Preferences > Sound) and test the "seound events" it I get an error that reads: > audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

For music and movies:
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect: Connection refused

For audio conferencing/sound playback:
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect: Connection refused

I don't think pulseaudio is working or it is at least interfering with Wesnoth's ability to use sound.  I am going to install Wesnoth on my Ubuntu Gutsy install and see if it does it there (I don't think Ubuntu Gutsy uses pulseaudio, but I could be wrong)

---

### Post by billdotson on 2008-06-30
I went to Ubuntu Gutsy and installed the version of Wesnoth that was in the repos.  I tried installing 1.4.3 from the .deb's I have but it would not let me.  Even after installing libboost-iostreams1.34.1 (the dependency the .deb installer says is the dependency that cannot be met).  Anyway, the sound is working with this.  I think it has something to do with Ubuntu Hardy, which seems to have caused more problems for me in other things as well >:-|

---

### Post by billdotson on 2008-07-01
I was just looking through the options in the pulseaudio applet and then I decided I would try wesnoth.  I ticked the sound on and it worked.  I then turned pulseaudio off (unless it automatically turned itself back on) and the sound still worked.  The sound, while working, isn't very good.  It is very shaky and scratchy; it does not do this in Ubuntu 7.10 or Windows XP SP2.

---

### Post by Oldsoldier2003 on 2008-07-25
do you have wesnoth-music installed?

---

### Post by sdennie on 2008-07-26
Along with what oldsoldier2003 said, you may want to try the following: 1) Go to System->Preferences->Sound and change all sound output to ALSA instead of pulse audio.  Make sure sound is working properly still (you may have to close all sound related apps first) by trying to play a youtube video and an mp3 in totem/rhythmbox and verify you can hear sound in both apps.  Try running wesnoth again now.  2) If that doesn't work, try starting wesnoth from the command line but proceeding it with the aoss command (this takes OSS programs and pipes them to ALSA):

```

aoss wesnoth

```

---

### Post by billdotson on 2008-08-02
thanks I will try that.

---

