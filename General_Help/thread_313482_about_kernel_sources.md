---
title: "about kernel sources"
date: 2006-12-06
forum: General Help
---

### Post by Laryllan on 2006-12-06
Hi there!

I twice tried to recompile the Ubuntu Kernel (6.10) provided by Synaptic - and twice I failed. 

The only thing I wanted to change is remove SMP support for compatibility reasons. I used the Ubuntu configuration found in /boot - the only thing I changed: unchecked SMP support.
Building works but there are *lots* of errors during compilation.

It seems not to be possible to recompile the kernel from the Ubuntu repository. This makes me think.
Why do they provide kernel sources that don't work? This leads to the conclusion that the sources have to be different than the kernel image provided. What *are* these differences? What do the Ubuntu developers try to hide?

Please don't misunderstand, maybe there is a reasonable explanation. This is just a question I'd like to be answered.

So long.

---

### Post by pay on 2006-12-06
Make sure that you have gcc installed before compilling```
sudo aptitude install build-essential
```

---

### Post by Laryllan on 2006-12-06
I did. And I have absolutely no problems compiling the kernel anew using the sources of kernel.org.

It's just that it doesn't work with the Ubuntu sources.

Just try it.

---

### Post by pay on 2006-12-06
I can't try it because I use Gentoo, but it doesn't seem right that a major distribution like Ubuntu would release kernel source patches that don't compile.

---

### Post by Laryllan on 2006-12-06
This is exactly why I started this thread...

---

### Post by christhemonkey on 2006-12-06
What are the exact errors it spews out?

---

### Post by pay on 2006-12-06
Why not post the errors so we know what the problem is.
EDIT:christhemonkey beat me to it.

---

### Post by Laryllan on 2006-12-08
Ok, I recompiled the kernel using the Ubuntu sources 2.6.17 from the repository.

If I now try to compile something, it doesn't work anymore. This is the error output:

```
make[1]: Betrete Verzeichnis '/usr/src/linux-source-2.6.17'
  CC [M]  /home/laryllan/src/rt73-cvs-2006120306/Module/rtmp_main.o
/home/laryllan/src/rt73-cvs-2006120306/Module/rtmp_main.c: In function â&#8364;&#732;CMDHandlerâ&#8364;&#8482;:
/home/laryllan/src/rt73-cvs-2006120306/Module/rtmp_main.c:306: warning: comparison of distinct pointer types lacks a cast
{standard input}: Assembler messages:
{standard input}:702: Error: suffix or operands invalid for `pop'
make[2]: *** [/home/laryllan/src/rt73-cvs-2006120306/Module/rtmp_main.o] Fehler 1
make[1]: *** [_module_/home/laryllan/src/rt73-cvs-2006120306/Module] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-source-2.6.17'
rt73.ko failed to build!
make: *** [module] Fehler 1
```

I recompiled the kernel using the how-to from Ubuntu wiki; the only things I changed via xconfig are: I disabled SMP support and preemption.

You can find an explanation why I try to do this [here]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=2565").

---

