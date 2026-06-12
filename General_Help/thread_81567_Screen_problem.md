---
title: "Screen problem"
date: 2005-10-24
forum: General Help
---

### Post by PaulHanson on 2005-10-24
I just switched to 5.10 from windoze xp on my dell inspiron 1100. there is alot of black space around the display area, which is obviously a huge pain. the bios version is A32 and a friend tried to increase the allotment for video memory via the command line but no luck. any ideas on how to get back to full-screen?

note: i had this same problem when playing starcraft on xp. i don't know if its due to the same cause but it might be relevant.

Thanks!

---

### Post by Kyral on 2005-10-24
Inspirion 1100?! They still make those?! Wow... I had one like a couple years ago.

Anyway the problem is that the BIOS doesn't pass the right amount of video memory to X. You are gonna have to get the latest BIOS Update from Dell. Then it should work.

In XP it worked because the version of XP that comes on those Restore Discs is hacked to get around the BIOS bug

---

### Post by PaulHanson on 2005-10-24
Yeah, it is a chunky old thing, that 1100....but we make do with what we have eh?

I think I have the latest version of the BIOS...A32, right? I tried an upgrade patch but it just told me that I already have the latest one....so upgrading the BIOS doesnt seem to be the answer.

---

### Post by soulestream on 2005-10-24
you can just add VideoRam 65536 (or however much video ram you have) under you r video device in xorg


soule

---

