---
title: "Ubuntu, Fedora Core and old programs"
date: 2004-11-14
forum: General Help
---

### Post by frspin on 2004-11-14
I have an old program using libc5 and running on RedHat9.
I have defined LD_LIBRARY_PATH pointing to a compatibility directory with required old libraries (libc.so.5, libX11.so.6.1 and so) and copied ld-linux.so.1.9.5 and libdl.so.1.9.5 to /lib for loader compatibility.

Now I am testing current Ubuntu, wich use libc-2.3.2 and XFree86, and Fedora Core 3, wich use libc-2.3.3 and Xorg.

In Ubuntu I get my old program running correctly
In FC3 (and also in FC2) I get a "Xlib unespected async reply" and a signal 11 (segvec?) and my program abort.

Is this a incompatibility in libc or in Xorg libraries ? 
I have no possibility to re-link my program (a stripped binary-only program).

Regards
Franco

---

### Post by TravisNewman on 2004-11-14
[QUOTE=frspin]I have an old program using libc5 and running on RedHat9.
I have defined LD_LIBRARY_PATH pointing to a compatibility directory with required old libraries (libc.so.5, libX11.so.6.1 and so) and copied ld-linux.so.1.9.5 and libdl.so.1.9.5 to /lib for loader compatibility.

Now I am testing current Ubuntu, wich use libc-2.3.2 and XFree86, and Fedora Core 3, wich use libc-2.3.3 and Xorg.

In Ubuntu I get my old program running correctly
In FC3 (and also in FC2) I get a "Xlib unespected async reply" and a signal 11 (segvec?) and my program abort.

Is this a incompatibility in libc or in Xorg libraries ? 
I have no possibility to re-link my program (a stripped binary-only program).

Regards
Franco[/QUOTE]
 Let me see if I follow... it's an old program that you had running in RH9, and it WORKS in Ubuntu, but NOT in Fedora, right?

Did you have to do anything in Ubuntu to get it to work?

---

### Post by frspin on 2004-11-14
[QUOTE=panickedthumb]Let me see if I follow... it's an old program that you had running in RH9, and it WORKS in Ubuntu, but NOT in Fedora, right?

Did you have to do anything in Ubuntu to get it to work?[/QUOTE]

Yes, it is correct.

For getting it work in Ubuntu I only made same work that I have made on RedHat 9 - Setting LD_LIBRARY_PATH and putting in /lib 2 files required for loader

Regards

Franco Spinelli

---

