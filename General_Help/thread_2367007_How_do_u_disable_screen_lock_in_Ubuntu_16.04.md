---
title: "How do u disable screen lock in Ubuntu 16.04"
date: 2017-07-24
forum: General Help
---

### Post by kenthink on 2017-07-24
I just installed Ubuntu 16.04 I use it a lot for playing music while I work on another computer. It works fine but after a few minutes the screen automatically locks so I have to enter my password to unlock it. This is a pain since I have to unlock it quite often. Is there some way of disabling the lock?

---

### Post by unityforever on 2017-07-24
system setting -screen and lock

modify parameters below

turn off the screen after "" minutes  -- if computer stay idle after "" minutes, screen will goes black, you can change the value to never.
lock the screen after "" seconds --** if screen is black after** "" seconds, computer will be locked,the **defau****lt **[B]value is  immediately, thus you will feel the computer locked right after the screen went black

[/B]frankly i hate this default setting too, system always suddenly locked while im watching videos. really want to know what kind of nut set that dumb default value.

---

### Post by kenthink on 2017-07-24
> **uiduser said:**
> system setting -screen and lock

modify parameters below

turn off the screen after "" minutes  -- if computer stay idle after "" minutes, screen will goes black, you can change the value to never.
lock the screen after "" seconds --** if screen is black after** "" seconds, computer will be locked,the **defau****lt **[B]value is  immediately, thus you will feel the computer locked right after the screen went black

[/B]frankly i hate this default setting too, system always suddenly locked while im watching videos. really want to know what kind of nut set that dumb default value.

Maybe you have a different version. I could not find system setting screen and lock. However I did find under preferences light-locker settings locking. There is a line about automatically locking the session. I changed that to Never, from when the screensaver is activated and that worked. Thanks for the help. It led me in the right direction.

---

