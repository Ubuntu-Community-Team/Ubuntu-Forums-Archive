---
title: "make problem, installing nes emulator"
date: 2007-05-25
forum: General Help
---

### Post by ssamoon on 2007-05-25
i was trying to find an alternative to FCE for a NES emulator (didn't seem to live up to windows equivalents), and i tried fakenes (decent) and wast trying to install tuxnes but am running into the following problem compiling the source.

./configure runs ok but make gives me

> moon@moon:~/Desktop/tuxnes-0.75$ make
gcc -DHAVE_CONFIG_H -I. -I. -I.     -O -pipe -Wall -D__USE_BSD -c emu.c
emu.c: In function ‘loadpal’:
emu.c:893: error: expected ‘)’ before string constant
emu.c:915: error: expected ‘)’ before string constant
emu.c:927: error: expected ‘)’ before string constant
emu.c: In function ‘main’:
emu.c:1605: error: expected ‘)’ before string constant
make: *** [emu.o] Error 1
moon@moon:~/Desktop/tuxnes-0.75$ 

any ideas? thanks, sorry kinda noob here.

---

