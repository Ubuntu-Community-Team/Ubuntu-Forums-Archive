---
title: "Touchscreens and Long Press Right Clicking... impossible?"
date: 2014-12-17
forum: General Help
---

### Post by ari5 on 2014-12-17
Good afternoon. 

I have an MSI Slidebook S20 and I am looking to get rid of windows 8 on it and go back to linux. I've been using various distros for nearly a decade now, and I was pleased to see Ubuntu supports pretty much all of the hardware right out of the box (I am using 14.10 right now, from a live USB)

Here's the issue, and this is pretty much a dealbreaker: How in the world can I get a simulated right click by long pressing? I've tried touchegg and ginn, and I haven't been able to produce desirable results. Touchegg just flat out doesn't work and ginn segfaults if I add a 1finger tap trigger.

If I have to get rid of all the other gestures, I will, I just want a long press right click.

---

### Post by mattgyver83 on 2015-01-11
Your not alone, I am also looking into a way to do this however I am using a different model laptop Acer Aspire R14.  Out of the gate all things worked really well with some minor tweaking and I am still exploring possibilities and likely will not go the touchegg/ginn method as it requires some mucking with Unity to work and I am really not interested in jumping off the mainline version.  I am digging around for some alternative and will post if I come up with something.  I feel there is a sneaky way to do this even if its just hacked into a script and if I figure it out ill be sure to update you!

---

### Post by mattgyver83 on 2015-01-11
Nailed it!  This is embarrasingly simple and it worked well for me however the sensitivity can be a pita off and on.  Go into Universal Access > Pointing & Clicking and enable "Simulated Secondary Click" and just set the Acceptance delay to whatever is tolerable for you.

---

