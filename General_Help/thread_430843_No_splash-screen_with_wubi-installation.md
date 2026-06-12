---
title: "No splash-screen with wubi-installation?"
date: 2007-05-02
forum: General Help
---

### Post by lprofil on 2007-05-02
Hi,

i just installed Ubuntu via wubi because i was curious if i could really recommend it for friends of mine who frighten to partition teir harddrive.
After experiencing some [know issues with a delayed startup]("http://ubuntuforums.org/showthread.php?t=421060") on the first boot i was quiet impressed how the install-rutine works.
You've done a great job creating a painless trial for not low-experienced linux-newbies. Good work!

But, is the **boot-splash-screen** *deactivated* for some reason by default?

/lprofil

---

### Post by ago on 2007-05-02
> **lprofil said:**
> 
But, is the **boot-splash-screen** *deactivated* for some reason by default?


In final version usplash should be activated. Anyway it is a pretty easy fix. Change menu.lst and add "splash" to the kernel line.

---

