---
title: "beryl crash"
date: 2006-11-16
forum: General Help
---

### Post by M!K3_$ on 2006-11-16
beryl crashed on me (guess u could of figured that one out:>)

so i restart
and i get my login screen
i login 
then i just get a screen full of color
the desktop doesn't load or anything
from the terminal, i type in x-window-system and it says it cant start the display

mabye there is a way (through terminal) to take beryl-manager off of startup programs, is this possible
then i could try to fix beryl that way

thankx
mike

---

### Post by PriceChild on 2006-11-16
At the login screen, choose sessions > "Failsafe Gnome".

This will log in without using the startup entries. You can then remove it and log in again.

---

### Post by M!K3_$ on 2006-11-16
allright ill try that

thankx pricechild
mike

---

### Post by M!K3_$ on 2006-11-16
nope, samething happend.
xcept it totally froze up, at least i could move the cursor bfor

help plz :S

---

### Post by M!K3_$ on 2006-11-18
like a ***_BUMP_*** in the night :S :>

---

### Post by philippe_carlo on 2006-11-18
It's probably not an X problem, otherwise the GDM would suffer from the same symptoms. If you are still able to switch to a virtual console, you may be able to figure out which program is making X hang, using ps and top.

---

### Post by M!K3_$ on 2006-11-18
ps and top??

---

### Post by Thaigor on 2006-11-28
Got the same problems after A manual restart ( the computer went too crazy so I had to do it ) ... then when I turn it back on it's just show only a blank screen ... I tried remove Beryl + Emerald but still nothing happen ... 

the only way that I can think of is to change to Metacity from the Terminal ... which probably nobody in this forum know ( I check almost everywhere on this forum and a lot of same question like this comes up ... without a proper answer )

I'll try to look around for another week for a one good solution on the net and if there is no answer then I better re-install Ubuntu again ( Which I really hate because all the setting and tweak I had done is pretty cool )

---

### Post by Thaigor on 2006-11-28
I used "top" and I found out that the stuff that is working is "Compiz" not Beryl/Emerald or Metacity

Well ... What should I do ?

---

