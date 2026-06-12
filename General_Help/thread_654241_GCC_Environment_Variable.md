---
title: "GCC Environment Variable"
date: 2007-12-30
forum: General Help
---

### Post by jsatubnutufroums on 2007-12-30
Hi, 
I write a make file:
```

VPATH    = src include
CPPFLAGS = -I include

count_words: count_words.o counter.o lexer.o -lfl
        gcc $^  -o $@

count_words.o: count_words.c
        gcc  -c $<

counter.o: counter.c
        gcc  -c $<

lexer.o: lexer.c
        gcc  -c $<

lexer.c: lexer.l
        flex -t $< > $@

clean:
        rm -f *.o lexer.c
```
When I command 'make', GNU make shows me:
```
gcc -c src/counter.c
src/counter.c:1:19: error: lexer.h: No such file or directory
src/counter.c:2:21: error: counter.h: No such file or directory
src/counter.c: In function ‘counter’:
src/counter.c:9: error: ‘fee_count’ undeclared (first use in this function)
src/counter.c:9: error: (Each undeclared identifier is reported only once
src/counter.c:9: error: for each function it appears in.)
src/counter.c:10: error: ‘fie_count’ undeclared (first use in this function)
src/counter.c:11: error: ‘foe_count’ undeclared (first use in this function)
src/counter.c:12: error: ‘fum_count’ undeclared (first use in this function)
make: *** [counter.o] Error 1
```
I understand what's the problem is. So I modify the make file as
```
VPATH    = src include
CPPFLAGS = -I include

count_words: count_words.o counter.o lexer.o -lfl
        gcc $^ [COLOR="Red"]$(CPPFLAGS)[/COLOR] -o $@

count_words.o: count_words.c
        gcc [COLOR="Red"]$(CPPFLAGS)[/COLOR] -c $<

counter.o: counter.c
        gcc [COLOR="Red"]$(CPPFLAGS)[/COLOR] -c $<

lexer.o: lexer.c
        gcc [COLOR="Red"]$(CPPFLAGS)[/COLOR] -c $<

lexer.c: lexer.l
        flex -t $< > $@
```
Ok! Let's see the following 'reduced form'
```
VPATH    = src include
CPPFLAGS = -I include

count_words: counter.o lexer.o -lfl
count_words.o: counter.h
counter.o: counter.h lexer.h
lexer.o: lexer.h
clean:
        rm -f *.o lexer.c
```
This make file just adds [[COLOR="Blue"]CPPFLAGS = -I include[/COLOR]] and the C compiler knows how to find the include file from 'include' directory. But in the first make file, why does GNU make show me error?
Thank you.

---

