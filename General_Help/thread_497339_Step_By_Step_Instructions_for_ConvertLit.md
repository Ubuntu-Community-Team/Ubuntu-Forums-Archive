---
title: "Step By Step Instructions for ConvertLit"
date: 2007-07-10
forum: General Help
---

### Post by NeghVar on 2007-07-10
Hello,

I have been trying without success to figure this installation out. The creators website is incredibly outdated and there is no support on the net. I tried some of the other metheds on the forum here but they all return no bash command found, so if come one could give me a step by step guide I'd appreciate it.

Thanks,
Len

---

### Post by clach04 on 2007-10-16
Rough notes:

Need package "build-essential"
Need source code for ConvertLIT from [http://www.convertlit.com/](http://www.convertlit.com/)
Need LibTomMath source code from [http://math.libtomcrypt.com/download.html](http://math.libtomcrypt.com/download.html)

Extract  ConvertLIT
Extract LibTomMath in same directory as ConvertLIT
cd to  LibTomMath directory ; issue make
cd to converlit/lib directory; issue make
cd to convertlit source dir; e.g. cd ../clit18; issue make - this should use the LibTomMath built above.

---

### Post by christopher.newell on 2008-05-10
I need help figuring what I may have done wrong in these simple, clear directions.
-I have 'build-essential'
-I've downloaded the convert-lit source to my desktop
-I've downloaded libtommath to my desktop

-I right clicked and selected 'extract here' on both the convert-lit source and libtommath

-in the terminal, I changed to the libtommath-0.39 directory and typed 'make' resulting in no problems as far as I could see.

-I switched to clit18src/lib and again typed 'make', and I noticed a number of lines had a warning message

-I switched to clit18src/clit18 and again typed 'make', and almost every line had a warning or error message.

-using 'clit sourcefile.lit destination' doesn't work.

I'm still trying to learn my way around the command line, and I'm getting very frustrated.  I'm trying hard to end my dependence on another popular OS, so I've switched gears or given up on other applications that have given me similar problems.  I just don't understand why I can find very concise directions on how to install things, but when I copy commands and the author says I should see xyz message as a result, I'm getting error messages.  If I can figure this one out, I may brave the numerous possible ways of getting my WM5 PDA synced to Ubuntu and finally leave my wife's XP laptop alone.

---

### Post by jamh on 2008-05-20
Take a look inside the Makefile in the clit18 directory, make sure the name of libtommath is the same as the directory you downloaded.  For me it was libtommath-0.39 so my Makefile looks like:

<code>
all: clit

CFLAGS=-funsigned-char -Wall -O2 -I ../libtommath-0.39/ -I ../lib -I ../lib/des -I .
clean:
	rm -f *.o clit

clit: clit.o hexdump.o drm5.o explode.o transmute.o display.o utils.o manifest.o ../lib/openclit.a 
	gcc -o clit $^  ../libtommath-0.39/libtommath.a

</code>

---

