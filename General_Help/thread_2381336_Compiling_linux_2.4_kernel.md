---
title: "Compiling linux 2.4 kernel"
date: 2017-12-29
forum: General Help
---

### Post by nicksanchez on 2017-12-29
Hello everyone!
Now I am trying to compile Linux 2.4.32 kernel on my pc. According to readme inside the folder with the sources I should compile the kernel with gcc 2.95 (or something close to it, the max version is 4.1 I think). So the point is that I cannot even compile the gcc on my pc.

Everything is going on VBox or on a laptop (if that matters), everytime it's a 64 bit system installed (didn't tried 32bit cuz thing it doesn't matter).
The way I am compiling gcc is:
linux32 ../configure --target=i386-pc-linux-gnu (here I need linux32 cuz of without it the configurator cannot get the x86 architecture)
linux32 make OR linux32 make bootstrap (here actually I got errors)

The errors are like "[LEFT][COLOR=#000000][FONT=-apple-system]Makefile:1741: recipe for target collect.o failed" + "make[1]: *** [collect2.o] error 1[/FONT][/COLOR][/LEFT]" + same for 'all-gcc' OR same for 'cc1'+ 'bootstrap' if compiling through bootstrap version.

So I hope someone has an idea how to figure that out... Maybe I am totally wrong and there is better to compile kernel another way...

Anyways, ty for any advice!

---

### Post by QIII on 2017-12-29
Hello!

Are you doing this as a pure learning experience, or do you plan to use that very old kernel?

---

### Post by nicksanchez on 2017-12-29
Hello! Just for learning.

I should notice that I googled lot's of tutors but with no success. I guess I am missing something or my way to compile the kernel is bad :|

---

### Post by nicksanchez on 2017-12-30
For now tried out 32 bit Ubuntu 16.04 but still with no result... Still cannot compile gcc-2.95

---

