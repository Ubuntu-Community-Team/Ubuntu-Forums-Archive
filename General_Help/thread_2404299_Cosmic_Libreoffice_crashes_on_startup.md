---
title: "Cosmic: Libreoffice crashes on startup"
date: 2018-10-22
forum: General Help
---

### Post by amano on 2018-10-22
Does somebody else experience this crash? I didn't experience it before during the cosmic development cycle.

```
amano@amano-desktop:~$ libreoffice --norestore
Application Error

Fatal exception: Signal 6
Stack:
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x3cfb3)[0x7f0a82c03fb3]
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x3d1c3)[0x7f0a82c041c3]
/lib/x86_64-linux-gnu/libc.so.6(+0x41100)[0x7f0a829fe100]
/lib/x86_64-linux-gnu/libc.so.6(gsignal+0xc7)[0x7f0a829fe077]
/lib/x86_64-linux-gnu/libc.so.6(abort+0x121)[0x7f0a829df535]
/usr/lib/libreoffice/program/libmergedlo.so(+0x11ee372)[0x7f0a83e12372]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN11Application5AbortERKN3rtl8OUStringE+0x90)[0x7f0a85a5cfe0]
/usr/lib/libreoffice/program/libmergedlo.so(+0x1efdc57)[0x7f0a84b21c57]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2e3e59b)[0x7f0a85a6259b]
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x17202)[0x7f0a82bde202]
/usr/lib/libreoffice/program/libuno_sal.so.3(+0x3d08f)[0x7f0a82c0408f]
/lib/x86_64-linux-gnu/libc.so.6(+0x41100)[0x7f0a829fe100]
/lib/x86_64-linux-gnu/libc.so.6(+0xad116)[0x7f0a82a6a116]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(g_dbus_node_info_new_for_xml+0x124)[0x7f0a817c55a4]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2eb899f)[0x7f0a85adc99f]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0xc9996)[0x7f0a817ba996]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0xc9ba8)[0x7f0a817baba8]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x8f203)[0x7f0a81780203]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x8fad6)[0x7f0a81780ad6]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0xc1812)[0x7f0a817b2812]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x8f203)[0x7f0a81780203]
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0(+0x8f239)[0x7f0a81780239]
/usr/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x158)[0x7f0a815cdae8]
/usr/lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x4ded8)[0x7f0a815cded8]
/usr/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_iteration+0x2c)[0x7f0a815cdf6c]
/usr/lib/libreoffice/program/libvclplug_gtk3lo.so(+0x89973)[0x7f0a769a8973]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN11Application5YieldEv+0x2e)[0x7f0a85a5d4be]
/usr/lib/libreoffice/program/libmergedlo.so(_ZN11Application7ExecuteEv+0x45)[0x7f0a85a5ec35]
/usr/lib/libreoffice/program/libmergedlo.so(+0x1f035b6)[0x7f0a84b275b6]
/usr/lib/libreoffice/program/libmergedlo.so(+0x2e3fd26)[0x7f0a85a63d26]
/usr/lib/libreoffice/program/libmergedlo.so(_Z6SVMainv+0x30)[0x7f0a85a63e20]
/usr/lib/libreoffice/program/libmergedlo.so(soffice_main+0x91)[0x7f0a84b43c61]
/usr/lib/libreoffice/program/soffice.bin(+0x107b)[0x55a4c0b8e07b]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xeb)[0x7f0a829e109b]
/usr/lib/libreoffice/program/soffice.bin(+0x10ba)[0x55a4c0b8e0ba]

```

I installed Nautilus 3.30 and the tracker update from the GNOME staging PPA, but i can't see that those are really related? I wiped Libreoffice and re-installed from scratch, but no dice :(

---

### Post by dino99 on 2018-10-22
Answered into recent nautilus thread on dev subforum. Does not believe about nautilus/libreoffice relationship.

You might want checking for orphans / old settings; that can build conflict
Use gtkorphan & bleachbit (as root, carefully select settings)

---

