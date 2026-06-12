---
title: "USB Audio Problems"
date: 2008-03-01
forum: General Help
---

### Post by JNCR on 2008-03-01
I am running Ubuntu Gusty Gibbon, and I cannot get my SoundSticks working.  The sound card works perfectly, as in I can plug in headphones and get sound perfectly.  I know the soundsticks are working because when I do System > Preferences > Sound, and test the device "USB Audio" I get test sound out of my speakers.  Also, when I use XMMS (a media player), I am able to specify to use the SoundSticks using ALSA, and I get sound fine.  I am guessing what I need to do is change the default sound output to USB Audio. Thank you.

~JNCR

---

### Post by SpaceTeddy on 2008-03-01
i think what you are looking for is the programm gstreamer-properties

open up a terminal, and run the command. You can choose the default device for audio output for the gstreamer sink there...

hope it helps :)

---

### Post by JNCR on 2008-03-01
Ok I just changed the gstreamer-properties to plugin alsa and device USB-Audio, (in both my user and sudo) yet I still have no sound in firefox.  Is it firefox's error? should I set the audio in firefox to output to ALSA USB audio? should I restart the computer?

ps. in gstreamer-properties if I click test (while selection is set to ALSA and USB Audio) I get test sound out of my speakers

~jncr

---

### Post by SpaceTeddy on 2008-03-01
> **JNCR said:**
> Ok I just changed the gstreamer-properties to plugin alsa and device USB-Audio, (in both my user and sudo) yet I still have no sound in firefox.  Is it firefox's error? should I set the audio in firefox to output to ALSA USB audio? should I restart the computer?
~jncr

you need to restart at least your xserver, i think... but restarting the computer is the safe way... if that does not fix the problem, i am also out of ideas :) that was the only guess i had :)

---

### Post by JNCR on 2008-03-01
hmm yeah it didnt work

thanks anyway

---

