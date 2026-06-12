---
title: "Manual load of xorg.conf modules"
date: 2006-08-14
forum: General Help
---

### Post by earobinson on 2006-08-14
is there a way that I can manual load in the xorg.conf modules from the xorg.conf file.

for example I currently have ```
Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

``` and want to change it to ```
Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

``` (no load xgl) and then later load the xgl module from the command line. Is there a way to do this?

Thanks

---

### Post by earobinson on 2006-08-14
> 
My hunch is that it'll be too late for Xorg to do that after it's booted, but I guess I could be wrong.  Why do you want to do this?


Well Im using xdmx and making a video wall the only problem is when I start the video wall and then run a program with wine on the video wall.

Only problem is when I run it I get this error
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  110
  Current serial number in output stream:  110

```

and it works not on the video wall so I assume I need to lode in the glx module

edit01: Its never to late with linux is it ? :(
edit02: Any idea on where I can go to for help with this problem?

---

