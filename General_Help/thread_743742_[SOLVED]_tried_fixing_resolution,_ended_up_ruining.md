---
title: "[SOLVED] tried fixing resolution, ended up ruining everything ; ;"
date: 2008-04-02
forum: General Help
---

### Post by rayefrenzy on 2008-04-02
Okay, so I was playing around and trying to get the resolution working on my computer. It was stuck at 640x4-whatever and I was trying to make it at least bearable. In desperation, I changed the monitor. They didn't have the "HP mx70" but "HP mx705" was on the list. I figured, what the heck, maybe it'll work.

So, it re-boots, and it's all scrambled and jumbled, and I can't seem to fix it since there's no way to see what's going on with the display. Is there anyway I can get into the root and fix this? If so, tell me what the heck to type, since terminal is mostly moonspeak to me.

PLEASE HELP!

---

### Post by LaRoza on 2008-04-02
Run this:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

Boot to the recover console to do it.

---

### Post by rayefrenzy on 2008-04-03
Works! Thank you!

---

