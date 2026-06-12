---
title: "Compiling MMX Support"
date: 2007-10-12
forum: General Help
---

### Post by Ryan H on 2007-10-12
I'm trying to compile the latest SVN revision of Inkscape. I'm running Gusty Gibbon 64-bit. I ran **configure** with MMX support enabled, and it said the compiler supported it; but when I ran **make** I got this error:
```
gcc  -Wall -Wformat-security -W -D_FORTIFY_SOURCE=2 -Wno-pointer-sign -g -O2 -c -o libnr/have_mmx.o `test -f 'libnr/have_mmx.S' || echo './'`libnr/have_mmx.S
have_mmx.S: Assembler messages:
have_mmx.S:15: Error: suffix or operands invalid for `push'
have_mmx.S:19: Error: suffix or operands invalid for `pushf'
have_mmx.S:20: Error: suffix or operands invalid for `pop'
have_mmx.S:23: Error: suffix or operands invalid for `push'
have_mmx.S:24: Error: suffix or operands invalid for `popf'
have_mmx.S:25: Error: suffix or operands invalid for `pushf'
have_mmx.S:26: Error: suffix or operands invalid for `pop'
have_mmx.S:46: Error: suffix or operands invalid for `pop'
make[2]: *** [libnr/have_mmx.o] Error 1
make[2]: Leaving directory `/usr/local/src/inkscape-20071009/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/inkscape-20071009'
make: *** [all] Error 2

```This makes me think for some reason my computer doesn't have MMX support? Although I'm pretty sure I've used it with FFMPEG. My processor is an AMD Athlon 64 3200+.

I know that the benefits of MMX would probably help rendering the vectors, but if it's not even really beneficial, please say!

Thank you!

-Ryan H

---

### Post by hardyn on 2007-10-12
push and pop are assembly stack calls... you might be missing a library or may have to flip a switch in on the compiler. (i have not done alot of advanced compiling)

will it complile without mmx support?

yes mmx would most likely help, but in the initial release of mmx, it would only handle integers.  it would most likely improve image manipulation algorithms... moving pixels around at high speeds.

---

### Post by Ryan H on 2007-10-14
I can compile without MMX extensions enabled, but as far as I'm away the Inkscape package in the repositories actually DOES have this enabled. . . Hmm, any ideas on how to check this?

-Ryan H

---

