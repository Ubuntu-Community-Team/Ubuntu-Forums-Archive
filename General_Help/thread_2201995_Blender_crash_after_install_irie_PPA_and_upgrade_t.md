---
title: "Blender crash after install irie PPA and upgrade to 2.69 version."
date: 2014-01-26
forum: General Help
---

### Post by Portaro on 2014-01-26
Blender dont start and this is the result off command ->
$blender

> connect failed: No such file or directory
Read new prefs: /home/joao/.config/blender/2.69/config/userpref.blend
archimesh: added to phytonpath
archimesh: Imported multifiles
blender: swrast/s_span.c:1327: _swrast_write_rgba_span: Assertion `colorType == 0x1401 || colorType == 0x1406' failed.
Abortado (core dumped)


if I try command, that I need use to start the old version 2.62 ->

> $ LIBGL_ALWAYS_SOFTWARE=1 blender
connect failed: No such file or directory
Read new prefs: /home/joao/.config/blender/2.69/config/userpref.blend
Writing: /tmp/blender.crash.txt
Falha de segmentação (core dumped)

There is the file crash on /tmp/blender.txt -
> # Blender 2.69 (sub 10), Commit date: 2014-01-23 03:58, Hash 3b71cab

# backtrace
/usr/lib/blender/blender() [0x8787873]
[0x138400]
/usr/lib/i386-linux-gnu/libLLVM-3.0.so.1(_ZN4llvm3ARM8SPRClassC1Ev+0x15) [0xad65f9d5]
/usr/lib/i386-linux-gnu/libLLVM-3.0.so.1(+0x25ca48) [0xad604a48]
/lib/ld-linux.so.2(+0xeeab) [0xbcdeab]
/lib/ld-linux.so.2(+0xef94) [0xbcdf94]
/lib/ld-linux.so.2(+0x12fa6) [0xbd1fa6]
/lib/ld-linux.so.2(+0xeccf) [0xbcdccf]
/lib/ld-linux.so.2(+0x127f4) [0xbd17f4]
/lib/i386-linux-gnu/libdl.so.2(+0xbe9) [0x77ebe9]
/lib/ld-linux.so.2(+0xeccf) [0xbcdccf]
/lib/i386-linux-gnu/libdl.so.2(+0x133a) [0x77f33a]
/lib/i386-linux-gnu/libdl.so.2(dlopen+0x47) [0x77ec97]
/usr/lib/i386-linux-gnu/mesa/libGL.so.1(+0x3cbf0) [0xdc3bf0]
/usr/lib/i386-linux-gnu/mesa/libGL.so.1(+0x3c1ff) [0xdc31ff]
/usr/lib/i386-linux-gnu/mesa/libGL.so.1(+0x1a3e8) [0xda13e8]
/usr/lib/i386-linux-gnu/mesa/libGL.so.1(glXQueryVersion+0x2e) [0xd9ccee]
/usr/lib/blender/blender(_ZN15GHOST_WindowX11C1EP15GHOST_SystemX11P9_XDisplayRK10STR_Stringiijj18GHOST_TWindowStatei25GHOST_TDrawingContextTypebbt+0x11c) [0x8f84d7c]
/usr/lib/blender/blender(_ZN15GHOST_SystemX1112createWindowERK10STR_Stringiijj18GHOST_TWindowState25GHOST_TDrawingContextTypebbti+0xd7) [0x8f7f507]
/usr/lib/blender/blender(GHOST_CreateWindow+0xb6) [0x8f7cfe6]
/usr/lib/blender/blender(wm_window_add_ghostwindows+0x205) [0x87a7e35]
/usr/lib/blender/blender(WM_check+0x50) [0x8788b50]
/usr/lib/blender/blender(wm_homefile_read+0x174) [0x8792fc4]
/usr/lib/blender/blender(WM_init+0xda) [0x879506a]
/usr/lib/blender/blender(main+0xfba) [0x874575a]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3) [0x4a5e4d3]
/usr/lib/blender/blender() [0x8785e29]

What can I do?

---

### Post by Frank_Harland on 2014-02-06
Here same problem! Desperately trying to get it to work.
Cheers, Frank.

---

### Post by sandyd on 2014-02-06
sounds like [https://bugs.freedesktop.org/show_bug.cgi?id=47375](https://bugs.freedesktop.org/show_bug.cgi?id=47375)

what version of ubuntu are you running

---

### Post by Portaro on 2014-02-06
I use 12.04. THanks for your answer

---

### Post by sandyd on 2014-02-08
> **Portaro said:**
> I use 12.04. THanks for your answer

Try an upgrade to 13.10 or try using [LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") to upgrade your graphics stack

---

