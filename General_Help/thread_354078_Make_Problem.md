---
title: "Make Problem"
date: 2007-02-05
forum: General Help
---

### Post by OracleUK on 2007-02-05
Hi,

Trying to compile Zelda2d but keep getting the following errors:
```

tim@tim-desktop:~/Games/zelda2d-0.2.3$ make engine
make -C tinyxml
make[1]: Entering directory `/home/tim/Games/zelda2d-0.2.3/tinyxml'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/tim/Games/zelda2d-0.2.3/tinyxml'
make linux -C lua
make[1]: Entering directory `/home/tim/Games/zelda2d-0.2.3/lua'
make all MYCFLAGS=-DLUA_USE_LINUX MYLIBS="-Wl,-E -ldl -lreadline -lhistory -lncurses"
make[2]: Entering directory `/home/tim/Games/zelda2d-0.2.3/lua'
gcc -O2 -Wall -DLUA_USE_LINUX   -c -o lua.o lua.c
In file included from lua.h:16,
                 from lua.c:15:
luaconf.h:275:31: error: readline/readline.h: No such file or directory
luaconf.h:276:30: error: readline/history.h: No such file or directory
lua.c: In function ‘pushline’:
lua.c:180: warning: implicit declaration of function ‘readline’
lua.c:180: warning: assignment makes pointer from integer without a cast
lua.c: In function ‘loadline’:
lua.c:208: warning: implicit declaration of function ‘add_history’
make[2]: *** [lua.o] Error 1
make[2]: Leaving directory `/home/tim/Games/zelda2d-0.2.3/lua'
make[1]: *** [linux] Error 2
make[1]: Leaving directory `/home/tim/Games/zelda2d-0.2.3/lua'
make: *** [engine] Error 2

```

---

### Post by Ryan450 on 2007-02-05
looks like your missing files that are needed. might not be a bad idea to do a ./configure first if you havent done so already to ensure you have everything needed in your OS already. 

missing files in specific from what I can grab out of that msg is 

luaconf.h:275:31: error: readline/readline.h: No such file or directory
luaconf.h:276:30: error: readline/history.h: No such file or directory

make sure readline.h and history.h are where they need to be.

---

### Post by OracleUK on 2007-02-05
Thanks, but when I do a ./configure in the terminal I get:

```
bash: ./configure: No such file or directory

```

Also the source code doesn't come with readline.h and history.h so where would I get these from?

Thanks for your help.

Oracle

---

### Post by Ryan450 on 2007-02-05
have you installed the build-essential package from synaptic or apt-get?

---

### Post by OracleUK on 2007-02-05
Not following, sorry.

I found Build-Essential in Synaptic  and yes it was already installed.

Regards,

Oracle

---

### Post by lamego on 2007-02-05
You will probably need to install the package:
libreadline5-dev

I am trying to build it now :)

---

### Post by OracleUK on 2007-02-05
Thank you both, its now compiled and working.

Oracle

---

