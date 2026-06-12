---
title: "trouble with pidgin plugin compilation"
date: 2007-07-03
forum: General Help
---

### Post by axeae on 2007-07-03
I'm trying to help my friend (Ubuntu Fiesty Fawn 32bit) install pidgin-latex. he currently has the latest build of pidgin compiled and the latest version of GAIM is installed as well.this is what is received after make:
```
john@john-desktop:~/Desktop/pidgin-latex$ sudo make install PREFIX="/usr"
Password:
Package pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pidgin' found
gcc  -fPIC -c LaTeX.c -o LaTeX.o  -I/usr/include/gtk-2.0
-I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo
-I/usr/include/pango-1.0 -I/usr/include/glib-2.0
-I/usr/lib/glib-2.0/include -I/usr/include/freetype2
-I/usr/include/libpng12   -DHAVE_CONFIG_H
In file included from LaTeX.c:32:
LaTeX.h:37:36: error: libpurple/conversation.h: No such file or directory
LaTeX.h:39:29: error: libpurple/debug.h: No such file or directory
LaTeX.h:40:31: error: libpurple/signals.h: No such file or directory
LaTeX.h:41:32: error: libpurple/imgstore.h: No such file or directory
LaTeX.h:42:28: error: libpurple/util.h: No such file or directory
LaTeX.h:43:30: error: libpurple/notify.h: No such file or directory
LaTeX.h:44:30: error: libpurple/server.h: No such file or directory
LaTeX.h:45:27: error: libpurple/log.h: No such file or directory
LaTeX.h:46:31: error: libpurple/version.h: No such file or directory
In file included from LaTeX.c:32:
LaTeX.h:79: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'is_blacklisted'
LaTeX.h:91: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'latex_to_image'
LaTeX.h:98: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'analyse'
LaTeX.h:109: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'pidgin_latex_write'
LaTeX.h:112: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'message_send'
LaTeX.h:115: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'message_recv'
LaTeX.c:47: error: expected ')' before '*' token
LaTeX.c: In function 'getdirname':
LaTeX.c:101: error: 'G_DIR_SEPARATOR' undeclared (first use in this function)
LaTeX.c:101: error: (Each undeclared identifier is reported only once
LaTeX.c:101: error: for each function it appears in.)
LaTeX.c:111: warning: incompatible implicit declaration of built-in
function 'malloc'
LaTeX.c: In function 'getfilename':
LaTeX.c:124: error: 'G_DIR_SEPARATOR' undeclared (first use in this function)
LaTeX.c:127: warning: incompatible implicit declaration of built-in
function 'malloc'
LaTeX.c:133: warning: incompatible implicit declaration of built-in
function 'malloc'
LaTeX.c: In function 'searchPATH':
LaTeX.c:161: warning: incompatible implicit declaration of built-in
function 'malloc'
LaTeX.c: In function 'execute':
LaTeX.c:232: warning: incompatible implicit declaration of built-in
function 'malloc'
LaTeX.c: At top level:
LaTeX.c:286: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'is_blacklisted'
LaTeX.c:301: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'latex_to_image'
LaTeX.c:374: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'analyse'
LaTeX.c:504: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'pidgin_latex_write'
LaTeX.c:534: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'message_send'
LaTeX.c:589: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'message_recv'
LaTeX.c:632: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'plugin_load'
LaTeX.c:646: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'plugin_unload'
LaTeX.c:657: error: expected '=', ',', ';', 'asm' or '__attribute__'
before 'info'
LaTeX.c:693: error: expected ')' before '*' token
LaTeX.c: In function 'PURPLE_INIT_PLUGIN':
LaTeX.c:697: error: expected '{' at end of input
make: *** [LaTeX.o] Error 1
john@john-desktop:~/Desktop/pidgin-latex$
```

---

### Post by ebash on 2007-07-03
Try to install the build dependencies of gaim:

```
sudo apt-get build-dep gaim
```

Then if the compilation process fails again, for every missing file use apt-file on the missing file (you will need to install apt-file) and recompile. Use apt-file this way:

```
apt-file search libpurple/conversation.h
```


Install apt-file:

```
sudo apt-get install apt-file; sudo apt-file update
```

---

### Post by Can+~ on 2007-10-19
> **ebash said:**
> Try to install the build dependencies of gaim:

```
sudo apt-get build-dep gaim
```


That's an insane huge file =O. I think you need something like gaim-dev.

---

### Post by Can+~ on 2007-10-19
After looking around, I found everything needed to compile the pidgin LaTeX. First you need to get the libpurple-dev:

```
sudo apt-get install libpurple-dev
```

Then make, and make install, and it's installed immediately. Also, he should uninstall everything related to gaim. AND! he needs to use [ImageMagick]("http://www.imagemagick.org/script/index.php")

PS. Sorry about the double posting. (at least I editted the first to look less suspicious).

---

