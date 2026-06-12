---
title: "Installing Compiz Plugins for Hardy Heron"
date: 2008-05-06
forum: General Help
---

### Post by knudsenjoe on 2008-05-06
Hey all, I'm trying to install Compiz Plugins for Hardy Heron, and just can't figure it out. 

I have compiz in my Home folder, and withing home/compiz I have plugins as tar files. All works great in Gutsy, but when I try to untar in Hardy I run into problems.

1) I have been going to home/compiz
2) The command I'm using to untar is:
     tar -xf '/tmp/3d.tar.gz' -C ~/compiz/  (I have copies of all plugins in that tmp directory as well)
    I'm not sure if that -C is a hard drive, is that my problem? I have a triple boot setup with Vista-Gutsy-Hardy
3) Here's what it says when I use the command in (2)

Sorry for the length :)

convert   : 3d.xml.in -> build/3d.xml
bcop'ing  : build/3d.xml -> build/3d_options.h
bcop'ing  : build/3d.xml -> build/3d_options.c
schema    : build/3d.xml -> build/compiz-3d.schema
compiling : 3d.c -> build/3d.lo3d.c:46:18: error: cube.h: No such file or directory
In file included from 3d.c:47:
build/3d_options.h:19: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/3d_options.h:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/3d_options.h:68: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdGetMipmaps’
build/3d_options.h:72: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdGetDisableCulling’
build/3d_options.h:76: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdGetDisableCaps’
build/3d_options.h:80: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdGetManualOnly’
build/3d_options.h:88: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdGetBevelTopleft’
build/3d_options.h:92: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdGetBevelTopright’
build/3d_options.h:96: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdGetBevelBottomleft’
build/3d_options.h:100: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdGetBevelBottomright’
3d.c:57: error: expected specifier-qualifier-list before ‘Bool’
3d.c:67: error: expected specifier-qualifier-list before ‘Bool’
3d.c:77: error: expected specifier-qualifier-list before ‘Bool’
3d.c:132: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘windowIs3D’
3d.c:149: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘differentResolutions’
3d.c: In function ‘tdPreparePaintScreen’:
3d.c:216: error: dereferencing pointer to incomplete type
3d.c:216: error: dereferencing pointer to incomplete type
3d.c:217: warning: implicit declaration of function ‘CUBE_SCREEN’
3d.c:217: warning: nested extern declaration of ‘CUBE_SCREEN’
3d.c:219: error: ‘tdScreen’ has no member named ‘active’
3d.c:219: error: ‘cs’ undeclared (first use in this function)
3d.c:219: error: (Each undeclared identifier is reported only once
3d.c:219: error: for each function it appears in.)
3d.c:219: error: ‘RotationNone’ undeclared (first use in this function)
3d.c:220: warning: implicit declaration of function ‘tdGetManualOnly’
3d.c:220: warning: nested extern declaration of ‘tdGetManualOnly’
3d.c:221: error: ‘RotationManual’ undeclared (first use in this function)
3d.c:223: error: ‘tdScreen’ has no member named ‘currentMoMode’
3d.c:224: error: ‘tdScreen’ has no member named ‘currentViewportNum’
3d.c:224: error: dereferencing pointer to incomplete type
3d.c:225: error: ‘tdScreen’ has no member named ‘currentScreenNum’
3d.c:225: error: dereferencing pointer to incomplete type
3d.c:226: error: ‘tdScreen’ has no member named ‘currentDifferentResolutions’
3d.c:226: warning: implicit declaration of function ‘differentResolutions’
3d.c:226: warning: nested extern declaration of ‘differentResolutions’
3d.c:228: error: ‘tdScreen’ has no member named ‘currentMoMode’
3d.c:229: error: ‘tdScreen’ has no member named ‘currentViewportNum’
3d.c:229: error: dereferencing pointer to incomplete type
3d.c:230: error: ‘tdScreen’ has no member named ‘currentScreenNum’
3d.c:230: error: dereferencing pointer to incomplete type
3d.c:231: error: ‘tdScreen’ has no member named ‘currentDifferentResolutions’
3d.c:233: error: ‘tdScreen’ has no member named ‘currentViewportNum’
3d.c:234: error: ‘CUBE_MOMODE_MULTI’ undeclared (first use in this function)
3d.c:234: error: dereferencing pointer to incomplete type
3d.c:235: error: ‘tdScreen’ has no member named ‘xMove’
3d.c:236: error: ‘tdScreen’ has no member named ‘currentViewportNum’
3d.c:236: error: ‘tdScreen’ has no member named ‘currentViewportNum’
3d.c:238: error: ‘tdScreen’ has no member named ‘xMove’
3d.c:241: error: ‘tdScreen’ has no member named ‘active’
3d.c:243: error: ‘tdScreen’ has no member named ‘lastInViewportListSize’
3d.c:243: error: dereferencing pointer to incomplete type
3d.c:245: error: ‘tdScreen’ has no member named ‘lastInViewportList’
3d.c:246: error: ‘tdScreen’ has no member named ‘lastInViewportList’
3d.c:246: error: dereferencing pointer to incomplete type
3d.c:247: error: ‘tdScreen’ has no member named ‘lastInViewportListSize’
3d.c:247: error: dereferencing pointer to incomplete type
3d.c:250: error: dereferencing pointer to incomplete type
3d.c:251: error: ‘tdScreen’ has no member named ‘lastInViewportList’
3d.c:253: error: ‘tdScreen’ has no member named ‘maxZ’
3d.c:255: error: dereferencing pointer to incomplete type
3d.c:255: error: dereferencing pointer to incomplete type
3d.c:257: warning: implicit declaration of function ‘windowIs3D’
3d.c:257: warning: nested extern declaration of ‘windowIs3D’
3d.c:260: error: dereferencing pointer to incomplete type
3d.c:263: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:265: error: dereferencing pointer to incomplete type
3d.c:267: error: ‘tdScreen’ has no member named ‘lastInViewportList’
3d.c:267: error: ‘tdScreen’ has no member named ‘lastInViewportList’
3d.c:268: error: ‘tdScreen’ has no member named ‘lastInViewportList’
3d.c:270: error: ‘tdScreen’ has no member named ‘lastInViewportList’
3d.c:276: error: ‘tdScreen’ has no member named ‘maxZ’
3d.c:277: error: ‘tdScreen’ has no member named ‘maxZ’
3d.c:281: warning: implicit declaration of function ‘UNWRAP’
3d.c:281: warning: nested extern declaration of ‘UNWRAP’
3d.c:281: error: ‘preparePaintScreen’ undeclared (first use in this function)
3d.c:282: error: dereferencing pointer to incomplete type
3d.c:283: warning: implicit declaration of function ‘WRAP’
3d.c:283: warning: nested extern declaration of ‘WRAP’
3d.c: At top level:
3d.c:287: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdPaintWindow’
3d.c: In function ‘tdAddWindow’:
3d.c:570: error: dereferencing pointer to incomplete type
3d.c:570: error: dereferencing pointer to incomplete type
3d.c:571: error: dereferencing pointer to incomplete type
3d.c:571: error: dereferencing pointer to incomplete type
3d.c:571: error: dereferencing pointer to incomplete type
3d.c:573: error: ‘tdScreen’ has no member named ‘first’
3d.c:575: error: ‘tdScreen’ has no member named ‘first’
3d.c:575: error: ‘tdScreen’ has no member named ‘last’
3d.c:579: error: ‘tdScreen’ has no member named ‘last’
3d.c:580: error: ‘tdWindow’ has no member named ‘prev’
3d.c:580: error: ‘tdScreen’ has no member named ‘last’
3d.c:581: error: ‘tdScreen’ has no member named ‘last’
3d.c: At top level:
3d.c:586: warning: type defaults to ‘int’ in declaration of ‘ScreenPaintAttrib’
3d.c:586: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
3d.c:662: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdPaintOutput’
3d.c: In function ‘tdDonePaintScreen’:
3d.c:689: error: dereferencing pointer to incomplete type
3d.c:689: error: dereferencing pointer to incomplete type
3d.c:692: error: ‘tdScreen’ has no member named ‘active’
3d.c:692: error: ‘tdScreen’ has no member named ‘tdWindowExists’
3d.c:696: warning: implicit declaration of function ‘damageScreen’
3d.c:696: warning: nested extern declaration of ‘damageScreen’
3d.c:698: error: ‘tdScreen’ has no member named ‘tdWindowExists’
3d.c:698: error: ‘FALSE’ undeclared (first use in this function)
3d.c:700: error: dereferencing pointer to incomplete type
3d.c:700: error: dereferencing pointer to incomplete type
3d.c:702: error: dereferencing pointer to incomplete type
3d.c:702: error: dereferencing pointer to incomplete type
3d.c:702: error: dereferencing pointer to incomplete type
3d.c:705: error: ‘tdScreen’ has no member named ‘active’
3d.c:707: error: ‘cs’ undeclared (first use in this function)
3d.c:708: error: ‘tdScreen’ has no member named ‘maxZ’
3d.c:723: error: ‘tdScreen’ has no member named ‘tdWindowExists’
3d.c:723: error: ‘TRUE’ undeclared (first use in this function)
3d.c:727: error: ‘donePaintScreen’ undeclared (first use in this function)
3d.c:728: error: dereferencing pointer to incomplete type
3d.c: At top level:
3d.c:734: warning: type defaults to ‘int’ in declaration of ‘ScreenPaintAttrib’
3d.c:734: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
3d.c:754: warning: type defaults to ‘int’ in declaration of ‘ScreenPaintAttrib’
3d.c:754: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
3d.c: In function ‘tdWalkFirst’:
3d.c:775: error: dereferencing pointer to incomplete type
3d.c:775: error: dereferencing pointer to incomplete type
3d.c:776: error: ‘tdScreen’ has no member named ‘first’
3d.c:777: warning: control reaches end of non-void function
3d.c: In function ‘tdWalkLast’:
3d.c:782: error: dereferencing pointer to incomplete type
3d.c:782: error: dereferencing pointer to incomplete type
3d.c:783: error: ‘tdScreen’ has no member named ‘last’
3d.c:784: warning: control reaches end of non-void function
3d.c: In function ‘tdWalkNext’:
3d.c:789: error: dereferencing pointer to incomplete type
3d.c:789: error: dereferencing pointer to incomplete type
3d.c:789: error: dereferencing pointer to incomplete type
3d.c:790: error: ‘tdWindow’ has no member named ‘next’
3d.c:791: warning: control reaches end of non-void function
3d.c: In function ‘tdWalkPrev’:
3d.c:796: error: dereferencing pointer to incomplete type
3d.c:796: error: dereferencing pointer to incomplete type
3d.c:796: error: dereferencing pointer to incomplete type
3d.c:797: error: ‘tdWindow’ has no member named ‘prev’
3d.c:798: warning: control reaches end of non-void function
3d.c: At top level:
3d.c:801: error: expected declaration specifiers or ‘...’ before ‘CompWalker’
3d.c: In function ‘tdInitWindowWalker’:
3d.c:803: error: dereferencing pointer to incomplete type
3d.c:803: error: dereferencing pointer to incomplete type
3d.c:806: error: ‘initWindowWalker’ undeclared (first use in this function)
3d.c:807: error: dereferencing pointer to incomplete type
3d.c:807: error: ‘walker’ undeclared (first use in this function)
3d.c:810: error: ‘tdScreen’ has no member named ‘active’
3d.c:810: error: ‘tdScreen’ has no member named ‘tdWindowExists’
3d.c:811: error: ‘cs’ undeclared (first use in this function)
3d.c:811: error: ‘BTF’ undeclared (first use in this function)
3d.c: At top level:
3d.c:821: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdInitPluginForDisplay’
3d.c: In function ‘tdFiniPluginForDisplay’:
3d.c:880: error: dereferencing pointer to incomplete type
3d.c:882: error: ‘finiPluginForDisplay’ undeclared (first use in this function)
3d.c:883: error: dereferencing pointer to incomplete type
3d.c:886: error: dereferencing pointer to incomplete type
3d.c:889: error: dereferencing pointer to incomplete type
3d.c:889: error: dereferencing pointer to incomplete type
3d.c:891: error: dereferencing pointer to incomplete type
3d.c:891: error: dereferencing pointer to incomplete type
3d.c:892: error: ‘paintTransformedOutput’ undeclared (first use in this function)
3d.c:893: error: ‘paintWindow’ undeclared (first use in this function)
3d.c:894: error: ‘paintOutput’ undeclared (first use in this function)
3d.c:895: error: ‘donePaintScreen’ undeclared (first use in this function)
3d.c:896: error: ‘preparePaintScreen’ undeclared (first use in this function)
3d.c:897: error: ‘initWindowWalker’ undeclared (first use in this function)
3d.c: At top level:
3d.c:904: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdInitPluginForScreen’
3d.c: In function ‘tdFiniPluginForScreen’:
3d.c:929: error: dereferencing pointer to incomplete type
3d.c:929: error: dereferencing pointer to incomplete type
3d.c:931: error: ‘finiPluginForScreen’ undeclared (first use in this function)
3d.c:932: error: dereferencing pointer to incomplete type
3d.c:935: error: dereferencing pointer to incomplete type
3d.c:939: error: ‘cs’ undeclared (first use in this function)
3d.c:939: error: ‘paintTop’ undeclared (first use in this function)
3d.c:940: error: ‘paintBottom’ undeclared (first use in this function)
3d.c: At top level:
3d.c:944: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdInitDisplay’
3d.c: In function ‘tdFiniDisplay’:
3d.c:969: error: dereferencing pointer to incomplete type
3d.c:971: warning: implicit declaration of function ‘freeScreenPrivateIndex’
3d.c:971: warning: nested extern declaration of ‘freeScreenPrivateIndex’
3d.c:973: error: ‘initPluginForDisplay’ undeclared (first use in this function)
3d.c:974: error: ‘finiPluginForDisplay’ undeclared (first use in this function)
3d.c: At top level:
3d.c:979: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdInitScreen’
3d.c: In function ‘tdFiniScreen’:
3d.c:1027: error: dereferencing pointer to incomplete type
3d.c:1027: error: dereferencing pointer to incomplete type
3d.c:1029: warning: implicit declaration of function ‘freeWindowPrivateIndex’
3d.c:1029: warning: nested extern declaration of ‘freeWindowPrivateIndex’
3d.c:1031: error: ‘tdScreen’ has no member named ‘lastInViewportList’
3d.c:1032: error: ‘tdScreen’ has no member named ‘lastInViewportList’
3d.c:1034: error: ‘initPluginForScreen’ undeclared (first use in this function)
3d.c:1035: error: ‘finiPluginForScreen’ undeclared (first use in this function)
3d.c: At top level:
3d.c:1040: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdInitWindow’
3d.c: In function ‘tdFiniWindow’:
3d.c:1063: error: dereferencing pointer to incomplete type
3d.c:1063: error: dereferencing pointer to incomplete type
3d.c:1063: error: dereferencing pointer to incomplete type
3d.c: At top level:
3d.c:1068: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdInit’
3d.c: In function ‘tdFini’:
3d.c:1080: warning: implicit declaration of function ‘freeDisplayPrivateIndex’
3d.c:1080: warning: nested extern declaration of ‘freeDisplayPrivateIndex’
3d.c: In function ‘tdGetVersion’:
3d.c:1085: error: ‘ABIVERSION’ undeclared (first use in this function)
3d.c:1086: warning: control reaches end of non-void function
3d.c: At top level:
3d.c:1088: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tdVTable’
3d.c:1106: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/3d.lo] Error 1


Any help would be much appreciated.


HARDY ROCKS !!!!!!!!!!!!!!!!!!!!

---

### Post by qwerty12 on 2008-05-06
I think you are missing a -dev package which has the header files needed to compile, I've never compiled plugins so I can't tell you which one sorry.
> 
compiling : 3d.c -> build/3d.lo3d.c:46:18: error: cube.h: No such file or directory

cube.h will be in a -dev package somewhere and because that cube.h cannot be found, it cannot get the definitions from that file etc.

---

### Post by redserpent7 on 2008-05-10
same here, anyone knows the package that contains the header

---

