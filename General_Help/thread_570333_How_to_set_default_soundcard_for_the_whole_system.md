---
title: "How to set default soundcard for the whole system?"
date: 2007-10-08
forum: General Help
---

### Post by Nightblade on 2007-10-08
Hello!
I recently plugged in my Omega Lexicon (USB-soundcard) and it works wonders, but now I wonder if I can somehow set it as default for the overall system? Is it possible? Like in some alsa control app or something?

Because right now almost all apps has my usual SBLive soundcard as default and I don't like that. I want my Onega ;).

Best regards,
Nightblade

---

### Post by sageb1 on 2007-10-08
Dude, you are talking about a professional external mixer which replaces alsa mixer and has input and output for everything including midi keyboards etc, professional mikes and probably guitar input.

Seriously, the Omega :replaces: your SB Live! and probably the ALSA sound system and associated daemons (ESD and ARTSD).

Yes, probably sound handled by those two sound daemons (for beeps and audio media).

You may have to kluge together a bash script to enable the Omega, but you will have to remove your SB Live! (unless it is needed to play back input handled by the USB soundcard and mixer).

Yet the Omega has sound output, so I am still wondering why you have the Live card still in your computer. I guess it is a laptop.

You have to change the scripts controlling loading of SB Live! drivers to not load those drivers first. The Omega' drivers need to be loaded first.

I do not know how to disable the onboard sound card since I do not know if the bios has a toggle to turn on/off this card.  

Hopefully I am not talking to a newbie to Linux here. 

FWIW you could remove the SB Live! driver and start up the script to enable the Omega.

I leave it to you to turn this vague advice into a script.

:guitar:

---

### Post by Nightblade on 2007-10-08
Thanks man! Didn't think of that.

I'll just remove the SBLive and disable the onboard soundcard.

---

### Post by Bigdeath on 2007-11-26
Dude I got a lexicon omega and I cant seem to get it to work. What did you have to do?

---

