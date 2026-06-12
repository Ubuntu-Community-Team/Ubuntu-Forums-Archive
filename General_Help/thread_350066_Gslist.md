---
title: "Gslist"
date: 2007-01-31
forum: General Help
---

### Post by KeeganX on 2007-01-31
I recently downloaded XQF as a substitution for Gamespy Arcade on my Ubuntu system, so I can play Medal of Honor Allied Assault.  My problem is or I think it is, is that I need a program called gslist.  I can't find it in the repository and I've been all over google trying to find it.  If anyone knows  a place I can get it, that would be greatly appreciated.

---

### Post by taux on 2007-01-31
Is this what you were searching for?:

[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Fortune/Gslist-5213.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Fortune/Gslist-5213.shtml)

---

### Post by KeeganX on 2007-01-31
I've downloaded this one before.  I tried to compile it, but I get this error

```
keegan@keegan-desktop:~/Desktop/gslist$ make
cc -O2 -s   -c -o src/gslist.o src/gslist.c
cc -O2 -s   -c -o src/enctype1_decoder.o src/enctype1_decoder.c
cc -O2 -s   -c -o src/enctype2_decoder.o src/enctype2_decoder.c
cc -O2 -s   -c -o src/enctype_shared.o src/enctype_shared.c
cc -O2 -s   -c -o src/mydownlib.o src/mydownlib.c
cc src/gslist.c src/enctype1_decoder.c src/enctype2_decoder.c src/enctype_shared.c src/mydownlib.c -O2 -s -o gslist -lpthread -lmysqlclient -DGSWEB -DSQL
In file included from src/gslist.c:315:
src/gssql.h:21:25: error: mysql/mysql.h: No such file or directory
In file included from src/gslist.c:315:
src/gssql.h:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dbase’
src/gssql.h: In function ‘gssql_init’:
src/gssql.h:75: error: ‘dbase’ undeclared (first use in this function)
src/gssql.h:75: error: (Each undeclared identifier is reported only once
src/gssql.h:75: error: for each function it appears in.)
src/gssql.h: In function ‘gssql_later’:
src/gssql.h:96: error: ‘dbase’ undeclared (first use in this function)
src/gssql.h: In function ‘gssql_close’:
src/gssql.h:111: error: ‘dbase’ undeclared (first use in this function)
src/gssql.h: In function ‘gssql’:
src/gssql.h:128: error: ‘dbase’ undeclared (first use in this function)
make: *** [gslist] Error 1

```

---

### Post by KeeganX on 2007-02-01
Bump,

If someone could elaborate on that it would be really awesome, I never was good at compiling things :(

---

### Post by taux on 2007-02-03
I can not help you with the error, but you could try this workaround:

First install a wine windows emulator if you don't have one:

```
apt-get install wine
```

Then download the original gslist from its creator page

[http://aluigi.altervista.org/papers.htm#gslist](http://aluigi.altervista.org/papers.htm#gslist)

Unzip it, enter the unzipped dir and write in your console

```
wine gslist.exe
```

Good luck!

---

### Post by moopoo on 2007-05-11
I'd like to confirm KeeganX's problem. It's the same on my computer (running Feisty). Someone mentioned that maybe the mysql-devel files were missing. I could not find anything like that in the repos. Reinstalling mysql and co did not help.

Any clue anyone? Thanks in advance,
moo

---

### Post by deadite66 on 2007-12-17
just compiled this in gutsy

needed:
libmysql++-dev
&
libgeoip-dev

---

