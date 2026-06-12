---
title: "Inverted Mouse???"
date: 2008-01-14
forum: General Help
---

### Post by Route490 on 2008-01-14
Hello All,

I feel this may be a total noob question, but I cannot find a solution and even browsing the web is proving to be a pain.

The problem for reasons unbeknown to me is my mouse is now inverted but only in the vertical directions.  You move it up, your mouse goes down on the screen and vice versa.  Left and right still work as normal.  All i was doing at the time was watching a movie from my bed, wasn't even touching the computer!

Any ideas would be much appreciated

Cheers

---

### Post by erpo on 2008-01-14
Maybe someone is playing a practical joke on you. Check /etc/X11/xorg.conf to make sure this isn't happening to you: [http://ubuntuforums.org/showthread.php?t=483723](http://ubuntuforums.org/showthread.php?t=483723)

---

### Post by Route490 on 2008-01-14
Thanks Erpo, I had looked in xorg.conf earlier and didn't see anything untoward but I just added the line

```
Option      "InvY" "on"
``` 

Although this is probably a workaround at best, it has worked.  I am the only one with access to the computer "locally" anyway and can't think of anything that would cause such an effect.

But thanks for the speedy reply, tho I must admit i had just got used to the inverted mouse, struggling now :lolflag:

---

