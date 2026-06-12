---
title: "No sound in xubuntu"
date: 2008-05-18
forum: General Help
---

### Post by enoughsaid05 on 2008-05-18
Hi all

I initially used Gnome but I installed xubuntu-desktop to try out xfce

There was sound in Gnome but not in xubuntu. How do I solve the problem?

Thanks in advance

---

### Post by enoughsaid05 on 2008-05-18
Hi all... any response??

---

### Post by Bakker on 2008-05-18
What kind of sound are you expecting? XFCE doesn't really have any interface or event sounds. 
Is sound even enabled in xfce4-mixer?

---

### Post by enoughsaid05 on 2008-05-18
As in cannot play mp3 songs.

My xfce4-mixer have all been tuned to the maximum volume, but still no sound...

---

### Post by t4ggs on 2008-05-18
Do you have the mp3 codecs installed??

---

### Post by Fibonacci on 2008-05-18
Is your MP3 player configured to output sound through PulseAudio? Try to set everything up to output through ALSA.

---

### Post by enoughsaid05 on 2008-05-18
Yep sure enough, my sound was configured to use Pulse Audio

I have changed to Alsamixer. Things are working fine! Thanks!

---

### Post by dgavenda on 2008-09-13
enoughsaid05,

I have the same exact problem: sound is great in ubuntu but nothing in xubuntu.  How did you change xfce to use alsa?  

Thx,
Dan

---

### Post by Sam Lars on 2008-10-14
I'm pretty sure it's here:
Right click on the desktop, go to settings (at the top), and then Multimedia Systems Selector.
I changed mine to Alsa, which gives me the test sound instead of an error, but Totem/Rhythmbox still no go.  Does it require a log out?

---

