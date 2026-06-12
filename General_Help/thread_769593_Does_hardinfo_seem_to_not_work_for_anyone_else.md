---
title: "Does hardinfo seem to not work for anyone else?"
date: 2008-04-26
forum: General Help
---

### Post by SZF2001 on 2008-04-26
I'm not sure why, but whenever I use hardinfo it can only handle telling me one bit of info at a time then it freezes. As in, I click on something like "general info", look over it, then click on "sound" and it just quits for no reason. Here's the terminal output:

[b]~$ hardinfo
*** glibc detected *** hardinfo: munmap_chunk(): invalid pointer: 0x082da210 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb74e692b]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb782e961]
/usr/lib/libglib-2.0.so.0[0xb781a1a7]
/usr/lib/libglib-2.0.so.0[0xb781a3b0]
hardinfo[0x8050eaf]
hardinfo[0x8051fb8]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb78d5c09]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb78c8772]
/usr/lib/libgobject-2.0.so.0[0xb78d9323]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb78da847]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb78daa09]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_tree_selection_internal_select_node+0x92)[0xb7e2cde2]
/usr/lib/libgtk-x11-2.0.so.0[0xb7e45363]
/usr/lib/libgtk-x11-2.0.so.0[0xb7e4c65b]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7d431de]
/usr/lib/libgobject-2.0.so.0[0xb78c6f89]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb78c8772]
/usr/lib/libgobject-2.0.so.0[0xb78d9973]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb78da60f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb78daa09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7e61498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0x14f)[0xb7d3c36f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x307)[0xb7d3d587]
/usr/lib/libgdk-x11-2.0.so.0[0xb7ba8b9a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb782711c]
/usr/lib/libglib-2.0.so.0[0xb782a55f]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb782a909]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7d3d9e4]
hardinfo(main+0x119)[0x804f989]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb748f050]
hardinfo[0x804f7e1]
======= Memory map: ========
08048000-08063000 r-xp 00000000 08:01 1183779    /usr/bin/hardinfo
08063000-08064000 rw-p 0001a000 08:01 1183779    /usr/bin/hardinfo
08064000-08327000 rw-p 08064000 00:00 0          [heap]
b64d5000-b64df000 r-xp 00000000 08:01 868421     /lib/libgcc_s.so.1
b64df000-b64e0000 rw-p 0000a000 08:01 868421     /lib/libgcc_s.so.1
b64e0000-b64ef000 r-xp 00000000 08:01 902106     /lib/tls/i686/cmov/libresolv-2.6.1.so
b64ef000-b64f1000 rw-p 0000f000 08:01 902106     /lib/tls/i686/cmov/libresolv-2.6.1.so
b64f1000-b64f3000 rw-p b64f1000 00:00 0 
b64f3000-b64f4000 r-xp 00000000 08:01 868428     /lib/libkeyutils-1.2.so
b64f4000-b64f5000 rw-p 00001000 08:01 868428     /lib/libkeyutils-1.2.so
b64f5000-b64fc000 r-xp 00000000 08:01 1180574    /usr/lib/libkrb5support.so.0.1
b64fc000-b64fd000 rw-p 00006000 08:01 1180574    /usr/lib/libkrb5support.so.0.1
b64fd000-b6502000 r-xp 00000000 08:01 902093     /lib/tls/i686/cmov/libcrypt-2.6.1.so
b6502000-b6504000 rw-p 00004000 08:01 902093     /lib/tls/i686/cmov/libcrypt-2.6.1.so
b6504000-b652b000 rw-p b6504000 00:00 0 
b652b000-b652d000 r-xp 00000000 08:01 868386     /lib/libcom_err.so.2.1
b652d000-b652e000 rw-p 00001000 08:01 868386     /lib/libcom_err.so.2.1
b652e000-b6552000 r-xp 00000000 08:01 1180571    /usr/lib/libk5crypto.so.3.1
b6552000-b6553000 rw-p 00024000 08:01 1180571    /usr/lib/libk5crypto.so.3.1
b6553000-b65d9000 r-xp 00000000 08:01 1180573    /usr/lib/libkrb5.so.3.3
b65d9000-b65db000 rw-p 00086000 08:01 1180573    /usr/lib/libkrb5.so.3.3
b65db000-b6603000 r-xp 00000000 08:01 1180558    /usr/lib/libgssapi_krb5.so.2.2
b6603000-b6604000 rw-p 00027000 08:01 1180558    /usr/lib/libgssapi_krb5.so.2.2
b6604000-b6637000 r-xp 00000000 08:01 1179757    /usr/lib/libcups.so.2
b6637000-b6639000 rw-p 00032000 08:01 1179757    /usr/lib/libcups.so.2
b6639000-b6699000 rw-s 00000000 00:09 7176222    /SYSV00000000 (deleted)
b6699000-b66a8000 r-xp 00000000 08:01 868490     /lib/libbz2.so.1.0.4
b66a8000-b66a9000 rw-p 0000f000 08:01 868490     /lib/libbz2.so.1.0.4
b66a9000-b66db000 r-xp 00000000 08:01 1181271    /usr/lib/libcroco-0.6.so.3.0.1
b66db000-b66de000 rw-p 00031000 08:01 1181271    /usr/lib/libcroco-0.6.so.3.0.1
b66de000-b670e000 r-xp 00000000 08:01 1181565    /usr/lib/libgsf-1.so.114.0.7
b670e000-b6711000 rw-p 0002f000 08:01 1181565    /usr/lib/libgsf-1.so.114.0.7
b6711000-b6712000 rw-p bAborted (core dumped)[/b]

---

### Post by rbmorse on 2008-04-26
Works fine here, although I don't like a lot of what it tells me. Are you running it with root permissions?

---

### Post by spadewarrior on 2008-04-26
It works for me now I'm in Hardy but always crashed for me in Gutsy whenever I clicked on a different menu. 

Looks like it's fixed in the upgrade:

[https://bugs.launchpad.net/ubuntu/gutsy/+source/hardinfo/+bug/175423](https://bugs.launchpad.net/ubuntu/gutsy/+source/hardinfo/+bug/175423)

---

### Post by SZF2001 on 2008-04-26
Hmm... I'm using Mint, but it's basically Gutsy with a bunch of restricted codecs installed by default.

Any way to upgrade Mint to Hardy standards?

---

### Post by spadewarrior on 2008-04-27
I'd suggest asking over at the Mint forums unless someone else here can help. 

Best of luck.

---

