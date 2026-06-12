---
title: "Can't start Chrome in Terminal"
date: 2015-09-10
forum: General Help
---

### Post by XinyuHou on 2015-09-10
I compiled and installed cairo on my Ubuntu 14.04. After that when I tried to open Chrome in Terminal, it gave me this error.
"/opt/google/chrome/chrome: symbol lookup error: /usr/libx86_64-linux-gnu/libpangocairo-1.0.so.0: undefined symbol: cairo_ft_front_options_substitute"

But I can open Chrome from Applications.

Here is part of the result from ldd command

ldd /usr/libx86_64-linux-gnu/libpangocairo-1.0.so.0
libcairo.so.2 => /home/bob/wayland_install/lib/libcairo.so.2 (0x0000)

The reason I compiled and installed cairo was I needed it for compiling Wayland.

How do I get pass this error?

---

