---
title: "Has anyone been able to compile leafpad?"
date: 2004-12-02
forum: General Help
---

### Post by jeremymarx on 2004-12-02
I am trying to compile leafpad...  [http://www.gnomefiles.org/app.php?soft_id=365](http://www.gnomefiles.org/app.php?soft_id=365)
But I am getting GTK+ errors in the ./compile, and several pages of errors with make...
If any one can give sugggestions I would appreciate it!  Thanks.

-Jeremymarx

---

### Post by chambery on 2004-12-04
I'm a leafpad fan myself.  I did have some problems compiling new versions of leafpad, and while I can't remember exactly what the fix was, I think what I did was:

$ ./configure
[get errors from missing libs (or constants or whatever)]
traceback through the errors for the name of the missing lib
fetch missing packages from Synaptic (usually I was missing xxx-dev packages, e.g. libgtk2.0-dev)
**delete/re-extract the leafpad sources**
$ ./configure (etc.)

Deleting and re-extracting the build dir for leafpad was the key I think.  Rerunning ./configure on the same build dir with the newly installed dev packages in place didn't work.

Hope that helps,

Todd

---

