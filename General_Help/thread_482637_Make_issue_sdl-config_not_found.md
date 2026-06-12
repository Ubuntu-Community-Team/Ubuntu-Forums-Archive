---
title: "Make issue: sdl-config not found?"
date: 2007-06-23
forum: General Help
---

### Post by Dylnuge on 2007-06-23
Hello. I recently downloaded glHack (a lLinux GUI for NetHack) and ran the make commands. However, I got the same error repeated over and over about sdl-config not being a valid command. I decided to try a different NetHack gui-same problem. Here is the output from the last one:
```
make[2]: sdl-config: Command not found
../sys/unix/unixmain.c:18:18: error: SDL.h: No such file or directory
make[2]: *** [unixmain.o] Error 1
make[1]: *** [vultureseye] Error 2
make: *** [nethack-home] Error 2

```

Note, however, that the sdl line was repeated at least forty times before that. In the first try, on glHack, it showed the c source file names after each error-on the second try, it did not.

These are two separate programs, in no way affiliated with each other, and despite them being frontends for the same game, they should have had different makefiles. I think this is a problem with make itself.

Any light on this situation would be appreciated.

Thanks,
Dylan

PS: I just checked the Gnumakefile file, and there is no mention of sdl in it.

---

### Post by Dylnuge on 2007-06-26
...Anyone? This is the third thread that has gone unanswered by anyone that I have posted in the last few weeks.

---

### Post by shirilover on 2007-06-26
try this
```

sudo aptitude install libsdl1.2-dev

```

---

### Post by Dylnuge on 2007-06-28
It worked! Thanks.

---

