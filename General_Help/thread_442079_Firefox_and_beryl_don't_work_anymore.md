---
title: "Firefox and beryl don't work anymore"
date: 2007-05-13
forum: General Help
---

### Post by persoontje on 2007-05-13
Hey,

Suddenly firefox and bery-manager (and I think other gtk programs) stopped working. I think it happened when I installed the flash plugin

They crash with this error
```

firefox
QPainter::begin: Cannot paint null pixmap
QPainter::setPen: Will be reset by begin()
QPainter::setFont: Will be reset by begin()
QPainter::end: Missing begin() or begin() failed
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 438 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

```

didier@ice-ubuntu:~$ beryl-manager
didier@ice-ubuntu:~$ QPainter::begin: Cannot paint null pixmap
QPainter::setPen: Will be reset by begin()
QPainter::setFont: Will be reset by begin()
QPainter::end: Missing begin() or begin() failed
The program 'beryl-manager' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 447 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I already tried the  export XLIB_SKIP_ARGB_VISUALS=1 workaround, but that doesn't make any difference. Uninstalling the flash-plugin doesn't solve the problem either.

I'm using kubuntu feisty (and nvidia binary drivers + beryl for desktop effects)

---

### Post by pokemon_jojo on 2007-05-15
I have the same problem with firefox and beryl !!!!

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QPainter::begin: Cannot paint null pixmap
QPainter::setPen: Will be reset by begin()
QPainter::setFont: Will be reset by begin()
QPainter::end: Missing begin() or begin() failed
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 466 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

i'm using kubuntu feisty.

---

### Post by marseillai on 2007-05-15
you should reinstall gtk-qt-engine it should work after.

---

### Post by zackpete on 2007-10-09
im getting the same errors... used apt-get to remove and reinstall gtk-qt-engine, and it doesnt make a difference. is there another way to reinstall it?
edit: domino was causing the problem, changed the gtk style from Qt to raleigh in kcontrol

---

### Post by lajevardi on 2008-04-02
Same problem here.

---

