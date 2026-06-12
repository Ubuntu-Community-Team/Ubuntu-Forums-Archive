---
title: "[SOLVED] [  251.790031] cdrom: This disc doesn't have any tracks I recognize!"
date: 2008-07-05
forum: General Help
---

### Post by Majin_Buu on 2008-07-05
```
[  251.790031] cdrom: This disc doesn't have any tracks I recognize!
```

> growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/hdb=all-ds.dvd

Executing 'builtin_dd if=all-ds.dvd of=/dev/hdb obs=32k seek=0'
:-( write failed: Input/output error

That's what I get all the time when im trying to use growisofs to burn a dual layer disc (xbox360. I've checked dmegs and it gave me a LOT of errors.. I manually edited fstab to "auto" and the only error remaining now is "this disc doesnt have any tracks I recognize".

Can anyone explain to me what that means exactly and how to make it work with growisofs?

I want to use CLI as much as possible.

Right now im burning the disc using wine-imgburn and it gave me a full working copy... but again I prefer CLI (linux) :KS

---

### Post by prshah on 2008-07-05
> **Majin_Buu said:**
> ```
[  251.790031] cdrom: This disc doesn't have any tracks I recognize!
```


This is not an error message; it's a normal (informational) message that you will get every time you insert a blank disc. The same message will also be displayed with a coaster (bad burn) disc or with a highly damaged and scratched disc.

---

### Post by Majin_Buu on 2008-07-05
> **prshah said:**
> This is not an error message; it's a normal (informational) message that you will get every time you insert a blank disc. The same message will also be displayed with a coaster (bad burn) disc or with a highly damaged and scratched disc.

Ah I see, well thanks anyways :)

There's a typo with my command I linked it to the .dvd instead of the acutal iso..

Problem RESOLVED!

---

