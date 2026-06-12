---
title: "HELP!! X won't start!"
date: 2008-02-15
forum: General Help
---

### Post by MEGAMANULTIMATE on 2008-02-15
Okay, so this is weird.

I chose to restart my computer just last night...and now the graphical interface won't start. It just brings me back to some sort of terminal interface. Even when I try to use recovery nothing works. A white screen came up and diagnosed the problem as this:

/usr/X11R6/bin/X:error while loading shared libraries:

usr/lib/libXfont.so.1:invalid ELF loader

What the hell has happened and is there any chance of fixing it?
Sorry for the outburst. Please help me.

---

### Post by neurostu on 2008-02-15
when you boot try logging in and then try:
```
 startx 
```

---

### Post by jan quark on 2008-02-15
go into recovery mode and run this
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

---

