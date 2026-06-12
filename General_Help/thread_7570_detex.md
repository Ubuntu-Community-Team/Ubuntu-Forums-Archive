---
title: "detex"
date: 2004-12-08
forum: General Help
---

### Post by aurelian on 2004-12-08
Anyone had any success compiling detex? I got the source, detex-2.7.tar, from [http://www.cs.purdue.edu/homes/trinkle/detex/](http://www.cs.purdue.edu/homes/trinkle/detex/), but am getting a compilation error:

> sudo make all
gcc -O    -c -o detex.o detex.c
lex.yy.c:784: error: parse error before ']' token
In file included from lex.yy.c:809:
/usr/include/unistd.h:924: error: parse error before "__delta"
make: *** [detex.o] Error 1

(I edited the makefile to use flex instead of lex.)

Don't suppose anyone has put together a deb package for detex?

---

### Post by TheOtherShoe on 2005-12-15
Will untex work?

```
sudo apt-get install untex
```

---

### Post by naomi on 2006-01-08
untex works, BUT it doesn't ignore equations, hence you get lots of funny letters and symbols. so if you e.g. do a word count afterwards, you can't trust the result. It would be great, if somebody can tell us here, how to get detex to work - so far I couldn't make it to run on my Ubuntu machine.

---

