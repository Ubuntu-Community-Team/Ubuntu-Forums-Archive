---
title: "Left expo on during update today"
date: 2008-06-23
forum: General Help
---

### Post by ad_267 on 2008-06-23
I had an interesting experience. I had left the expo plugin active during the updates today, I think there were updates to compiz and the kernel. I came back after a while and my computer was completely locked up. Mouse wouldn't move, ctrl-alt-backspace did nothing. ctrl-alt-F1 etc did nothing. Had to do a hard reboot and came back into low graphics mode. Had to run "sudo dpkg --configure -a" and then update and upgrade. Thankfully after restarting everything was back to normal.

I'm just wondering if I should not leave something like expo running again during an update or if this was a coincidence and it should be fine to do that.

---

### Post by paulderol on 2008-06-23
it might have been that the update to compiz changed the files used to render expo, so that the shift in packages broke the compositing that was being done, i assume you mean that the expo screen was actually up, rather than just "on." it's probably not a big thing, but you might avoid having anything but updates happen at update time. shouldn't have done anything really though. that's weird. as i think about it it makes less and less sense. see what the compiz packages did that just updated, because compiz and AWN didn't flub on my machine, but i wasn't "expo-ing" at the time...

short answer--probably not a big deal.

---

### Post by ad_267 on 2008-06-23
Yeah I mean expo was actually up. I thought this was weird too. Often an update to firefox kills stuff and firefox needs to be restarted but I would have thought that anything used by expo would still just be in memory or expo would be closed if it was a problem. I'm wondering whether it was just a coincidence and something else randomly caused this problem. I don't know how to see what packages were recently updated.

---

