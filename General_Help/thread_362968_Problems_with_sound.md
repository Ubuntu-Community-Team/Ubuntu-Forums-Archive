---
title: "Problems with sound"
date: 2007-02-16
forum: General Help
---

### Post by Forseti on 2007-02-16
Hello,

I've got periodic problems with sound thorought my GNOME. With about 50% chance my computer boots with no sound effects (say for checkbox clicks) nor multimedia sounds. 
The hardware gets detected (it's integrated with my Gigabyte GA-K8N mainboard) but when I start Totem, or any other GNOME app dealing with sound it says: "could not open resource for writing". Also, tried mpg321 to play sample MP3 file which gave: 

Playing MPEG stream from milosc.mp3 ...
MPEG 1.0 layer III, 128 kbit/s, 44100 Hz joint-stereo
ALSA snd_pcm_open error: No such file or directory
Link points to "/tmp/ksocket-forsetius"
can't create mcop directory

'forsetius' is user with admin privileges.

Tried rebooting but not helped. It seems that only after more time computer spends resting  the sound comes back. What's also interesting I can perfectly hear cracking sounds due to my hard disk working in my monitor's speakers.
Any ideas?

-- 
Forseti

---

### Post by JustinAlf on 2007-02-16
Check out Preferences->Sound-> and enable your ESD

---

### Post by JustinAlf on 2007-02-16
nm i didn't read your whole post, that probably is not the problem

---

