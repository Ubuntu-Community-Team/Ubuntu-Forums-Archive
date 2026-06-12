---
title: "A problem with ALSA?"
date: 2008-04-04
forum: General Help
---

### Post by ibuclaw on 2008-04-04
Hi all.

Until recently, I've had no problems whatsoever with ALSA, my soundcard, or my speakers for that matter.

Then I'd notice that every hour or so, my speakers would make a click or popping noise.
Presumably from Linux (ALSA or something or another) refreshing it's (driver) cache??? (guess work... I honestly do not know)

Anyway, overtime the popping noise has been exponentially becoming more amplified. ie: can be heard while music is playing, etc. 

Now I've since I've first started noticing it.
I've done a clean install onto Hardy and created new users accounts with clean config files.

But the popping sound is still there and growing in loudness.

If anyone has any clue what's going on. Messages back will be most graciously thanked.

Regards
Iain

---

### Post by ed-koala on 2008-04-04
Perhaps the speakers are going bad?  First thing I'd try is hooking up different speakers and see what happens.  Borrow a pair from someone which you know works fine, then you'll know if it's software or hardware causing the problem.

Oh, the cord might be fraying or dying on you instead.  Check both.

---

### Post by ibuclaw on 2008-04-06
Hi, sorry for the late reply, I've been busy.

OK, I'm 99% sure that it isn't the speakers.

As for wires, I have a plastic coated wire wrapped around the tied up cable to keep it off the ground and getting tangled with everything.

And I've tried them on my mates PC, and they don't make a single irregular noise (tested them for a straight day).

To be more precise about the sound, it's kinda like when you type this
```
 echo > /dev/dsp 
``` into the terminal.

I've also noticed that only does it when my soundcard has been inactive for a good hour.

Thanks
Regards
Iain

---

### Post by ghost_ryder35 on 2008-04-06
swap the speakers out for headphones and see if it still happens, if it does it says the speakers are good, if it doesnt its either the speakers, the speaker wire, or the power supply for the speakers

---

