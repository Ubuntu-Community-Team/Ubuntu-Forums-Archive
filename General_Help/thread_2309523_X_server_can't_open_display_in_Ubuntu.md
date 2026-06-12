---
title: "X server can't open display in Ubuntu"
date: 2016-01-11
forum: General Help
---

### Post by andrew277 on 2016-01-11
[COLOR=#222426][FONT=Helvetica Neue]I'm not very familiar with the X server display but I'm trying to use a debugger program called DDD and it needs X server to open up to use it.[/FONT][/COLOR]
[COLOR=#222426][FONT=Helvetica Neue]I get this error when I try to run ddd:[/FONT][/COLOR]
```
Error: Can't open display: XX.XX.X.XX:0.0

```[COLOR=#222426][FONT=Helvetica Neue]I set my DISPLAY variable to my IP address but it still won't open.[/FONT][/COLOR]
[COLOR=#222426][FONT=Helvetica Neue]When I run startx as root, I get this message:[/FONT][/COLOR]
```
Current version of pixman: 0.30.2
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Mon Jan 11 13:36:54 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension Present
Initializing built-in extension DRI3
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
xinit: connection to X server lost

waiting for X server to shut down (EE) Server terminated successfully (0). Closing log file.
```

[COLOR=#222426][FONT=Helvetica Neue]I've read some things about how it could possibly be a issue with modules-load.d but I don't even have that directory under my /etc/ folder.
[/FONT][/COLOR]
[COLOR=#222426][FONT=Helvetica Neue]I installed xinit as well but that didn't solve anything.
[/FONT][/COLOR]
[COLOR=#222426][FONT=Helvetica Neue]Any suggestions?[/FONT][/COLOR]
[COLOR=#222426][FONT=Helvetica Neue]Thanks[/FONT][/COLOR]

---

