---
title: "no sound with sound blaster live"
date: 2005-10-14
forum: General Help
---

### Post by carl903 on 2005-10-14
just installed 5.10 Flawlessly aside from no sound. Anyone can give me advise on a driver and how to install i would appreciate it!!sound blaster live 24

---

### Post by panocrat on 2005-12-03
carl, i have the same problem. i haven't got it working yet, but google on ALSA; there are some drivers for the card there. it's no easy fix, as i've had to install a number of other linux packages to even get to the point where i could do what's suggested on the ALSA site. but maybe you'll have more success than i've had!

---

### Post by hw-tph on 2005-12-03
There are a few different versions - some are not even emu10k-based. Try **sudo lspci** to see what kind of soundcard it really is.

---

### Post by panocrat on 2005-12-03
trying sudo lspci gives me this:

0000:01:0d.0 Multimedia audio controller: Creative Labs SB Audigy LS

which is the same driver on the ALSA site as the Live! 24 bit. read somewhere the cause of the problem may be that the card is on board the motherboard (msi k8n sli platinum for me)

---

### Post by panocrat on 2005-12-03
6 hours of pissing around paid off, the card now works; had to mute the SPDIF out.

---

### Post by muted on 2005-12-04
[QUOTE=panocrat]6 hours of pissing around paid off, the card now works; had to mute the SPDIF out.[/QUOTE]
which is located where?

---

### Post by panocrat on 2005-12-04
volume control/switches. i don't know what i did to get the volume control working, because until recently it wasn't there in the form it is now. 

i think installed in the earlier and later GCC packages made a difference; i followed the instructions from ALSA 3 or 4 times, and got less error messages when i had GCC 3.4 installed along with GCC 4.

---

### Post by teshue on 2006-02-25
Hey there guys.

I got this video card (Soundblaster Live! 24-Bit) yesterday and was having a HELL of a time getting it to work. I was running Ubuntu version 5.04 at the time. Last night I upgraded to 5.10 Breezy Badger. After installing I noticed that ALSA already seemed to be configured for the most part. So all I did was the following:

1. System >> Preferences >> Sound
2. In the "Default Soundcard Box" choose "CA0106" and close.
3. Double click the volume control in the upper right hand corner, this should open up the Volume Control. 
4. Click the "File" tab, then "Change Device", then click "CA0106".
5. Then click the "Edit" tab, then "Preferences".
6. Check all the boxes available, then close this.
7. In the Switches tab, make sure the "SPDIF Out" box is left unchecked.
8. Turn up the volumes in the "Playback" tab. And Presto!

That's all I did, and it seems to be working pretty damn good now. This is what I did to get it working, maybe it can be of some help to some of you folks.

---

