---
title: "Program fails to compile due to oddly named ubuntu libraries - help!"
date: 2007-04-13
forum: General Help
---

### Post by Antioch on 2007-04-13
I'm trying to install gnome-avrdude which is in no repos, and for which no package exists (for any distro).

[http://sourceforge.net/projects/gnome-avrdude/](http://sourceforge.net/projects/gnome-avrdude/)

However, when I run the configure script included with the source, it complains:

```
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libglade-2.0' found
```

However these packages are indeed installed. Unfortunately Ubuntu names these packages in an odd way: libgnome2-0, libgnomeui2-0, and libglade-0.

How can I get this script to successfully run and compile/install the program?

Thank you very much.

---

### Post by taurus on 2007-04-13
You probably need the development packages of those libraries, -dev.

---

### Post by qamelian on 2007-04-13
Since you're compiling from source you need to source code for those packages. The source code packages have the same name with -dev tacked on the end. You'll find the dev packages in the repos.

---

