---
title: "No OS Switching options..."
date: 2007-08-17
forum: General Help
---

### Post by polski_orzel on 2007-08-17
Hey guys. I just got Linux about a week ago, and yesterday installed Vista on the other part of my harddrive, and now they seem to be conflicting with eachother...

After I installed Vista, I was not giving an option to load Ubuntu when booting up. Then I did the "grub" thing, and now I can ONLY run Ubuntu....

Basically, like most of you, I play all my games in Windows, and do my regular stuff on Ubuntu. I really wanna play a game now >.<. Any tips on how I can switch between the two of them?

---

### Post by happysmileman on 2007-08-17
> **polski_orzel said:**
> Hey guys. I just got Linux about a week ago, and yesterday installed Vista on the other part of my harddrive, and now they seem to be conflicting with eachother...

After I installed Vista, I was not giving an option to load Ubuntu when booting up. Then I did the "grub" thing, and now I can ONLY run Ubuntu....

Basically, like most of you, I play all my games in Windows, and do my regular stuff on Ubuntu. I really wanna play a game now >.<. Any tips on how I can switch between the two of them?


Try editing your GRUB file yourself.

Add in the bit for Windows.
For example mine is

```
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by polski_orzel on 2007-08-17
Yep, my friend showed my that just now, thanks for the response though! Haven't tested it out, but I hope it will work.

---

