---
title: "How to make a generic makefile"
date: 2018-10-11
forum: General Help
---

### Post by Arunomi on 2018-10-11
I'm trying to make a generic makefile for all my c programming assignments but i have som problems i can't figure out.

I made this make file that i have attached as a text file, i have seen that it works like a charm but 
when i changes lines in a a .h file the make file don't recompile all files associated with that file.
I cant see where i have gone wrong.

So pleas help. =)

Best regards Arunomi

---

### Post by edadasiewicz on 2018-10-12
It's been a while since I wrote a makefile, but I always had a line where my objects (.o) depended upon my include files (.h):

```

OBJS=a.o b.o
INCS=c.h

$(OBJS): $(INCS)

```

---

