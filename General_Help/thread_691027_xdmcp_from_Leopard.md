---
title: "xdmcp from Leopard"
date: 2008-02-08
forum: General Help
---

### Post by rapchee on 2008-02-08
there is a feisty machine which i use with xdmcp on tiger with minor problems, but now there is a leopard, which won't work.
I use the command ```
/usr/X11R6/bin/X -query x.x.x.x
``` but on leopard after the login window appears, i cant type in it, instead it puts the text in the terminal. 
I get this in the terminal:

```
X11.app starting:
Xquartz server based on X.org Release 7.2, built on 2007924
Check-in failed: Permission denied
_XSERVTransmkdir: ERROR: euid != 0,directory /tmp/.X11-unix will not be created. 
```

Based on my googling i've tried '/usr/X11/X11.app/Contents/MacOS/X11 -query x.X.X.x' as well, and i could type the password in but after it quits. Terminal output:

```
X11.app starting:
Xquartz server based on X.org Release 7.2, built on 2007924
Check-in failed: Permission denied
meta mod is 4
Quitting Xquartz...
```

any suggestions appreciated

---

