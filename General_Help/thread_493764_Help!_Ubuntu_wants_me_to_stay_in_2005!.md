---
title: "Help! Ubuntu wants me to stay in 2005!"
date: 2007-07-06
forum: General Help
---

### Post by ior3k on 2007-07-06
Hey all,

the weirdest thing started happening since a few days ago: I resumed my laptop only to discover that Ubuntu had warped me to 2019. 

"That's odd", I thought. Then I looked around, only to find that everything was still the same. This led me to conclude that 1 of 2 things was happening:

[LIST=1]
[*]2019 is boring, or
[*]My clock has gone bananas.
[/LIST]
So I adjusted the clock, did a sudo -k and a sudo -K, rebooted, resetted /etc/adjtime (0.0 0 0.0), not necessarily in this order, and things worked fine for a few hours. Then Ubuntu decided to take me back to 2005. And that's where I'm stuck to this day, even after multiple hwclock --systohc, shaman consultations, and threats of going back to the preinstalled Windows Vista.

The weird thing is that the problem only happens with my hardware clock. System date is fine. Here are my questions:

[LIST=1]
[*]Do any of you happen to have a Delorean with a working flux capacitor around?
[*]If not, care to explain to me how the heck do I make Ubuntu send me back to 2007, and STAY there?
[/LIST]
Cheers,

David

---

### Post by jespdj on 2007-07-06
Maybe the battery on your motherboard that powers the CMOS is getting old. Replace the battery. (Note, ofcourse I don't mean the battery of your laptop, but the small mercury battery on the motherboard).

---

### Post by p_quarles on 2007-07-06
> **jespdj said:**
> Maybe the battery on your motherboard that powers the CMOS is getting old. Replace the battery. (Note, ofcourse I don't mean the battery of your laptop, but the small mercury battery on the motherboard).
I'm guessing that's the problem, too. That said, CMOS batteries usually last for about 4 or 5 years, so if this computer's only like a year old, it's probably something else.

---

### Post by ior3k on 2007-07-09
Nope, I can guarantee it's Ubuntu. The clock is fine until I hibernate or shutdown the computer. If I do that and immediately boot again, the clock turns up messed up. Also, Vista holds the time perfectly. It may crash twice every single day, but it holds the time perfectly.

---

