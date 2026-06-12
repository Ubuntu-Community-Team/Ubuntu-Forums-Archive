---
title: "Issue compiling extra compiz plugins"
date: 2007-12-11
forum: General Help
---

### Post by jjgy on 2007-12-11
I already tried posting this in the Desktop Effects & Customization forum, but it seems like this might be a more appropriate place for the trouble I'm having.  Having seen some of the effects that the extra compiz plugins have to offer, I (of course) went ahead and grabbed a few tarballs from some repos I looked up on [this forum]("http://forum.compiz-fusion.org/showthread.php?t=5303").  After sorting through some problems with missing packages and a bad compiz installation, I'm still stumped by a fresh set of compile errors.  People have pointed out shell scripts and such which go through the process of getting the plugins, putting the tarballs in a tmp folder then extracting and compiling, but the same issue arises.  I suppose I'll stop blabbering and let you guys take a look at the actual problem...

```

[user]@[machine]:~/compiz/snow$ make
compiling : snow.c -> build/snow.loIn file included from snow.c:39:
build/snow_options.h:15:27: error: compiz-common.h: No such file or directory
In file included from snow.c:39:
build/snow_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'CompPluginVTable'
snow.c:53: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'static'
snow.c: In function 'stepSnowPositions':
snow.c:151: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c:151: error: (Each undeclared identifier is reported only once
snow.c:151: error: for each function it appears in.)
snow.c: In function 'snowToggle':
snow.c:194: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowPaintOutput':
snow.c:326: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowDrawWindow':
snow.c:359: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'updateSnowTextures':
snow.c:435: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowInitScreen':
snow.c:513: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowFiniScreen':
snow.c:552: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowDisplayOptionChanged':
snow.c:580: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowInitDisplay':
snow.c:680: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowFiniDisplay':
snow.c:689: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowInit':
snow.c:698: error: 'displayPrivateIndex' undeclared (first use in this function)
snow.c: In function 'snowFini':
snow.c:708: error: 'displayPrivateIndex' undeclared (first use in this function)
make: *** [build/snow.lo] Error 1

```

---

