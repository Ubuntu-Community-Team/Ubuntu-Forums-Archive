---
title: "Problems compiling Wine"
date: 2005-04-24
forum: General Help
---

### Post by Vaego on 2005-04-24
I'm having a issue compiling wine, i've installed the flex and bison packages, and everything compiles properly until I reach a certain point, during the make depend && make process. Heres what I get

make[2]: *** No rule to make target `../../dlls/ddraw/tests/ddraw_test.exe.so', needed by `ddraw_test.exe.so'.  Stop.
make[2]: Leaving directory `/home/kyle/docs/src/wine/programs/winetest'
make[1]: *** [winetest] Error 2
make[1]: Leaving directory `/home/kyle/docs/src/wine/programs'
make: *** [programs] Error 2

thats about it right there, everything looks smooth till that point and then it stops the compilation. I have tried this with the official source release and with the cvs, maybe i'm missing a package? Who knows

I'm using Hoary 32-bit all up to date

---

### Post by Xerampelinae on 2005-04-24
Could you post a little more of the error/make output ?

---

### Post by Vaego on 2005-04-24
Well I managed to get it to compile correctly, I was missing some sort of package, problem is what I did was got a outdated version of wine, I think it was from last october or november and it installed winelib, and wine, I tried it out and removed them, however it had to have installed another package which I am not sure what it was called :(. But for future reference, there is a package wine does require that is not listed anywhere that i'm aware of

---

