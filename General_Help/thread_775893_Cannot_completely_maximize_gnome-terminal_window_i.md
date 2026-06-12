---
title: "Cannot completely maximize gnome-terminal window in fluxbox"
date: 2008-04-30
forum: General Help
---

### Post by leeyee on 2008-04-30
Hey guys, I got a tiny, but quite strange problem in fluxbox. From yesterday on, gnome-terminal window in fluxbox cannot be completely maximized. As shown in attachment.

In screenshot, you can see that, at the bottom and right side of the MAXIMIZED window, there still is a narrow blank. But other applications matches screen well. I've tried drag the border of it, but didn't work.

Besides, it's also from yesterday on, I am not sure if there is relations between them&#65292; gnome-settings-daemon which i set to run at startup of fluxbox would crash as the following description:
> 1, Open gnome-terminal;
2, Close gnome-terminal;
3, Open Thunar
then gnome-settings-daemon would close, and give a error info in .xsession-error about something "BadMatch". However, if i don't open gnome-terminal, just open Thunar, gnome-settings-daemon would keep running. Or I open gnome-terminal but not close it later, GSD would still keep running.

Can you guys help me find a workaround with this? Thanks a lot!

---

### Post by leeyee on 2008-05-01
Hi, 
I reproduced gnome-settings-daemon crashed, here is the output in xsession-errors about that:
```
The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 4087 error_code 8 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[1209620881,000,xklavier.c:xkl_engine_start_listen/] 	The backend does not require manual layout management - but it is provided by the application

```

---

### Post by markjensen on 2008-05-01
I don't have "gnome-terminal" installed on my setup, but I can maximize xterm without a problem.   Is this specific to gnome-terminal, or do other apps like xterm do the same thing for you?

---

### Post by leeyee on 2008-05-02
Sorry for not mention that, I also tried xterm, it has the same problem. As you may know, gnome-terminal is just an emulator of XTerm.

---

### Post by kerry_s on 2008-05-02
i think thats a font limitation to preserve columns, i get the same thing in rxvt on jwm. i can manually resize it, but if i just use the window bar button to maximize it doesn't go full to the edges.

---

### Post by p_quarles on 2008-05-02
> **kerry_s said:**
> i think thats a font limitation to preserve columns, i get the same thing in rxvt on jwm. i can manually resize it, but if i just use the window bar button to maximize it doesn't go full to the edges.
+1. I've never tried before, but I get the same thing with Sakura (a Gtk- and libvte-based terminal emulator, just like Gnome-term) in Fluxbox. Perhaps this is a limitation in the interactions between simple window managers and terminal emulators?

---

