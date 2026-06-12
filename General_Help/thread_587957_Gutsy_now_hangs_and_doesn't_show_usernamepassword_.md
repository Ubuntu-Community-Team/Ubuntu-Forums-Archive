---
title: "Gutsy now hangs and doesn't show username/password boxes"
date: 2007-10-23
forum: General Help
---

### Post by dmjones500 on 2007-10-23
I installed Gutsy on my Dell Latitude D420, and all was well.

Then I rebooted for the nth time (having installed MySQL and messed with a few things), and now my system hangs during booting.

It displays the normal Ubuntu boot-up progress bar, which seems to complete.  Then the screen blanks and starts to load the username / password screen.  However, it hangs before showing anything.  All I can see is the animated loading cursor, which seems to twitch for some reason (i.e. the cursor repeatedly jumps 10 pixels down and left, before returning).

Any ideas what could be causing the hang?  I'm running from the live CD at the moment, with my local FS mounted, so I can check logs etc if people suggest that.

Thanks,

Duncan Jones

---

### Post by dmjones500 on 2007-10-23
The last entries in the Xorg log read:

```
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
```

In case that helps...

---

### Post by dmjones500 on 2007-10-23
I got bored with this problem, so I reinstalled.

I know it sounds drastic, but I'd only being playing with my new install for two days...  It's also much neater when you have a separate /home partition :-)

---

