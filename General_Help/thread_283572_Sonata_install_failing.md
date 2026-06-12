---
title: "Sonata install failing"
date: 2006-10-24
forum: General Help
---

### Post by InspirationDate on 2006-10-24
I'm trying to install [Sonata]("http://sonata.berlios.de/") but the install can't seem to find pygtk even though I have the python2.4-gnome2 package installed.  I'm sure there is an easy fix but I haven't been able to find the answer.

Here is the error output:
```
mike@mike-laptop:~/sonata-0.8.1$ sudo python setup.py install
Password:
Package pygtk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `pygtk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pygtk-2.0' found
Package pygtk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `pygtk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pygtk-2.0' found
running install
running build
running build_py
running build_ext
building 'mmkeys' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O3 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.4 -c mmkeys/mmkeyspy.c -o build/temp.linux-i686-2.4/mmkeys/mmkeyspy.o
mmkeys.override:6:23: error: pygobject.h: No such file or directory
In file included from mmkeys.override:7:
mmkeys/mmkeys.h:23:21: error: gdk/gdk.h: No such file or directory
mmkeys/mmkeys.h:24:22: error: gdk/gdkx.h: No such file or directory
mmkeys/mmkeys.h:26:33: error: gtk/gtktogglebutton.h: No such file or directory
In file included from mmkeys.override:7:
mmkeys/mmkeys.h:43: error: syntax error before ‘GObject’
mmkeys/mmkeys.h:43: warning: no semicolon at end of struct or union
mmkeys/mmkeys.h:48: error: syntax error before ‘GObjectClass’
mmkeys/mmkeys.h:48: warning: no semicolon at end of struct or union
mmkeys/mmkeys.h:51: error: syntax error before ‘mmkeys_get_type’
mmkeys/mmkeys.h:51: warning: type defaults to ‘int’ in declaration of ‘mmkeys_get_type’
mmkeys/mmkeys.h:51: warning: data definition has no type or storage class
mmkeys.c:30: error: syntax error before ‘*’ token
mmkeys.c:31: warning: function declaration isn’t a prototype
mmkeys.c: In function ‘_wrap_mmkeys_new’:
mmkeys.c:34: error: ‘args’ undeclared (first use in this function)
mmkeys.c:34: error: (Each undeclared identifier is reported only once
mmkeys.c:34: error: for each function it appears in.)
mmkeys.c:34: error: ‘kwargs’ undeclared (first use in this function)
mmkeys.c:37: warning: implicit declaration of function ‘pygobject_constructv’
mmkeys.c:37: error: ‘self’ undeclared (first use in this function)
mmkeys.c: At top level:
mmkeys.c:52: error: ‘PyGObject’ undeclared here (not in a function)
mmkeys.c:75: error: syntax error before ‘PyGObject’
mmkeys.c:85: error: syntax error before ‘PyGObject’
mmkeys.c: In function ‘mmkeys_register_classes’:
mmkeys.c:124: warning: implicit declaration of function ‘pygobject_register_class’
mmkeys.c:125: warning: implicit declaration of function ‘pyg_set_object_has_new_constructor’
error: command 'gcc' failed with exit status 1

```

Thanks

---

### Post by aanderse on 2006-10-28
you are trying to compile it, so make sure you have the -dev files.  so try something like sudo apt-get install python2.4-dev
or search synaptic for the package that is named something like that.

always make sure you have the -dev packages when compiling :)

---

### Post by InspirationDate on 2006-10-29
Thanks a bunch.  I got it working.
I already had python2.4-dev installed so I tried a few other packages and one of them worked for me.

For reference, it was one of these:

python-gnome2-desktop-dev
python-gnome2-dev
python-gobject-dev
python-gtk2-dev

---

