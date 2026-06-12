---
title: "opengl bug"
date: 2007-04-09
forum: General Help
---

### Post by lennartack on 2007-04-09
Since some time ago, everytime I try to open a program that uses opengl, like beryl or a game, the screen becomes black and nothing, even the tty, works. A few seconds later X restarts and the the gnome login screen appears on the screen. Even when I do glxinfo this happens. Please help me...

---

### Post by lennartack on 2007-04-09
Oops, I didn't saw this thread: [http://ubuntuforums.org/showthread.php?t=403164&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=403164&highlight=nvidia)
I tried the fix listed there but, though X doesn't restart anymore, it still doesn't work. When I try to start beryl I get this:
[quote=beryl-manager]Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Xlib:  extension "GLX" missing on display ":0.0".
Root visual is not a GL visual
Not initializing the Gtk-Qt theme engine
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QImage::convertDepth: Image is a null image
QImage::convertDepth: Image is a null image
QImage::convertDepth: Image is a null image
QImage::convertDepth: Image is a null image
QImage::convertDepth: Image is a null image
QImage::convertDepth: Image is a null image
[/quote]

---

