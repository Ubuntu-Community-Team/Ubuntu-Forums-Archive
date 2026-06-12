---
title: "X11 failing to start with USB keyboard"
date: 2007-01-24
forum: General Help
---

### Post by goflyapig on 2007-01-24
I recently bought a new USB keyboard to replace my old PS/2 one that had been working fine under Edgy.  I unplugged the old (PS/2) one, plugged in the USB one, and the new keyboard seemed to be working fine.

But then I rebooted, and X spits out some nasty error message at me.  However, the keyboard works fine in the console after X finishes yelling at me.  When I try switching back to my old keyboard and rebooting again, everything is fine and dandy again.

But, I don't see anything in Xorg.0.log about my keyboard... :confused:
This looks like the interesting part, though:

```
Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/X11R6/bin/X(main+0x6af) [0x806e93f]
3: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d0d8cc]
4: /usr/X11R6/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting
```

And here's a bit from xorg.conf:

```
Section "InputDevice"
    Identifier      "Generic Keyboard"
    Driver          "kbd"
    Option          "CoreKeyboard"
    Option          "XkbRules"      "xorg"
    Option          "XkbModel"      "pc105"
    Option          "XkbLayout"     "us"
    Option          "XkbOptions"    "lv3:ralt_switch"
EndSection
```

I tried going into my BIOS and turning on "USB legacy support" and "port 64/something emulation", but no luck.

Any ideas?

---

