---
title: "Get C++ Headers"
date: 2007-12-29
forum: General Help
---

### Post by dr.silly on 2007-12-29
I'm compiling OpenLieroX, and I get this error:

```
sam@sam-desktop:~/OpenLieroX$ sudo ./compile.sh 
--- OpenLieroX compile.sh ---
ERROR: SDL headers not found
ERROR: SDL_image.h not found
ERROR: SDL_mixer.h not found
ERROR: gd header not found
ERROR: HawkNL header not found
errors detected, exiting

```

I assume that I need these C headers. How do I get them and add them to my system?

---

### Post by PmDematagoda on 2007-12-29
Did you try searching the repositories using Synaptic for the dependencies that are mentioned and installing them? That could fix the problem.

---

### Post by cmnorton on 2007-12-29
[http://ubuntuforums.org/showthread.php?t=485845](http://ubuntuforums.org/showthread.php?t=485845)

---

### Post by dr.silly on 2007-12-29
ok i think i got the sdl files where should i put them?

---

### Post by dr.silly on 2007-12-29
according to synaptic i have
libsdl1.2debian
libsdl-image1.2
libsdl-mixer1.2

shouldn't that cover (in terms of sdl)?

---

### Post by dr.silly on 2007-12-30
just followed the instrunctions on their website (duh) and it worked fine

---

