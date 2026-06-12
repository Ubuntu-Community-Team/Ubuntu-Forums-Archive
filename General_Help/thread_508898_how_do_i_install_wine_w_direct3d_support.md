---
title: "how do i install wine w/ direct3d support"
date: 2007-07-24
forum: General Help
---

### Post by benx009 on 2007-07-24
i don't care if the direct3d support is buggy, i just want to have it installed anyway.  i've read posts of people doing it w/ success before

---

### Post by zanglang on 2007-07-25
Wait, doesn't wine *already* support direct3d? World of Warcraft runs fine (well, almost) when run using direct3d from wine.

---

### Post by DoktorSeven on 2007-07-25
Wine already supports DirectX/Direct3d on its own.  It is a limited implementation that won't work on everything, but runs a fair amount of games.  Since Wine has to implement its own version of DirectX to work on Linux, getting it working properly involves the Wine devs doing more work on it; it's not possible to just install a version of DirectX into Wine and get it working.

---

### Post by benx009 on 2007-07-25
don't mean to complain, but i have never got a direct3d app (simple and complex alike) to work w/ wine yet.  are you sure there's nothing that i can do to optimize the limited direct3d support available in wine?  nothing at all:confused:

---

### Post by loneshadowcccp on 2007-12-08
i know this is a late reply, but on wine appDB people say something about setting enable gsl r something like that. for that u have to go in the regestry/hkey_current_user/software/wine/direct3d.; when i go into the regestry there is no direct 3d. how do i install it?

---

### Post by Rhubarb on 2007-12-08
> **loneshadowcccp said:**
> i know this is a late reply, but on wine appDB people say something about setting enable gsl r something like that. for that u have to go in the regestry/hkey_current_user/software/wine/direct3d.; when i go into the regestry there is no direct 3d. how do i install it?

The latest version of wine already has GLSL enabled by default.
Get it here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

