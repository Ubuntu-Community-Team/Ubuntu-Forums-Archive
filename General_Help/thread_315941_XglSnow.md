---
title: "XglSnow"
date: 2006-12-10
forum: General Help
---

### Post by penguinchrissy on 2006-12-10
I'm trying to install Xglsnow and I'm running into a problem heres the output;

dj@dj-laptop:~/Desktop/xglsnow-0.1.3$ make
-e compiling : snow.c -> build/libsnow.loPackage x11 was not found in the pkg-config search path.
Perhaps you should add the directory containing `x11.pc'
to the PKG_CONFIG_PATH environment variable
No package 'x11' found
Package beryl was not found in the pkg-config search path.
Perhaps you should add the directory containing `beryl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'beryl' found
/bin/sh: libtool: not found
make: *** [build/libsnow.lo] Error 127
dj@dj-laptop:~/Desktop/xglsnow-0.1.3$ make
-e compiling : snow.c -> build/libsnow.loPackage x11 was not found in the pkg-config search path.
Perhaps you should add the directory containing `x11.pc'
to the PKG_CONFIG_PATH environment variable
No package 'x11' found
Package beryl was not found in the pkg-config search path.
Perhaps you should add the directory containing `beryl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'beryl' found
snow.c:34:23: error: X11/Xatom.h: No such file or directory
snow.c:35:36: error: X11/extensions/Xrender.h: No such file or directory
snow.c:37:19: error: beryl.h: No such file or directory
snow.c:95: error: expected specifier-qualifier-list before 'Bool'
snow.c:105: error: expected declaration specifiers or '...' before 'CompWindow'
snow.c:114: error: expected specifier-qualifier-list before 'CompScreen'
snow.c: In function 'snowThink':
snow.c:143: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:143: error: 'SnowScreen' has no member named 's'
snow.c:144: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:145: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:145: error: 'SnowScreen' has no member named 's'
snow.c:146: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:147: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c: In function 'snowMove':
snow.c:157: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:157: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:157: error: 'SnowScreen' has no member named 'lastMsCount'
snow.c:158: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:158: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:158: error: 'SnowScreen' has no member named 'lastMsCount'
snow.c:159: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:159: error: 'SnowScreen' has no member named 'allSnowFlakes'
snow.c:159: error: 'SnowScreen' has no member named 'lastMsCount'
snow.c: In function 'setupDisplayList':
snow.c:198: error: 'SnowScreen' has no member named 'snowTextureLoaded'
snow.c:200: warning: implicit declaration of function 'enableTexture'
snow.c:200: error: 'SnowScreen' has no member named 's'
snow.c:200: error: 'SnowScreen' has no member named 'snowTexture'
snow.c:200: error: 'COMP_TEXTURE_FILTER_GOOD' undeclared (first use in this function)

at first it couldn't find a c- complier so I did apt-get install buildessentials 
then it couldn't find libtool so I installed that 
but I don't know what its looking for here.
Really want this to work its all christmas like!

---

### Post by strabes on 2006-12-10
Install the new beryl from the svn repo. It has that and many other new features. [http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/SVN_Snapshots_Repository](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/SVN_Snapshots_Repository)

---

### Post by penguinchrissy on 2006-12-10
Thanks for the quick reply. I did update but didn't think to check settings for anything new. This makes me happy. Now I'm NEVER going to study for finals!

---

### Post by nkassi on 2006-12-10
I know the feeling.

Should be studying too. 

:0) 

Nic

---

