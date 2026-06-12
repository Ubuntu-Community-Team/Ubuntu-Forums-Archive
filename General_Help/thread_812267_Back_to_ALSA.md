---
title: "Back to ALSA"
date: 2008-05-29
forum: General Help
---

### Post by C64MAN on 2008-05-29
Hi all!

When I installed hardy on my box, i have sadly noticed that alsa has changed to pulseaudio. With alsa my soundcard (SB Live 5.1) worked very well... The quality of the sound was huge. But now, with pulseaudio it sounds like sh*****. :( Is it possible to remove pulseaudio, and set up ALSA? If yes, how? (If not, why?)

Thank You in advance!
C64MAN

---

### Post by sdennie on 2008-05-29
You should be able to set everything to use ALSA by going to System->Preferences->Sound and switching things from whatever the default is to explicitly be ALSA.

---

### Post by ibuclaw on 2008-05-29
Go into **System>Preferences>Sound** in the GNOME menu and change all "**sound playback**" dropdown-bars from "PulseAudio Sound Server" to 
"**ALSA - Advanced Linux...**".

Changing it to your actual soundcard works well too.

Although, first. I recommend that you give asoundconf a try before you do this!
```
sudo apt-get install asoundconf-gtk
```
Then go into "**System>Preferences>Default Sound Card**" and set it to "**default**" and quit.
Everything should take effect once you close all sound apps.
But, just incase, reboot your computer and then test it out then.

Regards
Iain

---

### Post by C64MAN on 2008-05-29
I had tried it once, but it didn't work. But now it works perfectly. (Mysteriously...) Thank you.

---

