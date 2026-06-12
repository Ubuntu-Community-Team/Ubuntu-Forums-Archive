---
title: "Trouble compiling Gpsdrive svn"
date: 2007-09-18
forum: General Help
---

### Post by mykrob on 2007-09-18
Hey-
I am trying to compile and install the svn version of gpsdrive so i can use openstreetmaps.
I have satisfied the dependencies to get through the configure stage, but i get errors on make:

```

myk@kubuntu:~/Downloads/gpsdrive/gpsdrive-2.10pre4$ make
make  all-recursive
make[1]: Entering directory `/home/myk/Downloads/gpsdrive/gpsdrive-2.10pre4'
Making all in src
make[2]: Entering directory `/home/myk/Downloads/gpsdrive/gpsdrive-2.10pre4/src'
make[3]: Entering directory `/home/myk/Downloads/gpsdrive/gpsdrive-2.10pre4/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DLOCALEDIR=\"/usr/local/share/locale\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DFRIENDSSERVERVERSION=\"2\"    -I/usr/include/ -I/usr/local/include -I/opt/boost_1_35/include/boost-1_35 -I/usr/local/include/freetype2 -I/usr/include/freetype2 -I. -L/usr/local/lib -I. -I. -I..     -g -O2 -g -Wall -Wno-format-y2k -pipe  -DHAVE_GTK   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libart-2.0   -I/usr/include/libxml2   -DHAVE_CAIRO -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12    -Imysql  -MT gpsdrive.o -MD -MP -MF ".deps/gpsdrive.Tpo" -c -o gpsdrive.o gpsdrive.c; \
        then mv -f ".deps/gpsdrive.Tpo" ".deps/gpsdrive.Po"; else rm -f ".deps/gpsdrive.Tpo"; exit 1; fi
In file included from gpsdrive.c:78:
./gpsdrive_config.h:35:25: error: mysql/mysql.h: No such file or directory
In file included from gpsdrive.c:95:
gpsdrive.h:31:25: error: mysql/mysql.h: No such file or directory
In file included from gpsdrive.c:95:
gpsdrive.h:242: error: expected ‘)’ before ‘*’ token
gpsdrive.h:243: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gpsdrive.h:244: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gpsdrive.h:251: error: expected ‘)’ before ‘*’ token
gpsdrive.h:252: error: expected ‘)’ before ‘*’ token
gpsdrive.h:253: error: expected declaration specifiers or ‘...’ before ‘*’ token
gpsdrive.h:253: error: expected ‘)’ before ‘*’ token
gpsdrive.h:254: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gpsdrive.h:255: error: expected declaration specifiers or ‘...’ before ‘*’ token
gpsdrive.h:255: error: expected ‘)’ before ‘*’ token
gpsdrive.h:256: error: expected ‘)’ before ‘*’ token
gpsdrive.h:257: error: expected declaration specifiers or ‘...’ before ‘*’ token
gpsdrive.h:257: error: expected ‘)’ before ‘*’ token
make[3]: *** [gpsdrive.o] Error 1
make[3]: Leaving directory `/home/myk/Downloads/gpsdrive/gpsdrive-2.10pre4/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/myk/Downloads/gpsdrive/gpsdrive-2.10pre4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/myk/Downloads/gpsdrive/gpsdrive-2.10pre4'
make: *** [all] Error 2
myk@kubuntu:~/Downloads/gpsdrive/gpsdrive-2.10pre4$                       

```

any ideas? Looks to me like it has something to do with mysql, but i have the mysql client and server installed..

Help?

Thanks,
-myk

---

### Post by graham-cracker on 2007-09-18
You may want to see if there are any  -dev packages that you're missing. I am unfamiliar with openstreetmaps, so I'm not sure what you might want to look for, but possibly:

libmysqlclient15-dev
or
libmysql++-dev

Hopefully this helps.
(I'm using the Gutsy repos, so the packages might be named differently)

---

### Post by mykrob on 2007-09-18
that got it, but produced another error.. Based on what you gave me, looks like i will just need to add dev files for whatever is referenced in each error.

thanks,
-myk

---

### Post by mykrob on 2007-09-18
dang it... seems like i just cannot satisfy all the dependencies necessary, and the documentation doesnt give much info..

Heck, even the official .deb file for the svn doesnt work.. must just be a messed up source or something..

anybody else able to do this?

-myk

---

### Post by mykrob on 2007-09-25
bump

---

### Post by Sqweeks on 2007-12-02
anyone having any luck compiling GpsDrive 2.10pre4 on Gutsy?

---

### Post by kelvinn on 2007-12-02
I've compiled GpsDrive 2.10pre4 on Gutsy.  I agree, the documentation could use a little work, yet I just went through and installed each dependency individually when required.  I wasn't able to get GpsDrive to install with the SVN version of Mapnik, but it installed fine with 0.4 -- your mileage may vary.  If you don't need Mapnik support, you can easily --disable-mapnik

If you post an error message, I might be able to steer you (no pun intended) in the correct direction.

---

### Post by haylocki on 2007-12-19
Hi, I have the latest svn version of gpsdrive running on my laptop, but am unable to get the mapnik maps to display.

What are your current dependency errors ?

maybe I can help you solve all your dependency problems.

Had gpsdrive working perfect under Feisty, but it'sbeen a long slog getting it going on Gutsy.

You might also want to consider joining the gpsdrive mailing list. Joerg Ostertag is normally very helpful with peoples gpsdrive problems.

Cheers, Ian

---

