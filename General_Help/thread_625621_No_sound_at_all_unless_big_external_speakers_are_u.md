---
title: "No sound at all unless big external speakers are used"
date: 2007-11-28
forum: General Help
---

### Post by SFinn on 2007-11-28
I recently switched from XP to Ubuntu. The only problem I have with Ubuntu is that I can't get any sound to play. I've tried the volume control on the panel on the desktop. I've tried altering the sound preferences on System>Preferences. I've tried typing 'alsamixer' in the terminal, and using that. None of these have worked.

The only success I've had is by plugging big surround sound speakers into the headphone jack and turning everything up to the max volume. Then I can hear noise if I put my ear right next to a speaker. Somehow this doesn't seem to be the way the OS was designed to be used  :P

I've found that I can only unmute the volume when the headphones are unmuted. So, no sound through my laptop speakers, and only tiny amounts through the headphone jack, using big speakers. 

Can anyone lend a hand with this?

---

### Post by renzokuken on 2007-11-28
any idea what sound chipset you have?

the command  
```
lspci
```
should show some info

---

### Post by SFinn on 2007-11-28
```
 00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
```

That's the one, right? What should I do with that info?

---

### Post by renzokuken on 2007-11-28
try the solution posted on this guys site....he's a ubuntuforums user and he got his sb450 working this way

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

follow only the **Toshiba Laptop ATI SB450 Audio no Sound** section, reboot and let us know how it went

---

### Post by SFinn on 2007-11-28
I followed the instructions, but still no sound.

The sound test files now refuse to play:
Message:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```

Also, only PCM on Alsamixer is now available, whether I use 'alsamixer' in the terminal, go to system>preferences>sound, or use the volume icon on the panel... There is no option for turning headphones on or off.

Should I remove the line of text that the instructions told me to add?

---

### Post by SFinn on 2008-01-17
bump

---

