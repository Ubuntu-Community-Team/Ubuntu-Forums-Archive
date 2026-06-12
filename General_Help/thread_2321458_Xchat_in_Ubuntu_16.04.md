---
title: "Xchat in Ubuntu 16.04"
date: 2016-04-22
forum: General Help
---

### Post by b4nny on 2016-04-22
Hello. I wanted to give a try Ubuntu 16.04 today. It seems everything is ok after fresh install so far.  Since there is no current release of this source package           in the Xenial, I wanted to install it manually. I downloaded the package and
```
./configure
``` is ok but when try to make;
```
make  all-recursive
make[1]: Entering directory '/home/satan/Desktop/xchat-2.8.8'
Making all in po
make[2]: Entering directory '/home/satan/Desktop/xchat-2.8.8/po'
make[2]: Leaving directory '/home/satan/Desktop/xchat-2.8.8/po'
Making all in intl
make[2]: Entering directory '/home/satan/Desktop/xchat-2.8.8/intl'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/satan/Desktop/xchat-2.8.8/intl'
Making all in src
make[2]: Entering directory '/home/satan/Desktop/xchat-2.8.8/src'
Making all in pixmaps
make[3]: Entering directory '/home/satan/Desktop/xchat-2.8.8/src/pixmaps'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/satan/Desktop/xchat-2.8.8/src/pixmaps'
Making all in common
make[3]: Entering directory '/home/satan/Desktop/xchat-2.8.8/src/common'
Making all in .
make[4]: Entering directory '/home/satan/Desktop/xchat-2.8.8/src/common'
depbase=`echo cfgfiles.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`;\
gcc -DHAVE_CONFIG_H -I. -I../.. -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include    -g -O2 -Wall -pipe -Wno-pointer-sign -funsigned-char  -MT cfgfiles.o -MD -MP -MF $depbase.Tpo -c -o cfgfiles.o cfgfiles.c &&\
mv -f $depbase.Tpo $depbase.Po
In file included from xchat.h:3:0,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gslist.h:29:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/gslist.h:32:0,
                 from xchat.h:3,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gmem.h:29:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/gmem.h:32:0,
                 from /usr/include/glib-2.0/glib/gslist.h:32,
                 from xchat.h:3,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gutils.h:29:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/gutils.h:32:0,
                 from /usr/include/glib-2.0/glib/gmem.h:32,
                 from /usr/include/glib-2.0/glib/gslist.h:32,
                 from xchat.h:3,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gtypes.h:29:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/gtypes.h:34:0,
                 from /usr/include/glib-2.0/glib/gutils.h:32,
                 from /usr/include/glib-2.0/glib/gmem.h:32,
                 from /usr/include/glib-2.0/glib/gslist.h:32,
                 from xchat.h:3,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gversionmacros.h:29:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/gslist.h:33:0,
                 from xchat.h:3,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gnode.h:29:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from xchat.h:4:0,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/glist.h:29:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from xchat.h:6:0,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/giochannel.h:29:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/giochannel.h:32:0,
                 from xchat.h:6,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gconvert.h:29:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/gconvert.h:32:0,
                 from /usr/include/glib-2.0/glib/giochannel.h:32,
                 from xchat.h:6,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gerror.h:24:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/gerror.h:29:0,
                 from /usr/include/glib-2.0/glib/gconvert.h:32,
                 from /usr/include/glib-2.0/glib/giochannel.h:32,
                 from xchat.h:6,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gquark.h:29:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/giochannel.h:33:0,
                 from xchat.h:6,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gmain.h:22:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/gmain.h:27:0,
                 from /usr/include/glib-2.0/glib/giochannel.h:33,
                 from xchat.h:6,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gthread.h:29:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/gthread.h:32:0,
                 from /usr/include/glib-2.0/glib/gmain.h:27,
                 from /usr/include/glib-2.0/glib/giochannel.h:33,
                 from xchat.h:6,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gatomic.h:24:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/giochannel.h:34:0,
                 from xchat.h:6,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gstring.h:29:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/gstring.h:33:0,
                 from /usr/include/glib-2.0/glib/giochannel.h:34,
                 from xchat.h:6,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gunicode.h:25:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/gstring.h:34:0,
                 from /usr/include/glib-2.0/glib/giochannel.h:34,
                 from xchat.h:6,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gbytes.h:26:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from /usr/include/glib-2.0/glib/gbytes.h:30:0,
                 from /usr/include/glib-2.0/glib/gstring.h:34,
                 from /usr/include/glib-2.0/glib/giochannel.h:34,
                 from xchat.h:6,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/garray.h:29:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from xchat.h:7:0,
                 from cfgfiles.c:27:
/usr/include/glib-2.0/glib/gstrfuncs.h:29:2: error: #error "Only <glib.h> can be included directly."
 #error "Only <glib.h> can be included directly."
  ^
In file included from cfgfiles.c:27:0:
xchat.h:565:41: error: missing binary operator before token "("
 #if defined(WIN32) && GLIB_CHECK_VERSION(2,4,0)
                                         ^
cfgfiles.c: In function ‘list_loadconf’:
cfgfiles.c:126:2: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result [-Wunused-result]
  read (fh, ibuf, st.st_size);
  ^
Makefile:445: recipe for target 'cfgfiles.o' failed
make[4]: *** [cfgfiles.o] Error 1
make[4]: Leaving directory '/home/satan/Desktop/xchat-2.8.8/src/common'
Makefile:481: recipe for target 'all-recursive' failed
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory '/home/satan/Desktop/xchat-2.8.8/src/common'
Makefile:342: recipe for target 'all-recursive' failed
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory '/home/satan/Desktop/xchat-2.8.8/src'
Makefile:451: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/satan/Desktop/xchat-2.8.8'
Makefile:338: recipe for target 'all' failed
make: *** [all] Error 2

```

Any chance to install xchat on xenial?

---

### Post by slickymaster on 2016-04-22
Just as a heads up, XChat hasn't been maintained actively, [almost since 2010]("http://xchat.org/"). So you'd probably should think in using another client.

I'd advise you to try [HexChat]("https://hexchat.github.io/") which in fact is a fork of XChat.

---

### Post by b4nny on 2016-04-22
Well I was happy with it in any ubuntu distro. I like the way it's simple.  Let's see If we can figure out something with it.

I solved this via ppa manager:```
sudo add-apt-repository ppa:webupd8team/y-ppa-manager
sudo apt update
sudo apt install y-ppa-manager
```

and then searched for 'xchat' in all launchpad ppas:

[HTML]http://i64.tinypic.com/m76ipt.png[/HTML]


and then;
```
sudo apt-get install xchat
```

there we go!

---

### Post by fmigpaulo-s on 2016-04-27
```
sudo apt-get install hexchat
```  Awesome. Great advice. HexChat is just like xchat (which I preferred 100x over xchat-gnome) Thank you!

---

