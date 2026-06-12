---
title: "Xlib error &quot;extension &quot;GLX&quot; missing on display&quot;"
date: 2014-09-01
forum: General Help
---

### Post by maciej9 on 2014-09-01
I have a remote build-machine with Jenkins and I'm trying to run GUI application. In Jenkins I installed Xvnc plugin, which uses TightVNC Server, but each build has failed.
Earlier, there was a problem with loading driver swrast (by libGL), currently  in the log there are this lines:

```
Xlib:  extension "RANDR" missing on display ":51".
(...)
Xlib:  extension "GLX" missing on display ":51".
Terminating xvnc.
$ vncserver -kill :51
Killing Xtightvnc process ID 22513
```

When I changed system to use Xvnc4server instead of tightvncserver, the output is:

```
[Warning] QXcbConnection: Failed to initialize XRandr
[Warning] Qt: XKEYBOARD extension not present on the X server. 
(...)
[Warning] Unrecognized OpenGL version
[Warning] Unrecognized OpenGL version
Terminating xvnc.
$ vncserver -kill :47
Killing Xvnc4 process ID 26522
```

Remote desktop is Ubuntu 14.04 running over VirtualBox, so I installed VBoxAddons but it didn't resolve the problem. Below I'm putting some logs, maybe helpful for you. 

```
$ cat /var/log/Xorg.0.log | grep GL -is
[266219.686] (II) LoadModule: "glx"
[266219.686] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[266219.687] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[266219.687] Loading extension GLX
[266219.687] (==) Assigned the driver to the xf86ConfigLayout

$ lsmod | grep box
vboxsf                 43786  0 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
vboxvideo              12658  0 
vboxguest             248441  8 vboxsf
drm                   302817  1 vboxvideo

$ lspci | grep VGA
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter

$ glxinfo 
Error: unable to open display 
```

Any ideas what should I do?

---

### Post by maciej9 on 2014-09-04
Does anybody can help?

---

