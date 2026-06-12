---
title: "SoundMax ac97 Sound Problem"
date: 2006-10-31
forum: General Help
---

### Post by rapidwiz on 2006-10-31
Thought some people might find this useful if the new 6.10 sound does not work ..



Procedure:
- Open a command window
- Type
    alsamixer
- Use the right arrow to make the "highlighted selection" (
  red text under the "bar display" be the "Headphone Jack Sense"
  (these things are somewhat truncated under the bar displays, so
  that the "headphone" and "headphone jack sense" bars may read
  almost the same; however, the "Item" in the upper right corner
  of the command window spells it out.
- At the top of the bar may appear (or not) "MM"; typing an "m"
  toggles the "MM" on and off.  (Confusingly, "MM" equates to "off"
  and "not MM" equates to "on"; MAKE SURE THE MM APPEARS at the
  top of the "headphone jack sense" bar
- Do the same thing to "line jack sense", found by pressing
  the right arrow sufficient times; there are more bars than
  fit in a normal window so it might not appear initially;
  the additional bars scroll into the window as you move right
With the "MM" appearing at the top of both the "headphone jack
sense" and the "line jack sense" (meaning I presume that the
features are "off" or "disabled", my sound works.

---

### Post by Matthewslf on 2007-10-27
Thanks a lot for the tips. I have been trying to get my sound to work for months and now it does. As a note to other users, I had to "MM" external amplifier as well to get my sound to work.

---

