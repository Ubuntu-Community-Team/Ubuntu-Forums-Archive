---
title: "{help} any easy way to install anaglyph plugin ?"
date: 2008-05-25
forum: General Help
---

### Post by dr_gauravsuneja on 2008-05-25
is there any easy way to install anayglyph 3d plugin in hardy .sometimes it works sometimes it give errors .i am usingthe guide given here


#1   Install the packages required for compiling plugins:
    Code:
   

sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool


#2   Make a compiz subdirectory in your home directory:
    Code:

mkdir -p ~/compiz/


Anaglyph Code:

wget -O /tmp/anaglyphz.tar.gz 'http://members.cox.net/mushroomlake/anaglyphz.tar.gz'

Code:

tar -xf '/tmp/anaglyphz.tar.gz' -C ~/compiz/

Code:

cd ~/compiz/anaglyphz-0.6

Code:

make

Code:

sudo make install




IT IS GIVING ME THE FOLLOWING ERROR


compiling : anaglyph.c -> build/anaglyph.loIn file included from anaglyph.c:12:
build/anaglyph_options.h:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/anaglyph_options.h:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/anaglyph_options.h:51: error: expected declaration specifiers or ‘...’ before ‘CompActionCallBackProc’
build/anaglyph_options.h:52: error: expected declaration specifiers or ‘...’ before ‘CompActionCallBackProc’
build/anaglyph_options.h:56: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/anaglyph_options.h:57: error: expected declaration specifiers or ‘...’ before ‘CompActionCallBackProc’
build/anaglyph_options.h:58: error: expected declaration specifiers or ‘...’ before ‘CompActionCallBackProc’
build/anaglyph_options.h:62: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/anaglyph_options.h:66: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/anaglyph_options.h:78: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘anaglyphGetDesaturate’
anaglyph.c:49: error: expected specifier-qualifier-list before ‘PaintWindowProc’
anaglyph.c:62: error: expected specifier-qualifier-list before ‘Bool’
anaglyph.c: In function ‘toggleAnaglyphWindow’:
anaglyph.c:71: error: dereferencing pointer to incomplete type
anaglyph.c:71: error: dereferencing pointer to incomplete type
anaglyph.c:71: error: dereferencing pointer to incomplete type
anaglyph.c:73: error: ‘AnaglyphWindow’ has no member named ‘isAnaglyph’
anaglyph.c:73: error: ‘AnaglyphWindow’ has no member named ‘isAnaglyph’
anaglyph.c:75: warning: implicit declaration of function ‘matchEval’
anaglyph.c:75: warning: nested extern declaration of ‘matchEval’
anaglyph.c:75: warning: implicit declaration of function ‘anaglyphGetExcludeMatch’
anaglyph.c:75: warning: nested extern declaration of ‘anaglyphGetExcludeMatch’
anaglyph.c:75: error: dereferencing pointer to incomplete type
anaglyph.c:76: error: ‘AnaglyphWindow’ has no member named ‘isAnaglyph’
anaglyph.c:76: error: ‘FALSE’ undeclared (first use in this function)
anaglyph.c:76: error: (Each undeclared identifier is reported only once
anaglyph.c:76: error: for each function it appears in.)
anaglyph.c:78: warning: implicit declaration of function ‘addWindowDamage’
anaglyph.c:78: warning: nested extern declaration of ‘addWindowDamage’
anaglyph.c: In function ‘toggleAnaglyphScreen’:
anaglyph.c:86: error: dereferencing pointer to incomplete type
anaglyph.c:86: error: dereferencing pointer to incomplete type
anaglyph.c:88: error: ‘AnaglyphScreen’ has no member named ‘isAnaglyph’
anaglyph.c:88: error: ‘AnaglyphScreen’ has no member named ‘isAnaglyph’
anaglyph.c:90: error: dereferencing pointer to incomplete type
anaglyph.c:90: error: dereferencing pointer to incomplete type
anaglyph.c: At top level:
anaglyph.c:98: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘anaglyphAnaglyphWindow’
anaglyph.c:122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘anaglyphAnaglyphScreen’
anaglyph.c:144: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘anaglyphDrawWindow’
anaglyph.c:249: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘anaglyphPaintOutput’
anaglyph.c: In function ‘anaglyphWindowAddNotify’:
anaglyph.c:270: error: dereferencing pointer to incomplete type
anaglyph.c:272: error: dereferencing pointer to incomplete type
anaglyph.c:272: error: dereferencing pointer to incomplete type
anaglyph.c:274: warning: implicit declaration of function ‘UNWRAP’
anaglyph.c:274: warning: nested extern declaration of ‘UNWRAP’
anaglyph.c:274: error: ‘windowAddNotify’ undeclared (first use in this function)
anaglyph.c:275: error: dereferencing pointer to incomplete type
anaglyph.c:276: warning: implicit declaration of function ‘WRAP’
anaglyph.c:276: warning: nested extern declaration of ‘WRAP’
anaglyph.c:278: error: ‘AnaglyphScreen’ has no member named ‘isAnaglyph’
anaglyph.c:278: warning: implicit declaration of function ‘anaglyphGetAnaglyphMatch’
anaglyph.c:278: warning: nested extern declaration of ‘anaglyphGetAnaglyphMatch’
anaglyph.c: In function ‘anaglyphScreenOptionChanged’:
anaglyph.c:293: error: dereferencing pointer to incomplete type
anaglyph.c:293: error: dereferencing pointer to incomplete type
anaglyph.c:295: error: dereferencing pointer to incomplete type
anaglyph.c:295: error: dereferencing pointer to incomplete type
anaglyph.c:297: error: ‘Bool’ undeclared (first use in this function)
anaglyph.c:297: error: expected ‘;’ before ‘isAnaglyph’
anaglyph.c:298: error: dereferencing pointer to incomplete type
anaglyph.c:298: error: dereferencing pointer to incomplete type
anaglyph.c:298: error: dereferencing pointer to incomplete type
anaglyph.c:300: error: ‘isAnaglyph’ undeclared (first use in this function)
anaglyph.c:303: error: ‘AnaglyphScreen’ has no member named ‘isAnaglyph’
anaglyph.c:303: error: ‘AnaglyphWindow’ has no member named ‘isAnaglyph’
anaglyph.c:305: error: ‘AnaglyphWindow’ has no member named ‘isAnaglyph’
anaglyph.c: At top level:
anaglyph.c:321: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘anaglyphInitDisplay’
anaglyph.c: In function ‘anaglyphFiniDisplay’:
anaglyph.c:348: error: dereferencing pointer to incomplete type
anaglyph.c:350: warning: implicit declaration of function ‘freeScreenPrivateIndex’
anaglyph.c:350: warning: nested extern declaration of ‘freeScreenPrivateIndex’
anaglyph.c: At top level:
anaglyph.c:358: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘anaglyphInitScreen’
anaglyph.c: In function ‘anaglyphFiniScreen’:
anaglyph.c:393: error: dereferencing pointer to incomplete type
anaglyph.c:393: error: dereferencing pointer to incomplete type
anaglyph.c:395: warning: implicit declaration of function ‘freeWindowPrivateIndex’
anaglyph.c:395: warning: nested extern declaration of ‘freeWindowPrivateIndex’
anaglyph.c:398: error: ‘paintOutput’ undeclared (first use in this function)
anaglyph.c:399: error: ‘paintWindow’ undeclared (first use in this function)
anaglyph.c:400: error: ‘windowAddNotify’ undeclared (first use in this function)
anaglyph.c: At top level:
anaglyph.c:407: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘anaglyphInitWindow’
anaglyph.c: In function ‘anaglyphFiniWindow’:
anaglyph.c:428: error: dereferencing pointer to incomplete type
anaglyph.c:428: error: dereferencing pointer to incomplete type
anaglyph.c:428: error: dereferencing pointer to incomplete type
anaglyph.c: At top level:
anaglyph.c:440: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘anaglyphInit’
anaglyph.c: In function ‘anaglyphFini’:
anaglyph.c:459: warning: implicit declaration of function ‘freeDisplayPrivateIndex’
anaglyph.c:459: warning: nested extern declaration of ‘freeDisplayPrivateIndex’
anaglyph.c: In function ‘anaglyphGetVersion’:
anaglyph.c:471: error: ‘ABIVERSION’ undeclared (first use in this function)
anaglyph.c:472: warning: control reaches end of non-void function
anaglyph.c: At top level:
anaglyph.c:474: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘anaglyphVTable’
anaglyph.c:492: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/anaglyph.lo] Error 1



what to do?

---

### Post by Forlong on 2008-05-25
Install git
```
sudo apt-get install git-core
```

And take the code from here:
```
git clone git://anongit.compiz-fusion.org/users/wodor/anaglyph
```

---

### Post by dr_gauravsuneja on 2008-05-25
> **Forlong said:**
> Install git
```
sudo apt-get install git-core
```

And take the code from here:
```
git clone git://anongit.compiz-fusion.org/users/wodor/anaglyph
```

thanks dear but synaptic said git core already install but it worked now thanks a ton

---

