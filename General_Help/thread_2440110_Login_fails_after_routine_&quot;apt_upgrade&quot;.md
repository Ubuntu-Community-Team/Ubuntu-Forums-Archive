---
title: "Login fails after routine &quot;apt upgrade&quot;"
date: 2020-04-06
forum: General Help
---

### Post by Adrian_Ho on 2020-04-06
Hi!

I just restarted my Xubuntu Eoan laptop after doing an `apt upgrade`, but when I tried to login as usual from the GUI console, the login prompt disappeared for a couple of seconds, then came right back.

So I ssh'd in from another laptop, and checked my .xsession-errors log. To my horror, I found this:

```

Xsession: X session started for aho at Mon Apr  6 12:20:21 +08 2020
dbus-update-activation-environment: setting DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/501/bus
dbus-update-activation-environment: setting DISPLAY=:0
dbus-update-activation-environment: setting XAUTHORITY=/home/aho/.Xauthority
localuser:aho being added to access control list
dbus-update-activation-environment: setting SHELL=/bin/bash
...
/usr/bin/startxfce4: X server already running on display :0
xfce4-session: symbol lookup error: /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0: undefined symbol: hb_glib_script_from_script

```

I've tried to login with all the other desktop environments available on the login screen:

[LIST]
[*]Xfce Session: failed, same error
[*]Openbox: failed, same error
[*]LxQt desktop: goes black for almost 30 seconds, then gives me a desktop without a panel (.xsession-errors shows a handful of process all dying with exactly the same "undefined symbol" error)
[*]Lubuntu: goes black for almost 30 seconds, then gives me a desktop with a panel, but without a window manager (.xsession-errors shows the same errors as for LxQt desktop)
[/LIST]

I've tried `apt reinstall libpangoft2-1-0`, in case there was a library corruption, but that didn't seem to fix anything. Rebooting again didn't help either.

Short of a complete reinstall, is there a known fix for this? Thanks much!

---

### Post by lvm on 2020-04-06
If you think the last upgrade is a culprit you may try rolling all or suspect packages back to previous versions. Upgraded packages are listed in /var/apt/history.log, it is also a good idea to check /var/apt/term.log for errors.

---

### Post by Adrian_Ho on 2020-04-06
Thanks for the pointers, lvm! It turned out to be a self-inflicted wound. I'd installed a terminal emulator called [https://sw.kovidgoyal.net/kitty/](https://sw.kovidgoyal.net/kitty/), which came packaged with a number of shared libraries that shadowed the system ones thanks to my LD_LIBRARY_PATH:

```

# ldd /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0
    linux-vdso.so.1 (0x00007fff589b9000)
    libpango-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0 (0x00007fcddc130000)
    libgobject-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007fcddc0d3000)
    libglib-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007fcddbfab000)
    libharfbuzz.so.0 => /graft/lib/libharfbuzz.so.0 (0x00007fcddbd17000)
    libfontconfig.so.1 => /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 (0x00007fcddbcd1000)
    libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007fcddbc16000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fcddba23000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fcddb8d4000)
    libthai.so.0 => /usr/lib/x86_64-linux-gnu/libthai.so.0 (0x00007fcddb8c9000)
    libfribidi.so.0 => /usr/lib/x86_64-linux-gnu/libfribidi.so.0 (0x00007fcddb8ac000)
    libffi.so.6 => /graft/lib/libffi.so.6 (0x00007fcddb69e000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fcddb67b000)
    libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007fcddb605000)
    libexpat.so.1 => /graft/lib/libexpat.so.1 (0x00007fcddb3d0000)
    libuuid.so.1 => /lib/x86_64-linux-gnu/libuuid.so.1 (0x00007fcddb3c7000)
    libpng16.so.16 => /graft/lib/libpng16.so.16 (0x00007fcddb184000)
    libz.so.1 => /graft/lib/libz.so.1 (0x00007fcddaf66000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fcddc1b8000)
    libdatrie.so.1 => /usr/lib/x86_64-linux-gnu/libdatrie.so.1 (0x00007fcddaf5c000)

```

Fixing LD_LIBRARY_PATH to move /graft/lib behind the system library directories solved all my issues for now.

---

