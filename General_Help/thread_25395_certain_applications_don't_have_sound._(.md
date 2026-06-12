---
title: "certain applications don't have sound. :("
date: 2005-04-10
forum: General Help
---

### Post by graigsmith on 2005-04-10
audacity doesn't have sound.  dosbox doesn't. flash based games don't.

but i get sound fine in rhythem box, Gaim, i get system sounds. and they all play whenever they need to.

dosbox gives this error.

*****
CONFIG: Using default settings. Create a configfile to change them
MIXER:Can't open audio: No available audio device , running in nosound mode.
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ALSA:Can't open sequencer
MIDI:Opened device:none
******

audacity gives this error

*******
There was an error initializing the audio i/o layer. You will not be able to play or record audio.    Error: Host error.
*******

Also, audacity looks horrible, its all ugly, and the fonts are not rendered right.  eww looks like windows 3.1 or how a java applet looks in windows.

---

### Post by graigsmith on 2005-04-10
[QUOTE=graigsmith]audacity doesn't have sound.  dosbox doesn't. flash based games don't.

but i get sound fine in rhythem box, Gaim, i get system sounds. and they all play whenever they need to.

dosbox gives this error.

*****
CONFIG: Using default settings. Create a configfile to change them
MIXER:Can't open audio: No available audio device , running in nosound mode.
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ALSA:Can't open sequencer
MIDI:Opened device:none
******

audacity gives this error

*******
There was an error initializing the audio i/o layer. You will not be able to play or record audio.    Error: Host error.
*******

Also, audacity looks horrible, its all ugly, and the fonts are not rendered right.  eww looks like windows 3.1 or how a java applet looks in windows.[/QUOTE]
 how do i change my sound driver?

---

### Post by graigsmith on 2005-04-10
anyone have any idea why?

---

### Post by graigsmith on 2005-04-10
Would getting a different sound card help?  im using a usb soundcard right now.  I'm not going to be able to use linux without these 2 programs.  Im very close to being able to delete windows and use linux permanently.  I even got my wacom tablet working and believe it or not, it actually works better than it does in windows.  

if i compile my own dosbox- would this fix it?

---

### Post by sinbad782 on 2005-04-10
I got XMMS working - I had to choose the esound plugin (not ALSA or OSS) in order to get it to make any noise. 

Perhaps this might be the issue with the other programs - it might be worth a try looking under preferences and changing the driver used to enlightened sound daemon.

---

### Post by c_dog on 2005-04-10
First thing the try is go to System>Preferences>Multimedia Systems Selector>Audio and change the default sink to ALSA or OSS.

Give people a chance to answer your questions in the future. Seeing this many self-bumps usually just annoys those who may answer.

---

### Post by graigsmith on 2005-04-10
as far as i know, dosbox or audacity don't have plugins that can be used.  if i could just get dosbox sound working.  i would be happy.

---

### Post by graigsmith on 2005-04-10
[QUOTE=c_dog]First thing the try is go to System>Preferences>Multimedia Systems Selector>Audio and change the default sink to ALSA or OSS.

Give people a chance to answer your questions in the future. Seeing this many self-bumps usually just annoys those who may answer.[/QUOTE]
 
ok i did this, now i am only getting ubuntu sounds.

edit, ok i did what you said, then disabled the gnome sound server by going to system, preferences, sound,  and i unchecked enable sound server startup. 

now both dosbox and audacity work.  thanks Alot!!

---

### Post by graigsmith on 2005-04-10
heres an update.  i swapped the usb soundcard out, for my old soundblaster live card.  And it works much better.  All the programs work, without having to fiddle around with anything.  apparently the usb soundblaster requires a software mixer.  and the sound blaster live can do hardware mixing with alsa, so it doesn't require esd, and all programs work with it.   

so if your having similar problems, and you have a soundblaster live laying around, you might wanna stick that in there instead. 

thanks for the help everyone.

---

