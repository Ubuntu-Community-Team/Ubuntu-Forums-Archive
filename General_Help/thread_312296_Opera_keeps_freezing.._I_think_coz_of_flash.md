---
title: "Opera keeps freezing.. I think coz of flash"
date: 2006-12-04
forum: General Help
---

### Post by jaywhy13 on 2006-12-04
The plugin it is referring to is flash. I'm running Kubuntu 6.1 and I have the Adobe Flash Player 9.0 installed. Does gtk have something to do with gnome though? It is possible that I need to download some gnome stuff? this whole gtk_init thingy

```
opera: Plug-in 21039 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.

(process:21044): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:21044): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);
The program '<unknown>' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 13916 error_code 3 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
opera: Plug-in 21044 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.

(process:21072): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:21072): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);
      
```

---

### Post by michaelp on 2006-12-04
From [http://labs.adobe.com/technologies/flashplayer9/](http://labs.adobe.com/technologies/flashplayer9/) :

"The plugin does not currently work in Opera browsers. We are working with Opera on this issue."

---

### Post by jaywhy13 on 2006-12-05
> **michaelp said:**
> From [http://labs.adobe.com/technologies/flashplayer9/](http://labs.adobe.com/technologies/flashplayer9/) :

"The plugin does not currently work in Opera browsers. We are working with Opera on this issue."

Funny enough, it used 2 work nicely... especially when I visit youtube but all of a sudden it stops working.... mus b seein it's period or summin... al wait n c and re-install the drivers again and see wot happens...

I think I may hav updated opera recently 2, mayb that complicated the issue even further

---

### Post by melancholeric on 2006-12-05
That bug was discussed at opera forums aswell. At the moment there's no fix. Other than not using flash in opera. Which is why I have to use firefox for youtube and such.

---

### Post by michaelp on 2006-12-05
There's a fix in the mid-weekly build (build 507 ):
[http://my.opera.com/desktopteam/blog/2006/12/05/phishing-unix-and-plug-ins](http://my.opera.com/desktopteam/blog/2006/12/05/phishing-unix-and-plug-ins)

"Fixes to Opera freezing with Flash 9 on Linux."

---

