---
title: "Xorg using lots of memory"
date: 2014-04-26
forum: General Help
---

### Post by dylan16 on 2014-04-26
I just left my computer on for a while, and  when I came back it was really slow, and System Monitor showed that xorg was using 3.6 gigabytes of memory.  It had Google chrome, Skype, and an empty terminal open in 4 different desktops.  I don't remember it doing this before, and I have 8 GB swap and ram.  I don't want it doing that because it starts to use swap which I can only clear out by rebooting the computer.

---

### Post by iris-n on 2014-05-25
I believe I have the same problem. Are you using ubuntu 14.04 and a AMD graphics card?

What happened is that after I upgraded from 13.10 to 14.04 Xorg's memory usage just grows constantly, and after a day or two of being left on the computer simply becomes unusable, until I rebbot.

What did work to stop it was to remove AMD's proprietary driver, fglrx, and switch to the open source one.

Can you test if this also works for you?

---

