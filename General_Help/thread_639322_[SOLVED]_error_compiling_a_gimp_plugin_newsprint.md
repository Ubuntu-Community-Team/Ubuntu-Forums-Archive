---
title: "[SOLVED] error compiling a gimp plugin: newsprint"
date: 2007-12-13
forum: General Help
---

### Post by solarbrad on 2007-12-13
I need some compiling help.  After reading other posts, I installed the build-essential and libgimp2.0-dev, but I still the get the following errors when I try to compile the source code with gimptool.

brad@brad-ubuntu:~/Desktop/newsprint$ gimptool --install newsprint.c
/usr/bin/install -c -d /home/brad/.gimp-2.2/plug-ins
cc -g -Wall -O2 -I/usr/include/gimp-2.0 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -o /home/brad/.gimp-2.2/plug-ins/newsprint newsprint.c -L/usr/lib -lgimpui-2.0 -lgimpwidgets-2.0 -lgimp-2.0 -lgimpcolor-2.0 -lgimpmath-2.0 -lgimpbase-2.0 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
newsprint.c:462: error: expected declaration specifiers or ‘...’ before ‘GParam’
newsprint.c:464: error: expected declaration specifiers or ‘...’ before ‘GParam’
newsprint.c:466: error: expected ‘)’ before ‘*’ token
newsprint.c:478: error: expected ‘)’ before ‘*’ token
newsprint.c:499: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PLUG_IN_INFO’
newsprint.c: In function ‘main’:
newsprint.c:511: error: ‘PLUG_IN_INFO’ undeclared (first use in this function)
newsprint.c:511: error: (Each undeclared identifier is reported only once
newsprint.c:511: error: for each function it appears in.)
newsprint.c: In function ‘query’:
newsprint.c:516: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘args’
newsprint.c:516: error: ‘args’ undeclared (first use in this function)
newsprint.c:516: error: expected expression before ‘]’ token
newsprint.c:539: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
newsprint.c:539: error: ‘return_vals’ undeclared (first use in this function)
newsprint.c:556: error: ‘PROC_PLUG_IN’ undeclared (first use in this function)
newsprint.c: At top level:
newsprint.c:564: error: expected declaration specifiers or ‘...’ before ‘GParam’
newsprint.c:566: error: expected declaration specifiers or ‘...’ before ‘GParam’
newsprint.c: In function ‘run’:
newsprint.c:568: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘values’
newsprint.c:568: error: ‘values’ undeclared (first use in this function)
newsprint.c:569: error: ‘GDrawable’ undeclared (first use in this function)
newsprint.c:569: error: ‘drawable’ undeclared (first use in this function)
newsprint.c:570: error: ‘GRunModeType’ undeclared (first use in this function)
newsprint.c:570: error: expected ‘;’ before ‘run_mode’
newsprint.c:571: error: ‘GStatusType’ undeclared (first use in this function)
newsprint.c:571: error: expected ‘;’ before ‘status’
newsprint.c:573: error: ‘run_mode’ undeclared (first use in this function)
newsprint.c:573: error: ‘param’ undeclared (first use in this function)
newsprint.c:576: error: ‘return_vals’ undeclared (first use in this function)
newsprint.c:578: error: ‘PARAM_STATUS’ undeclared (first use in this function)
newsprint.c:579: error: ‘status’ undeclared (first use in this function)
newsprint.c:590: error: ‘RUN_INTERACTIVE’ undeclared (first use in this function)
newsprint.c:596: warning: implicit declaration of function ‘newsprint_dialog’
newsprint.c:603: error: ‘RUN_NONINTERACTIVE’ undeclared (first use in this function)
newsprint.c:607: error: ‘STATUS_CALLING_ERROR’ undeclared (first use in this function)
newsprint.c:635: error: ‘RUN_WITH_LAST_VALS’ undeclared (first use in this function)
newsprint.c:644: error: ‘STATUS_SUCCESS’ undeclared (first use in this function)
newsprint.c:647: warning: implicit declaration of function ‘gimp_drawable_color’
newsprint.c:648: warning: implicit declaration of function ‘gimp_drawable_gray’
newsprint.c:656: warning: implicit declaration of function ‘newsprint’
newsprint.c:673: error: ‘STATUS_EXECUTION_ERROR’ undeclared (first use in this function)
newsprint.c: At top level:
newsprint.c:1076: error: expected ‘)’ before ‘*’ token
newsprint.c:1665: error: expected ‘)’ before ‘*’ token
newsprint.c: In function ‘entscale_new’:
newsprint.c:2042: warning: implicit declaration of function ‘strcpy’
newsprint.c:2042: warning: incompatible implicit declaration of built-in function ‘strcpy’

---

### Post by solarbrad on 2007-12-24
re-installed gimp and it had the plugin already installed.

---

