---
title: "Compiling user-selector-applet"
date: 2005-03-29
forum: General Help
---

### Post by RicardoBarrios on 2005-03-29
Hi, i've tried to compile user-selector-applet in a hoary distro, but it dont work..., i've this error

```
esco-screen-manager.c:29:23: X11/Xauth.h: No such file or directory
esco-screen-manager.c: In function `esco_screen_manager_update':
esco-screen-manager.c:264: warning: implicit declaration of function `XauFileName'
esco-screen-manager.c:264: warning: format argument is not a pointer (arg 4)
esco-screen-manager.c: In function `esco_screen_manager_get_this_screen':
esco-screen-manager.c:480: warning: format argument is not a pointer (arg 4)
esco-screen-manager.c: In function `esco_screen_manager_set_screen':
esco-screen-manager.c:553: warning: format argument is not a pointer (arg 4)
esco-screen-manager.c: In function `esco_screen_manager_new_screen':
esco-screen-manager.c:611: warning: format argument is not a pointer (arg 4)
make[3]: *** [libesco_gdm_a-esco-screen-manager.o] Error 1
make[3]: Leaving directory `/home/ricardo/user-selector-applet-0.0.7.tar.gz_FILES/user-selector-applet-0.0.7/src/esco-gdm'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ricardo/user-selector-applet-0.0.7.tar.gz_FILES/user-selector-applet-0.0.7/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ricardo/user-selector-applet-0.0.7.tar.gz_FILES/user-selector-applet-0.0.7'
make: *** [all] Error 2
```

some idea? thanks

---

