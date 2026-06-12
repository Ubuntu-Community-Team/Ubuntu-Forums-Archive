---
title: "Flash and edgy 64-bit"
date: 2006-11-03
forum: General Help
---

### Post by KAding on 2006-11-03
Hello,

I'm having some issues getting Flash to work on edgy 64-bit. I installed firefox32 without any problems. It is working great, so is the java plugin. 

But Flash will always crash the browser. It doesn't matter which version I use, 7 or the beta 9. I removed any trace of firefox from the system and completely reinstalled it. I made sure there were no double libflash.so files anywhere.

If I run firefox32 in a console and go to any website containing flash I just get the following error:
```

Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 86 error_code 8 request_code 146 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I really have no idea what could be wrong :(. I must say I haven't been able to get the stand-alone Flash 9 player to play anything either. It does not crash, but simply shows nothing (animation area simply blank) :(.

Internet without Flash is kinda difficult in this day and age. Anyone have any ideas?

---

### Post by KAding on 2006-11-03
Ah, I just found a bug report for edgy on this issue.

I'm checking that out now. Perhaps I posted this too soon :).

---

### Post by KAding on 2006-11-03
Ok, for those that have the same problem. Adding 'export XLIB_SKIP_ARGB_VISUALS=1' to /usr/bin/firefox (for 32-bit) or /usr/local/firefox32/firefox (for 64-bit) fixed it for me!

---

