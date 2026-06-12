---
title: "Sound Mysteriously Stoppped Working in Feisty"
date: 2007-05-31
forum: General Help
---

### Post by FreakyT on 2007-05-31
Hey all,

I have two soundcards in my computer: A Soundblaster Live 5.1, and an integrated one.  (Made by RealTek)  When I first installed Ubuntu Feisty, both worked fine, and I could switch between the two in the Gnome Sound Preferences.  After a while, however, the sound blaster no longer plays, and I only get ourput from the integrate card.

Now, one thing that makes this particularly odd is that, in the Gnome sound preferences, if I click the button to test audio output, the tone plays out of both sound cards, but nothing else will.

Anyone have any ideas?  I've already checked that the volume controls are up; they all are unmuted and turned up...

---

### Post by norberto on 2007-06-04
Please, try this,

# Make a file named asound.conf on /etc folder
sudo gedit /etc/asound.conf

# Paste the following text
pcm.!default {
	type			hw
	card			default
}

ctl.!default {
	type			hw
	card			default
}

# save and close

# restart alsa
sudo /etc/init.d/alsa-utils restart

---

