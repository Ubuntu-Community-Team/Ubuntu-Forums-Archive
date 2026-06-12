---
title: "Alt vs Shift and Ctrl"
date: 2021-03-28
forum: General Help
---

### Post by Skaperen on 2021-03-28
when i press and hold either the *Shift* or the *Ctrl* key and a letter a few times, the *Shift* or the *Ctrl* effect is applied to each letter press. however, when i press and hold the *Alt* key and a letter a few times, the held *Alt* key only applies to the first key press of a letter key.  the 2nd and 3rd letter keys do not get the *Alt* modification.  it's as if *Xorg* is putting that key in release state after the modification while iy is still being held.  i have to physically release the *Alt* key and press and hold it a 2nd time to get *Alt* applied to the 2nd letter i press (a different letter).  testing with *xev* shows that both *Alt* keys as well as both *Shift* and *Ctrl* keys have press and release events coming through, so *Xorg* is getting the events (and passing them through to the application).  is this just happening in *xfce4-terminal*?

i should be able to hold either *Alt* key and do multiple key presses of any key *Alt* can apply to and have the *Alt* effect apply to all presses of that key (until i release the *Alt* key).

---

### Post by GhX6GZMB on 2021-03-28
Depends on your locale. If it's en-US it's indeed odd.
For other locales it is normal.

---

### Post by Skaperen on 2021-03-28
it is en-US.  however there have been issues where some "things" that behaved as if en-UK and/or en-AU.  maybe that is still happening.

---

