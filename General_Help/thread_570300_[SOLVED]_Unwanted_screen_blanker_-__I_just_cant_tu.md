---
title: "[SOLVED] Unwanted screen blanker -  I just cant turn it off!"
date: 2007-10-08
forum: General Help
---

### Post by chrismyers on 2007-10-08
I have recently built a Feisty machine that we are using as an informative wallboard. Firefox (with the tab  slideshow plugin)constantly updates information for our team & informs us of possible problems.
[COLOR=Blue]
**However - After about 2 hours the screen blanks.**[/COLOR]

I have put 'computer sleep' & 'display sleep' to never. I have also set the BIOS to disable any power management.

I know it not the screen saver activating, because I have set it to 'plasma'.

What else can I do to prevent the screen blanking?

I suspect its the PC itself that is doing the VDU sleep (allthough I cant be certain). If this is the case, would it be possible to set something to force it to 'keep alive'?

Many thanks.


---

### Post by chrismyers on 2008-01-11
To follow up. This did the trick:
 
xset -dpms

---

