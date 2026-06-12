---
title: "Firefox coredump at startup"
date: 2007-02-23
forum: General Help
---

### Post by jolig on 2007-02-23
Hi, I am experiencing a direct Firefox core dump when I try to launch it.
[I]
I am running :[/I]
Linux iCore2Duo 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux

[I]
file on firefox-bin[/I]
/usr/lib/firefox/firefox-bin: ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), for GNU/Linux 2.6.0, stripped

*ldd on firefox-bin*
libmozjs.so => not found
libxpcom.so => not found
libxpcom_core.so => not found
libplc4.so => /usr/lib/libplc4.so (0x00002b5d739c1000)
libnspr4.so => /usr/lib/libnspr4.so (0x00002b5d73ac7000)
libpthread.so.0 => /lib/libpthread.so.0 (0x00002b5d73c01000)
libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00002b5d73d17000)
libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00002b5d741ab000)
libX11.so.6 => /usr/lib/libX11.so.6 (0x00002b5d74343000)
libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00002b5d74521000)
libc.so.6 => /lib/libc.so.6 (0x00002b5d74722000)
libdl.so.2 => /lib/libdl.so.2 (0x00002b5d74962000)
/lib64/ld-linux-x86-64.so.2 (0x00002b5d738a4000)
libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00002b5d74a66000)
libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00002b5d74b7f000)
libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00002b5d74c88000)
libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00002b5d74dc8000)
libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00002b5d74ee9000)
libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00002b5d7502a000)
libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x00002b5d7512d000)
libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00002b5d752cc000)
libm.so.6 => /lib/libm.so.6 (0x00002b5d75435000)
libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00002b5d755b6000)
libXext.so.6 => /usr/lib/libXext.so.6 (0x00002b5d756f6000)
libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00002b5d75807000)
libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00002b5d75910000)
libXi.so.6 => /usr/lib/libXi.so.6 (0x00002b5d75a13000)
libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00002b5d75b1b000)
libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00002b5d75c1e000)
libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00002b5d75d29000)
libXau.so.6 => /usr/lib/libXau.so.6 (0x00002b5d75e2e000)
libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002b5d75f31000)
libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00002b5d76037000)
libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00002b5d76144000)
libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00002b5d76272000)
libz.so.1 => /usr/lib/libz.so.1 (0x00002b5d763ec000)
librt.so.1 => /lib/librt.so.1 (0x00002b5d76502000)
libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00002b5d7660c000)
libexpat.so.1 => /usr/lib/libexpat.so.1 (0x00002b5d76730000)


I tryed to trace using firefox-dbg, it seems the break is comming from libcairo...
Any Idea ?

Thanks !

---

