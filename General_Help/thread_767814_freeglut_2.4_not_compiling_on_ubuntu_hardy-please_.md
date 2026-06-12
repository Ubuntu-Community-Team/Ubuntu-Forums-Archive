---
title: "freeglut 2.4 not compiling on ubuntu hardy-please help"
date: 2008-04-25
forum: General Help
---

### Post by ashjas on 2008-04-25
Hi,

I am trying to make freeglut 2.4 on ubuntu.on ubuntu 7.1 it used to make fine...but on hardy its giving errors...

the errors are::
```

 make
make  all-recursive
make[1]: Entering directory `/home/ashish/Desktop/freeglut-2.4.0'
Making all in src
make[2]: Entering directory `/home/ashish/Desktop/freeglut-2.4.0/src'
source='freeglut_callbacks.c' object='libglut_la-freeglut_callbacks.lo' libtool=yes \
        depfile='.deps/libglut_la-freeglut_callbacks.Plo' tmpdepfile='.deps/libglut_la-freeglut_callbacks.TPlo' \
        depmode=gcc3 /bin/bash ../depcomp \
        /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include    -g -O2 -Wall -pedantic -Werror -c -o libglut_la-freeglut_callbacks.lo `test -f freeglut_callbacks.c || echo './'`freeglut_callbacks.c
rm -f .libs/libglut_la-freeglut_callbacks.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include -g -O2 -Wall -pedantic -Werror -c freeglut_callbacks.c -MT libglut_la-freeglut_callbacks.lo -MD -MP -MF .deps/libglut_la-freeglut_callbacks.TPlo  -fPIC -DPIC -o .libs/libglut_la-freeglut_callbacks.lo
In file included from ../include/GL/freeglut.h:17,
                 from freeglut_callbacks.c:28:
../include/GL/freeglut_std.h:114:19: error: GL/gl.h: No such file or directory
../include/GL/freeglut_std.h:115:20: error: GL/glu.h: No such file or directory
In file included from ../include/GL/freeglut.h:17,
                 from freeglut_callbacks.c:28:
../include/GL/freeglut_std.h:432: error: expected ')' before 'layer'
../include/GL/freeglut_std.h:491: error: expected ')' before 'query'
../include/GL/freeglut_std.h:492: error: expected ')' before 'query'
../include/GL/freeglut_std.h:494: error: expected ')' before 'query'
../include/GL/freeglut_std.h:509: error: expected ')' before 'size'
../include/GL/freeglut_std.h:510: error: expected ')' before 'size'
../include/GL/freeglut_std.h:511: error: expected ')' before 'radius'
../include/GL/freeglut_std.h:512: error: expected ')' before 'radius'
../include/GL/freeglut_std.h:513: error: expected ')' before 'base'
../include/GL/freeglut_std.h:514: error: expected ')' before 'base'
../include/GL/freeglut_std.h:516: error: expected ')' before 'innerRadius'
../include/GL/freeglut_std.h:517: error: expected ')' before 'innerRadius'
../include/GL/freeglut_std.h:530: error: expected ')' before 'size'
../include/GL/freeglut_std.h:531: error: expected ')' before 'size'
../include/GL/freeglut_std.h:539: error: expected ')' before 'query'
../include/GL/freeglut_std.h:544: error: expected ')' before 'query'
../include/GL/freeglut_std.h:553: error: expected declaration specifiers or '...' before 'GLfloat'
../include/GL/freeglut_std.h:553: error: expected declaration specifiers or '...' before 'GLfloat'
../include/GL/freeglut_std.h:553: error: expected declaration specifiers or '...' before 'GLfloat'
../include/GL/freeglut_std.h:554: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'glutGetColor'
In file included from ../include/GL/freeglut.h:18,
                 from freeglut_callbacks.c:28:
../include/GL/freeglut_ext.h:97: error: expected ')' before 'option_flag'
../include/GL/freeglut_ext.h:108: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'glutStrokeHeight'
../include/GL/freeglut_ext.h:117: error: expected declaration specifiers or '...' before 'GLdouble'
../include/GL/freeglut_ext.h:117: error: expected declaration specifiers or '...' before 'GLdouble'
../include/GL/freeglut_ext.h:118: error: expected declaration specifiers or '...' before 'GLdouble'
../include/GL/freeglut_ext.h:118: error: expected declaration specifiers or '...' before 'GLdouble'
../include/GL/freeglut_ext.h:119: error: expected ')' before 'radius'
../include/GL/freeglut_ext.h:120: error: expected ')' before 'radius'
In file included from freeglut_callbacks.c:29:
freeglut_internal.h:95:24: error: GL/glx.h: No such file or directory
freeglut_internal.h:96:26: error: X11/Xlib.h: No such file or directory
freeglut_internal.h:97:27: error: X11/Xatom.h: No such file or directory
freeglut_internal.h:98:28: error: X11/keysym.h: No such file or directory
In file included from freeglut_callbacks.c:29:
freeglut_internal.h:176: error: expected specifier-qualifier-list before 'GLint'
cc1: warnings being treated as errors
freeglut_internal.h:178: warning: struct has no members
freeglut_internal.h:189: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:211: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:254: error: expected specifier-qualifier-list before 'Display'
freeglut_internal.h:285: warning: struct has no members
freeglut_internal.h:304: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'SFG_WindowHandleType'
freeglut_internal.h:305: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'SFG_WindowContextType'
freeglut_internal.h:321: error: expected specifier-qualifier-list before 'SFG_WindowHandleType'
freeglut_internal.h:331: warning: struct has no members
freeglut_internal.h:342: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:503: error: expected specifier-qualifier-list before 'XVisualInfo'
freeglut_internal.h:507: warning: struct has no members
freeglut_internal.h:521: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:539: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:565: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:605: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:607: warning: struct has no members
freeglut_internal.h:617: error: expected ':', ',', ';', '}' or '__attribute__' before '*' token
freeglut_internal.h:627: error: expected specifier-qualifier-list before 'GLfloat'
freeglut_internal.h:628: warning: struct has no members
freeglut_internal.h:640: error: expected specifier-qualifier-list before 'GLfloat'
freeglut_internal.h:643: warning: struct has no members
freeglut_internal.h:650: error: expected specifier-qualifier-list before 'GLfloat'
freeglut_internal.h:732: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
freeglut_internal.h:750: error: expected declaration specifiers or '...' before 'GLboolean'
freeglut_internal.h:750: error: expected declaration specifiers or '...' before 'GLboolean'
freeglut_internal.h:753: error: expected declaration specifiers or '...' before 'GLboolean'
freeglut_internal.h:754: error: expected declaration specifiers or '...' before 'GLboolean'
freeglut_internal.h:799: error: expected ')' before 'hWindow'
freeglut_internal.h:819: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'fgCheckActiveMenu'
freeglut_callbacks.c: In function 'glutDisplayFunc':
freeglut_callbacks.c:49: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutReshapeFunc':
freeglut_callbacks.c:61: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutKeyboardFunc':
freeglut_callbacks.c:71: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpecialFunc':
freeglut_callbacks.c:80: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutIdleFunc':
freeglut_callbacks.c:89: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:90: error: 'SFG_State' has no member named 'IdleCallback'
freeglut_callbacks.c: In function 'glutTimerFunc':
freeglut_callbacks.c:101: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:103: error: 'SFG_State' has no member named 'FreeTimers'
freeglut_callbacks.c:105: error: 'SFG_State' has no member named 'FreeTimers'
freeglut_callbacks.c:118: error: 'SFG_State' has no member named 'Timers'
freeglut_callbacks.c:124: error: 'SFG_State' has no member named 'Timers'
freeglut_callbacks.c: In function 'fghVisibility':
freeglut_callbacks.c:134: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutVisibilityFunc':
freeglut_callbacks.c:144: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutKeyboardUpFunc':
freeglut_callbacks.c:159: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpecialUpFunc':
freeglut_callbacks.c:168: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutJoystickFunc':
freeglut_callbacks.c:179: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:183: error: 'SFG_WindowState' has no member named 'JoystickPollRate'
freeglut_callbacks.c:185: error: 'SFG_WindowState' has no member named 'JoystickLastPoll'
freeglut_callbacks.c:186: error: 'SFG_WindowState' has no member named 'JoystickPollRate'
freeglut_callbacks.c:188: error: 'SFG_WindowState' has no member named 'JoystickLastPoll'
freeglut_callbacks.c:189: error: 'SFG_WindowState' has no member named 'JoystickLastPoll'
freeglut_callbacks.c: In function 'glutMouseFunc':
freeglut_callbacks.c:197: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutMouseWheelFunc':
freeglut_callbacks.c:206: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutMotionFunc':
freeglut_callbacks.c:216: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutPassiveMotionFunc':
freeglut_callbacks.c:226: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutEntryFunc':
freeglut_callbacks.c:235: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutCloseFunc':
freeglut_callbacks.c:244: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutWMCloseFunc':
freeglut_callbacks.c:250: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutMenuDestroyFunc':
freeglut_callbacks.c:257: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutMenuStateFunc':
freeglut_callbacks.c:267: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:268: error: 'SFG_State' has no member named 'MenuStateCallback'
freeglut_callbacks.c: In function 'glutMenuStatusFunc':
freeglut_callbacks.c:276: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:277: error: 'SFG_State' has no member named 'MenuStatusCallback'
freeglut_callbacks.c: In function 'glutOverlayDisplayFunc':
freeglut_callbacks.c:285: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutWindowStatusFunc':
freeglut_callbacks.c:294: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpaceballMotionFunc':
freeglut_callbacks.c:303: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpaceballRotateFunc':
freeglut_callbacks.c:312: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpaceballButtonFunc':
freeglut_callbacks.c:321: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutButtonBoxFunc':
freeglut_callbacks.c:330: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutDialsFunc':
freeglut_callbacks.c:339: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutTabletMotionFunc':
freeglut_callbacks.c:348: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutTabletButtonFunc':
freeglut_callbacks.c:357: error: 'SFG_State' has no member named 'Initialised'
make[2]: *** [libglut_la-freeglut_callbacks.lo] Error 1
make[2]: Leaving directory `/home/ashish/Desktop/freeglut-2.4.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ashish/Desktop/freeglut-2.4.0'
make: *** [all] Error 2

```

Kindly help to sort this out...
Thanks verymuch...

---

