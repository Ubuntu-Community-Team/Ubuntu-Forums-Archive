---
title: "Problem compiling awsome window manager"
date: 2008-01-05
forum: General Help
---

### Post by brenix on 2008-01-05
I am trying to compile awesome window manager, but am receiving errors. Here is what I get:

```

awesome-2.0 $ make
awesome build options:
LAYOUTS  = layouts/tile.c layouts/floating.c layouts/max.c
Package xft was not found in the pkg-config search path.
Perhaps you should add the directory containing `xft.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xft' found
CFLAGS   = -fgnu89-inline -std=gnu99 -ggdb3 -pipe -Wall -Wextra -W -Wchar-subscripts -Wundef -Wshadow -Wcast-align -Wwrite-strings -Wsign-compare -Wunused -Wuninitialized -Winit-self -Wpointer-arith -Wredundant-decls -Wno-format-zero-length -Wmissing-prototypes -Wmissing-format-attribute -Wmissing-noreturn -O3 -I. -I/usr/include -I/usr/include/X11  -DVERSION="2.0" -DRELEASE="Fruit Fly"
Package xft was not found in the pkg-config search path.
Perhaps you should add the directory containing `xft.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xft' found
LDFLAGS  = -ggdb3 -L/usr/lib -lc -L/usr/lib/X11 -lX11  -lXext -lXrandr -lXinerama
CC       = cc
-e      (CC) client.c
Package xft was not found in the pkg-config search path.
Perhaps you should add the directory containing `xft.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xft' found
client.c:24:34: error: X11/extensions/shape.h: No such file or directory
In file included from common.h:25,
                 from client.h:25,
                 from screen.h:25,
                 from client.c:26:
config.h:26:25: error: X11/Xft/Xft.h: No such file or directory
In file included from common.h:25,
                 from client.h:25,
                 from screen.h:25,
                 from client.c:26:
config.h:229: error: expected specifier-qualifier-list before &#8216;XftFont&#8217;
In file included from client.c:26:
screen.h:27:37: error: X11/extensions/Xinerama.h: No such file or directory
In file included from client.c:26:
screen.h:29: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;ScreenInfo&#8217;
screen.h:31: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
screen.h:32: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
In file included from client.c:32:
statusbar.h:27: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;XftFont&#8217;
client.c: In function &#8216;client_ban&#8217;:
client.c:118: error: &#8216;IconicState&#8217; undeclared (first use in this function)
client.c:118: error: (Each undeclared identifier is reported only once
client.c:118: error: for each function it appears in.)
client.c: In function &#8216;focus&#8217;:
client.c:184: error: &#8216;awesome_config&#8217; has no member named &#8216;clients&#8217;
client.c:215: error: &#8216;awesome_config&#8217; has no member named &#8216;clients&#8217;
client.c: In function &#8216;client_manage&#8217;:
client.c:267: error: &#8216;ScreenInfo&#8217; undeclared (first use in this function)
client.c:267: error: &#8216;screen_info&#8217; undeclared (first use in this function)
client.c:292: warning: implicit declaration of function &#8216;get_screen_info&#8217;
client.c:304: error: &#8216;display_info&#8217; undeclared (first use in this function)
client.c:304: warning: implicit declaration of function &#8216;get_display_info&#8217;
client.c:317: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;__ptr&#8217;
client.c:319: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;__ptr&#8217;
client.c:337: warning: implicit declaration of function &#8216;XShapeSelectInput&#8217;
client.c:337: error: &#8216;ShapeNotifyMask&#8217; undeclared (first use in this function)
client.c:348: error: &#8216;awesome_config&#8217; has no member named &#8216;clients&#8217;
client.c:360: error: &#8216;awesome_config&#8217; has no member named &#8216;clients&#8217;
client.c: In function &#8216;client_resize&#8217;:
client.c:377: error: &#8216;ScreenInfo&#8217; undeclared (first use in this function)
client.c:377: error: &#8216;si&#8217; undeclared (first use in this function)
client.c:427: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;__ptr&#8217;
client.c:451: warning: implicit declaration of function &#8216;XineramaIsActive&#8217;
client.c: In function &#8216;client_unban&#8217;:
client.c:486: error: &#8216;NormalState&#8217; undeclared (first use in this function)
client.c: In function &#8216;client_unmanage&#8217;:
client.c:499: error: &#8216;awesome_config&#8217; has no member named &#8216;clients&#8217;
client.c:510: error: &#8216;NormalState&#8217; undeclared (first use in this function)
client.c: In function &#8216;updatesizehints&#8217;:
client.c:520: error: &#8216;XSizeHints&#8217; undeclared (first use in this function)
client.c:520: error: expected &#8216;;&#8217; before &#8216;size&#8217;
client.c:522: warning: implicit declaration of function &#8216;XGetWMNormalHints&#8217;
client.c:522: error: &#8216;size&#8217; undeclared (first use in this function)
client.c:523: error: &#8216;PSize&#8217; undeclared (first use in this function)
client.c:525: error: &#8216;PBaseSize&#8217; undeclared (first use in this function)
client.c:530: error: &#8216;PMinSize&#8217; undeclared (first use in this function)
client.c:537: error: &#8216;PResizeInc&#8217; undeclared (first use in this function)
client.c:545: error: &#8216;PMaxSize&#8217; undeclared (first use in this function)
client.c:566: error: &#8216;PAspect&#8217; undeclared (first use in this function)
client.c: In function &#8216;uicb_client_swapnext&#8217;:
client.c:692: error: &#8216;awesome_config&#8217; has no member named &#8216;clients&#8217;
client.c: In function &#8216;uicb_client_swapprev&#8217;:
client.c:711: error: &#8216;awesome_config&#8217; has no member named &#8216;clients&#8217;
make: *** [client.o] Error 1


```

The dependencies should all be installed. The website says it must have libcairo-dev and libconfused, which I have installed both. Can anyone help me on this?

---

### Post by Craigus on 2008-01-05
Have you installed build-essential ?

---

### Post by brenix on 2008-01-06
yea, build essential had been installed. Though i managed to compile the program. Not exactly sure which library it took, but I took a guess and downloaded some :P . Thanks!

---

### Post by marties on 2008-01-14
for whose interested, i managed to install awesome 2-0 under Gutsy doing 
```
apt-get install libxrandr-dev libxinerama-dev libconfuse-dev libxft-dev libcairo2-dev libx11-dev
```

---

