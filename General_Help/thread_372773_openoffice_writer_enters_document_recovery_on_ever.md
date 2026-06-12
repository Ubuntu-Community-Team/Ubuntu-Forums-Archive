---
title: "openoffice writer enters document recovery on every startup, then crashes"
date: 2007-02-28
forum: General Help
---

### Post by onocrotalus on 2007-02-28
Hi, I've installed ooffice via synaptic on edgy 6.10 (I had removed it before becuase I was using Abiword). Every time I try and open a document, the program sys it has crashed, and tries to recover a document - even when one wasn't open. When I run it from the terminal, the following nasty stuff apears:
```
joe@joe-laptop:~$ ooffice -writer
libGL warning: 3D driver claims to not support visual 0x4b

(process:7170): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:7170): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

```

Also, the font looks horrible, as in the attached shot.

Any ideas about how to fix these problems will be very gratefully received.

Thanks.

---

### Post by keithbraafladt on 2007-05-30
Hi I'm having what looks like the exact same problem, has anyone written with solutions or suggestions?
Keith

---

### Post by Crafty Kisses on 2007-05-30
> **onocrotalus said:**
> Hi, I've installed ooffice via synaptic on edgy 6.10 (I had removed it before becuase I was using Abiword). Every time I try and open a document, the program sys it has crashed, and tries to recover a document - even when one wasn't open. When I run it from the terminal, the following nasty stuff apears:
```
joe@joe-laptop:~$ ooffice -writer
libGL warning: 3D driver claims to not support visual 0x4b

(process:7170): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:7170): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

```

Also, the font looks horrible, as in the attached shot.

Any ideas about how to fix these problems will be very gratefully received.

Thanks.
This has happened to me too, basically you should try uninstalling "OpenOffice Writer" and try installing it through AutoMatix or something to that nature and if that doesn't work I'll look into it for you. I installed it using Automatix and it worked for me.

---

### Post by onocrotalus on 2007-05-30
Upgrading to Feisty and getting OOffice 2.2 solved the problem for me.

---

