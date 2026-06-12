---
title: "After install Ubuntu 17.10 got some error ?!"
date: 2017-11-11
forum: General Help
---

### Post by fairbird on 2017-11-11
After install ubunt 17.10 I have got some troubles with some my build work on ubuntu 14.10 I did not got it like that error ..

1-I cannot run (tor-browser) says to me
```
Failed to add a plugin to the panel
No running instance of xfce4-panel was found
```
```
raed@fairbird:~$ xfce4-panel -q
/usr/share/themes/Ambiance/gtk-2.0/apps/mate-panel.rc:30: error: invalid string constant "murrine-scrollbar", expected valid string constant


(xfce4-panel:7575): GLib-WARNING **: (../../../../glib/gerror.c:407):g_error_new_valist: runtime check failed: (domain != 0)

```

2-After use sudo gedit and save file I got warring
 ```
raed@fairbird:~$ sudo gedit /boot/grub/grub.cfg

** (gedit:9123): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-language not supported



```

3-If I want to build emu (ncam I got also error)
```
/home/raed/NCam/cross/powerpc-tuxbox-linux-gnu/bin/../lib/gcc/powerpc-linux/3.4.4/../../../../powerpc-linux/bin/ld:/home/raed/NCam/cross/powerpc-tuxbox-linux-gnu/bin/../lib/gcc/powerpc-linux/3.4.4/../../../../powerpc-linux/lib/crt1.o: file format not recognized; treating as linker script/home/raed/NCam/cross/powerpc-tuxbox-linux-gnu/bin/../lib/gcc/powerpc-linux/3.4.4/../../../../powerpc-linux/bin/ld:/home/raed/NCam/cross/powerpc-tuxbox-linux-gnu/bin/../lib/gcc/powerpc-linux/3.4.4/../../../../powerpc-linux/lib/crt1.o:1: syntax error
collect2: ld returned 1 exit status
Makefile:420: recipe for target 'ncam.ppc.debug' failed
make[2]: *** [ncam.ppc.debug] Error 1
Makefile:389: recipe for target 'all' failed
make[1]: *** [all] Error 2
Makefile.extra:318: recipe for target 'cross-powerpc-tuxbox-linux' failed
make: *** [cross-powerpc-tuxbox-linux] Error 2
```

and

```
In file included from cscrypt/bn_add.c:1In file included from cscrypt/bn_asm.c:1:cscrypt/bn.h:77:30: stdio.h: No such file or directory
cscrypt/bn_asm.c:69:20: assert.h: No such file or directory
In file included from cscrypt/bn_ctx.c:1:
cscrypt/bn.h:77:30: stdio.h: No such file or directory
cscrypt/bn_ctx.c:67:20: assert.h: No such file or directory
:
cscrypt/bn.h:77:30: stdio.h: No such file or directory
Makefile:437: recipe for target 'build/powerpc-tuxbox-linux-gnu/cscrypt/bn_add.o' failed
make[2]: *** [build/powerpc-tuxbox-linux-gnu/cscrypt/bn_add.o] Error 1
make[2]: *** Waiting for unfinished jobs....
Makefile:437: recipe for target 'build/powerpc-tuxbox-linux-gnu/cscrypt/bn_ctx.o' failed
make[2]: *** [build/powerpc-tuxbox-linux-gnu/cscrypt/bn_ctx.o] Error 1
In file included from cscrypt/aes.c:1:
cscrypt/aes.h:18:20: stdint.h: No such file or directory
cscrypt/aes.c:5:20: assert.h: No such file or directory
cscrypt/aes.c:6:20: stdlib.h: No such file or directory
cscrypt/aes.c:7:20: string.h: No such file or directory
Makefile:437: recipe for target 'build/powerpc-tuxbox-linux-gnu/cscrypt/aes.o' failed
make[2]: *** [build/powerpc-tuxbox-linux-gnu/cscrypt/aes.o] Error 1
Makefile:437: recipe for target 'build/powerpc-tuxbox-linux-gnu/cscrypt/bn_asm.o' failed
make[2]: *** [build/powerpc-tuxbox-linux-gnu/cscrypt/bn_asm.o] Error 1
Makefile:389: recipe for target 'all' failed
make[1]: *** [all] Error 2
Makefile.extra:325: recipe for target 'cross-ppc-tuxbox-linux' failed
make: *** [cross-ppc-tuxbox-linux] Error 2
```

Thank you

---

