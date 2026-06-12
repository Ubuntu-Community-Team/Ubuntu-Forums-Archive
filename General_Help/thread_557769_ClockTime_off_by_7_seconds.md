---
title: "Clock/Time off by 7 seconds"
date: 2007-09-23
forum: General Help
---

### Post by Linder on 2007-09-23
I have a problem: Ever since I installed Ubuntu, my clock is wrong. Not by time, per se, but that my clock goes 53 seconds per minute instead of 60. This makes it rather rapidly go totally off. And no matter if I run it on NPT sync or if I set it manually, it goes off by at least 7 seconds / minute. 

VERY annoying. Any ideas how to solve this?

---

### Post by Linder on 2007-09-23
Dropping off the third page now...BUMP?

Any ideas?

---

### Post by Arwen on 2007-09-23
I know time is money but 7 seconds are really a difference?:-P Are you sure you're synchronised with GMT?Type 'date' in terminal,is it the right time?

---

### Post by fjgaude on 2007-09-23
How old is your motherboard? The problem indicates that the software is getting the wrong tick from some clock.

---

### Post by Linder on 2007-09-23
If it was just off by 7 seconds, I wouldn't care at all, but since it's off by 7 seconds PER MINUTE, it gets off by high numbers really fast. In essence, every minute that passes on my computer, is only 53 seconds. Thus, for every minute, my computer gets ahead by 7 seconds.

And my mainboard is brand new. It's an Asus P5B-E Plus iP965 ([http://www.inwarehouse.se/Product.aspx?prd=1131974&ReferId=7](http://www.inwarehouse.se/Product.aspx?prd=1131974&ReferId=7)) .

---

### Post by Linder on 2007-09-23
Sorry, forgot to do the terminal thingy and now I've set my time manually again. I shall wait until morning and see if the time is off. I will also check bios settings to see it's not my bios going haywire.

---

### Post by paulr on 2007-09-23
Are you running ntp ? (Select "Keep Synchronised with Internet Servers" on Time and Date settings will install it). My clock is completely barmy but this makes it manageable.

---

### Post by Linder on 2007-09-23
I tried running that, but I haven't seen it sync once, and the synchronize now button is greyed out. Also, when trying to set the time manually, the "Synchronize now" button is not greyed, however, pressing it accomplishes nothing.

I'm at a loss here :P

---

### Post by rbmorse on 2007-09-23
Do you have any kind of overclock or "burn-in" setting active in the system BIOS settings?

---

### Post by Linder on 2007-09-23
Not sure if I have. I'll check it now, as well as BIOS time settings. I've concluded that the time advances by about 5 minutes every hour.

---

### Post by Linder on 2007-09-23
Seems that I did have an overclock active in BIOS. I use a so called "AI-NOS" setting which automatically increases CPU clock speed by 15% under heavy load (average 90%). I disabled this, and also checked system time. BIOS clock was also 5 minutes ahead of "real" time. 

Seems this might be hardware related, or can Ubuntu influence the BIOS time on it's own?

---

### Post by david_2001 on 2007-09-23
The first thing I would want to check is whether the hardware clock on the motherboard is keeping good time.  As Ubuntu sets its system clock from the hardware clock when it boots and then sets the hardware clock from its system clock when it shuts down, this will mean checking the hardware clock from the BIOS setup screen without booting Ubuntu in between.

---

### Post by Linder on 2007-09-23
It's solved now. I simply shut that AI-NOS overclocking thingy off and now the time holds. This morning when I woke up, the time was spot on (and the computer was on during all the night).

Although my BIOS clock showed "wrong" yesterday, so apparently my hardware was running too fast. Still, I can't remember ever having these problems in WinXP. Anypoo, solved! Thanks guys!

---

