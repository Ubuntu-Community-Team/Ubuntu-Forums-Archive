---
title: "When --32 bit ad --64bit flag will be avaible?"
date: 2007-10-26
forum: General Help
---

### Post by Opteron78 on 2007-10-26
I want to know when 32bit/64bit flag will be avaible in wubi! I noticed you are working hard and new alpha versions come out every 5 minutes :D, keep up your work! I appreciate it very much! But I am a new linux user...so I am not so expert in running 32 apps on 64bit linux...so I hope this flag will be added soon! 

Another thing....what you mean when you write "hold down alt+sysreq+...." . What is sysreq key and that sequence? I have heard that hard rebooting could destroy xp boot ...so I want to avoid that!

---

### Post by ago on 2007-10-26
--32bit is already supported

64 bit does not need any switch since it is the default for 64bit arch (unless you have a 32 bit ISO around).

The sysrq key combination is a way to obtain a clean shutdown even when the keyboard/monitor is not responsive (unless you are in a kernel deadlock). So it is the last thing to try before pulling the power if you get stuck for any reason (something that Wubi does not take too well). You basically keep pressed Alt+SysRq and type  the word "reisub". Then the machine should shutdown.

---

### Post by Opteron78 on 2007-10-26
> **ago said:**
> --32bit is already supported

64 bit does not need any switch since it is the default for 64bit arch (unless you have a 32 bit ISO around).

The sysrq key combination is a way to obtain a clean shutdown even when the keyboard/monitor is not responsive (unless you are in a kernel deadlock). So it is the last thing to try before pulling the power if you get stuck for any reason (something that Wubi does not take too well). You basically keep pressed Alt+SysRq and type  the word "reisub". Then the machine should shutdown.

wow thanks! It's already implemented!!  SysRq should be Print key on my keyboard? Sometimes it happened that linux hanged...so next time I will try this magic formula :)

---

