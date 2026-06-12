---
title: "GRUB menu doesn't *display*, still functional?"
date: 2007-09-08
forum: General Help
---

### Post by Zorlin on 2007-09-08
Strangely enough; I recently reinstalled Ubuntu in the hopes of getting Compiz Fusion working. I bothered to set up a /home/ partition this time too. But for some weird reason when I turned it on, the GRUB menu wouldn't display at all. I thought this was weird but eventually after the GRUB menu did its timeout (3 seconds) Ubuntu automatically booted. I thought this might be a menu.lst problem, or maybe that it simply didn't have more than one option yet so the "menu" wasn't necessary... I tried to add windows to the menu and found when I rebooted *shock horror* that the menu still wouldn't display. Worse, occasionally I get weird patterns across the screen; for example, white pixels dotting down the left side of the screen, the middle of the screen filling with blue with a light blue line on the left side; which could be explained by this line [color cyan/blue white/blue]. I don't have a huge problem with this as GRUB is still functional for me [I can simply select what I want to boot without a display; Windows is the top and Ubuntu is directly below it] but I'd still like to know the following things.

1) Is this a known bug; or is it possibly just a corrupted GRUB...
2) Has anyone else encountered this problem?
Thirdly, and most importantly: Would reinstalling GRUB help? If so, what would you guys recommend. Remember, I can still boot either Windows or Ubuntu. Thanks :)
:KS

===EDIT===
Could this topic get closed? Sorry for not checking back.
Turns out, it was my monitor at fault... I booted to BIOS and made the monitor do its whole "auto adjust" thing and it fixed the problem :)

---

### Post by confused57 on 2007-09-09
I had a similar problem that was caused by my LCD's auto-tune feature.  My mobo's bios post  would open with the Intel "splash" screen, the auto-tune would kick in on my LCD, but before it could finish, the grub menu booted, resulting in a garbled grub menu.   What I had to do was go into bios and select for the Intel splash screen not to be displayed at boot.  May not be your problem, though.

---

### Post by Zorlin on 2007-09-11
I don't believe this would be the problem; I don't have a splash screen. I'll look in BIOS anyways, see if I can find out anything. Usually its just a black screen though (doesn't show at all):guitar:

---

### Post by Damanther on 2007-09-11
This sounds very similiar to what happened when I pointed grub at a bogus splash screen. I know you said you don't have a splash, but you might just check and make sure your menu.lst isn't pointing a splash image somewhere that maybe doesn't exist, or exists but is corrupt.

---

