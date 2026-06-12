---
title: "need file of xlibint.h, xlib.h, etc"
date: 2005-10-03
forum: General Help
---

### Post by fsshl on 2005-10-03
dear ubuntu linux user:

  I am in new 5.10(2.6.12-9-386), when i try to compile (just in /configure stage) some benchmark code, I get many errors, especially lacking xlibint.h, xlib.h, etc.
-------------------------------------------------------------------------------------------------
ln -s EnvLINUX.c Env.c
gcc -c Env.c -o Release/Linux32/Env.o  -O3 -Ivpaux/libaux -I/usr/X11R6/include/ -I/usr/X11R6/lib/include/ -Ilibpng/include -DXWINDOWS -DSEARCHPATH -DLINUX -DPNGEnv.c:17:25: error: X11/Xlibint.h: No such file or directory
Env.c:18:22: error: X11/Xlib.h: No such file or directory
Env.c:19:23: error: X11/Xutil.h: No such file or directory
Env.c:20:20: error: GL/glx.h: No such file or directory
Env.c:21:23: error: X11/Xatom.h: No such file or directory
In file included from Env.c:25:
vpaux/libaux/vpaux.h:15:19: error: GL/gl.h: No such file or directory
vpaux/libaux/vpaux.h:16:20: error: GL/glu.h: No such file or directory
In file included from Env.c:25:
vpaux/libaux/vpaux.h:67: error: syntax error before ‘GLint’
vpaux/libaux/vpaux.h:67: warning: no semicolon at end of struct or union
vpaux/libaux/vpaux.h:68: warning: data definition has no type or storage class
vpaux/libaux/vpaux.h:69: error: syntax error before ‘}’ token
vpaux/libaux/vpaux.h:69: warning: data definition has no type or storage class
vpaux/libaux/vpaux.h:209: error: syntax error before ‘GLint’
vpaux/libaux/vpaux.h:209: warning: no semicolon at end of struct or union
vpaux/libaux/vpaux.h:210: error: conflicting types for ‘data’
vpaux/libaux/vpaux.h:68: error: previous declaration of ‘data’ was here
------------------------------------------------------------------------------------------
  could any advancer point out where or how to intall these missing files?
thanks in advance, fsshl

---

### Post by Rinnan on 2005-10-20
[B]sudo apt-get install xlibs-dev
[/B]
Look for "dev" packages when you are missing headers, in general.

---

