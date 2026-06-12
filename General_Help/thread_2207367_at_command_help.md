---
title: "at command help"
date: 2014-02-23
forum: General Help
---

### Post by edandavi on 2014-02-23
hi,

i'm trying to run transmission-gtk (bittorent client) with the at command,
and the program isn't opening... 
i tried opening gedit and again no success
but if i echo some text to a file the command dose get executed at the assigned time
is it a problem to run graphical programs with at command?

i'm trying to do the following:

at 15:50
>transmission-gtk
>^D

thanks for your time :)

---

### Post by Lars Noodén on 2014-02-23
It's a graphical program but *at* won't know about which display to use so you have to point it to one.  You can do that by setting the DISPLAY variable and that can be done by prepending it to the same line that runs transmission-gtk

```

DISPLAY=:0.0 /usr/bin/transmission-gtk

```

Of course for that to work, *at* should be run as the same user as is running the display.

---

### Post by edandavi on 2014-02-23
finally worked 
thank you

---

