---
title: "compiz 'unable to open display' fix"
date: 2007-09-30
forum: General Help
---

### Post by Sqwishy on 2007-09-30
If, when running something like compiz, and you get this nasty error...
```
xset:  unable to open display ""
xdpyinfo:  unable to open display "".
xvinfo:  Unable to open display 
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```
and if you run 
```
glxgears
``` you get *Error: couldn't open display (null)* and 
```
 env | grep DISPLAY
``` doesn't output anything


if that stuff happens to you, then you gotta run
```
sudo nano /etc/environment
```
and at the end of the file (line 3 or something) put 
```
DISPLAY=:0.0
```
then reboot your compy

---

