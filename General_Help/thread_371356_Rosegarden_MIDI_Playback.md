---
title: "Rosegarden: MIDI Playback"
date: 2007-02-26
forum: General Help
---

### Post by zeroblitzt on 2007-02-26
Hey there.

I've been struggling over the past few days to get MIDI playback working, so I can actually get back to arranging/composing songs. 

Tonight I've made a new milestone: I've at least managed to make it so Rosegarden can IMPORT midis (for some reason it wouldnt let me before). I've been tinkering with QJackCTL to try and get audio play back to work, but no dice.

I mean, I *could* compose things and export them, and open them in Timidity, but that would be a waste of time, especially when I have to listen to my progress every few minutes.


All I can really tell you is:
-Soundblaster Audigy (comes up as CA106 in the Sound preferences menu)
-Ubuntu 6.06, latest kernel and kernel headers
-I have a bunch of ALSA packages installed...

---

### Post by zeroblitzt on 2007-02-26
Rosegarden is telling my the JackD server isnt active, but when I try to start it I get: the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
 
Any ideas?

---

### Post by zeroblitzt on 2007-02-27
:confused:

I managed to start JackD by doing "killall esd" but rosegarden STILL wont play sound. Also, JackD gave me a lot of xruns, which I think are bad.

---

### Post by legzelda on 2007-03-01
I was having a similar problem.  I followed the instructions located at [https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime).  Evidently, Ubuntu Studios will come out in April.  Until then, you can get this realtime kernel doing the trick.  

After following these instructions, you will need to restart your computer.  At boot, you should have the option to select the realtime kernel (I am using GRUB).  Rosegarden will still complain about the system resolution being too low, but I was able to compose and play back MIDI.  

Unfortunately, the sound still chops a bit and doesn't sound as great as I would like it to for my recording purposes.  Maybe someone can post a follow-up with more information about how to resolve this, even after using the realtime kernel?

I hope this helps!

---

### Post by legzelda on 2007-03-02
Hi again!  I was able to get the choppy sound problem fixed by following this advice taken from [https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo](https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo).  It offers advice on how to get MIDI set up on your system, so if anyone is still having problems, I would advise you follow those steps.

[INDENT][B]Reducing CPU usage

If TiMidity++ uses too much CPU on your slow machine, and you're running a version prior to Breezy Badger, try adding these lines to the start of /etc/timidity/timidity.cfg (you may need to create this file)

opt EFresamp=l        #use linear resampling
opt EFvlpf=d            #disable VLPF
opt EFreverb=d        #disable reverb
opt EFchorus=d        #disable chorus
opt EFdelay=d          #disable delay

On Breezy Badger and Dapper Drake, simply uncomment all the lines in the section of the file that deals with a slow CPU. However, one of the lines contains a mistake. The "opt no-antialias" line should read "opt --no-anti-alias" instead. Also, make "opt p32a" say "opt p64a" because 32 voices just isn't enough.[/B] [/INDENT]

Let me know if anyone has any more questions!

---

### Post by legzelda on 2007-03-07
Oddly enough, I booted into the non-realtime kernel the other day.  I still had the same warning message about the system timer being too low, but MIDI still played back just fine in Rosegarden.  I chose to do this because suspend mode caused my system to lock up using the realtime kernel.

---

### Post by gnowak on 2007-03-10
Hello Zeroblitzt, try out the solution at the bottom of this post: [http://www.ubuntuforums.org/showthread.php?t=337125&highlight=rosegarden+midi]("http://www.ubuntuforums.org/showthread.php?t=337125&highlight=rosegarden+midi")

---

