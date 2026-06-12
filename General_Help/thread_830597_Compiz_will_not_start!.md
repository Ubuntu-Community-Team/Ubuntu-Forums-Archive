---
title: "Compiz will not start!"
date: 2008-06-16
forum: General Help
---

### Post by chrisruls00 on 2008-06-16
Compiz used to start for me, but when I updated to the latest git using the makefusion9 script, I get this message when typing compiz --replace

```
compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"

```

anyone know what this means?

---

### Post by chrisruls00 on 2008-06-16
I ran the compiz-check script and I got this:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   KDE
 Graphics chip:         nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: No path to Compiz found.

Would you like to know more? (Y/n) Y

 In case you did not compile Compiz manually, this will result in Compiz
 failing to run. The problem is presumably a result of you installing the
 proprietary fglrx driver manually or by script, which changed a certain
 config file to get itself on the whitelist.

```

---

### Post by Forlong on 2008-06-16
So... did you compile Compiz from source or not?


Edit: sorry, didn't read the very first line of the thread. I can't say anything about that script. You should ask the author about it.

---

