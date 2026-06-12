---
title: "Hardy Instability"
date: 2008-06-06
forum: General Help
---

### Post by darrenm on 2008-06-06
I don't understand what is going on with Ubuntu at the moment. I can't get anything to run stable.

I'm trying to run evolution connecting to an exchange and this happened: [https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/236080](https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/236080) 

Managed to get it to work again somehow and this happened : [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/237619](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/237619)

Now I'm trying capture some packets in wireshark, when I save the trace I get this:

```
*** glibc detected *** wireshark: free(): invalid pointer: 0x08e408a8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb5ca4a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb5ca84f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb5fa58b1]
/usr/lib/wireshark/libwireshark.so.0[0xb70147f4]
/usr/lib/wireshark/libwireshark.so.0[0xb69b6f59]
/usr/lib/libglib-2.0.so.0(g_slist_foreach+0x21)[0xb5fbbb11]
/usr/lib/wireshark/libwireshark.so.0(init_dissection+0x41)[0xb69b98b1]
wireshark(cf_open+0x43)[0x8076de3]
wireshark(cf_save+0x1e4)[0x80771b4]
wireshark[0x80be443]
wireshark(file_save_as_cmd+0x43c)[0x80be9bc]
/usr/lib/libgtk-x11-2.0.so.0[0xb631c86e]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x4f)[0xb6045a4f]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xb6038759]
/usr/lib/libgobject-2.0.so.0[0xb604cd1d]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c6)[0xb604e916]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb604ec59]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_activate+0x58)[0xb645e278]
/usr/lib/libgtk-x11-2.0.so.0(gtk_menu_shell_activate_item+0x182)[0xb6347bc2]
/usr/lib/libgtk-x11-2.0.so.0[0xb6349708]
/usr/lib/libgtk-x11-2.0.so.0[0xb6340914]
/usr/lib/libgtk-x11-2.0.so.0[0xb633a8d4]
/usr/lib/libgobject-2.0.so.0[0xb6037079]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xb6038759]
/usr/lib/libgobject-2.0.so.0[0xb604cea0]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x5fe)[0xb604e64e]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb604ec59]
/usr/lib/libgtk-x11-2.0.so.0[0xb6459667]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0xc1)[0xb6333b21]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x2b8)[0xb6334d88]
/usr/lib/libgdk-x11-2.0.so.0[0xb61ada9a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x178)[0xb5f9dbf8]
/usr/lib/libglib-2.0.so.0[0xb5fa0e5e]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1e7)[0xb5fa11e7]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb6335264]
wireshark(main+0xbc4)[0x808b854]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb5c4f450]
wireshark(register_all_protocols+0x5dd)[0x80666c1]
======= Memory map: ========
08048000-08184000 r-xp 00000000 08:03 84878154   /usr/bin/wireshark
08184000-08197000 rw-p 0013b000 08:03 84878154   /usr/bin/wireshark
08197000-092e0000 rw-p 08197000 00:00 0          [heap]
b1a00000-b1a21000 rw-p b1a00000 00:00 0 
b1a21000-b1b00000 ---p b1a21000 00:00 0 
b1b22000-b1b33000 r--s 00000000 08:03 50451336   /usr/share/mime/mime.cache
b1b33000-b1b67000 r-xp 00000000 08:03 134294516  /usr/lib/libdbus-1.so.3.4.0
b1b67000-b1b69000 rw-p 00033000 08:03 134294516  /usr/lib/libdbus-1.so.3.4.0
b1b69000-b1bc8000 r-xp 00000000 08:03 134294434  /usr/lib/libgio-2.0.so.0.0.0
b1bc8000-b1bca000 rw-p 0005e000 08:03 134294434  /usr/lib/libgio-2.0.so.0.0.0
b1bca000-b1bcb000 rw-p b1bca000 00:00 0 
b1bcb000-b1bcc000 ---p b1bcb000 00:00 0 
b1bcc000-b25c9000 rw-p b1bcc000 00:00 0 
b25c9000-b25ca000 ---p b25c9000 00:00 0 
b25ca000-b25cb000 rw-p b25ca000 00:00 0 
b25cb000-b25cc000 ---p b25cb000 00:00 0 
b25cc000-b2fc9000 rw-p b25cc000 00:00 0 
b2fc9000-b2fca000 ---p b2fc9000 00:00 0 
b2fca000-b2fcb000 rw-p b2fca000 00:00 0 
b2fcb000-b2fcc000 ---p b2fcb000 00:00 0 
b2fcc000-b39c9000 rw-p b2fcc000 00:00 0 
b39c9000-b39ca000 ---p b39c9000 00:00 0 
b39ca000-b39cb000 rw-p b39ca000 00:00 0 
b39cb000-b39cc000 ---p b39cb000 00:00 0 
b39cc000-b43c9000 rw-p b39cc000 00:00 0 
b43c9000-b43ca000 ---p b43c9000 00:00 0 
b43ca000-b4416000 r--p 00000000 08:03 201630070  /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b4416000-b4462000 rw-p b4759000 00:00 0 
b4470000-b448a000 r-xp 00000000 08:03 134471187  /usr/lib/libdbus-glib-1.so.2.1.0
b448a000-b448b000 rw-p 0001a000 08:03 134471187  /usr/lib/libdbus-glib-1.so.2.1.0
b4497000-b44a6000 r-xp 00000000 08:03 134294546  /usr/lib/libhal.so.1.0.0
b44a6000-b44a7000 rw-p 0000e000 08:03 134294546  /usr/lib/libhal.so.1.0.0
b44a7000-b4524000 r-xp 00000000 08:03 67914653   /usr/lib/wireshark/plugins/wimax.so
b4524000-b4540000 rw-p 0007c000 08:03 67914653   /usr/lib/wireshark/plugins/wimax.so
b4540000-b4548000 r-xp 00000000 08:03 67914651   /usr/lib/wireshark/plugins/v5ua.so
b4548000-b454b000 rw-p 00007000 08:03 67914651   /usr/lib/wireshark/plugins/v5ua.so
b454b000-b4560000 r-xp 00000000 08:03 67914649   /usr/lib/wireshark/plugins/unistim.so
b4560000-b4567000 rw-p 00014000 08:03 67914649   /usr/lib/wireshark/plugins/unistim.so
b4567000-b4572000 r-xp 00000000 08:03 67914647   /usr/lib/wireshark/plugins/tango.so
b4572000-b4573000 rw-p 0000a000 08:03 67914647   /usr/lib/wireshark/plugins/tango.so
b4573000-b4574000 r-xp 00000000 08:03 67914645   /usr/lib/wireshark/plugins/stats_tree.so
b4574000-b4575000 rw-p 00001000 08:03 67914645   /usr/lib/wireshark/plugins/stats_tree.so
b4575000-b457c000 r-xp 00000000 08:03 67914643   /usr/lib/wireshark/plugins/sbus.so
b457c000-b457e000 rw-p 00006000 08:03 67914643   /usr/lib/wireshark/plugins/sbus.so
b457e000-b4580000 r-xp 00000000 08:03 67914641   /usr/lib/wireshark/plugins/rudp.so
b4580000-b4581000 rw-p 00001000 08:03 67914641   /usr/lib/wireshark/plugins/rudp.so
b4581000-b4586000 r-xp 00000000 08:03 67914639   /usr/lib/wireshark/plugins/rtnet.so
b4586000-b4588000 rw-p 00004000 08:03 67914639   /usr/lib/wireshark/plugins/rtnet.so
b4588000-b4589000 r-xp 00000000 08:03 67914637   /usr/lib/wireshark/plugins/rlm.so
b4589000-b458a000 rw-p 00001000 08:03 67914637   /usr/lib/wireshark/plugins/rlm.so
b458a000-b45c4000 r-xp 00000000 08:03 67914635   /usr/lib/wireshark/plugins/profinet.so
b45c4000-b45d0000 rw-p 00039000 08:03 67914635   /usr/lib/wireshark/plugins/profinet.so
b45d0000-b4683000 r-xp 00000000 08:03 67914631   /usr/lib/wireshark/plugins/parlay.so
b4683000-b4685000 rw-p 000b3000 08:03 67914631   /usr/lib/wireshark/plugins/parlay.so
b4685000-b4689000 r-xp 00000000 08:03 67914629   /usr/lib/wireshark/plugins/opsi.so
b4689000-b468b000 rw-p 00003000 08:03 67914629   /usr/lib/wireshark/plugins/opsi.so
b468b000-b46ae000 r-xp 00000000 08:03 67914627   /usr/lib/wireshark/plugins/opcua.so
b46ae000-b46b5000 rw-p 00023000 08:03 67914627   /usr/lib/wireshark/plugins/opcua.so
b46b5000-b46ca000 r-xp 00000000 08:03 67914625   /usr/lib/wireshark/plugins/mate.so
b46ca000-b46cb000 rw-p 00014000 08:03 67914625   /usr/lib/wireshark/plugins/mate.so
b46cb000-b46dd000 rw-p b46cb000 00:00 0 
b46dd000-b46e0000 r-xp 00000000 08:03 67914623   /usr/lib/wireshark/plugins/m2m.so
b46e0000-b46e1000 rw-p 00003000 08:03 67914623   /usr/lib/wireshark/plugins/m2m.so
b46e1000-b46ec000 r-xp 00000000 08:03 67914619   /usr/lib/wireshark/plugins/irda.so
b46ec000-b46ee000 rw-p 0000b000 08:03 67914619   /usr/lib/wireshark/plugins/irda.so
b46ee000-b46f0000 rw-p b46ee000 00:00 0 
b46f0000-b46f5000 r-xp 00000000 08:03 67914617   /usr/lib/wireshark/plugins/infiniband.so
b46f5000-b46f7000 rw-p 00004000 08:03 67914617   /usr/lib/wireshark/plugins/infiniband.so
b46f7000-b470b000 r-xp 00000000 08:03 67914613   /usr/lib/wireshark/plugins/ethercat.so
b470b000-b4713000 rw-p 00013000 08:03 67914613   /usr/lib/wireshark/plugins/ethercat.so
b471b000-b471d000 rw-p b471b000 00:00 0 
b471d000-b471e000 r--s 00000000 08:03 235109047  /usr/local/share/mime/mime.cache
b471e000-b4720000 r-xp 00000000 08:03 9275       /lib/tls/i686/cmov/libutil-2.7.so
b4720000-b4722000 rw-p 00001000 08:03 9275       /lib/tls/i686/cmov/libutil-2.7.so
b4722000-b4723000 r--s 00000000 08:04 5874046    /home/darrenm/.local/share/mime/mime.cache
b4723000-b4724000 r--p 00000000 08:03 17009955   /usr/share/locale-langpack/en_GB/LC_MESSAGES/atk10.mo
b4724000-b472c000 r-xp 00000000 08:03 135150229  /usr/lib/libtrackerclient.so.0.0.0
b472c000-b472d000 rw-p 00007000 08:03 135150229  /usr/lib/libtrackerclient.so.0.0.0
b472d000-b472e000 r--p 00000000 08:03 17010029   /usr/share/locale-langpack/en_GB/LC_MESSAGES/gvfs.mo
b472e000-b474b000 r-xp 00000000 08:03 206979     /usr/lib/gio/modules/libgiohal-volume-monitor.so
b474b000-b474c000 rw-p 0001c000 08:03 206979     /usr/lib/gio/modules/libgiohal-volume-monitor.so
b474c000-b4752000 r-xp 00000000 08:03 100770095  /usr/lib/gtk-2.0/2.10.0/filesystems/libgio.so
b4752000-b4753000 rw-p 00006000 08:03 100770095  /usr/lib/gtk-2.0/2.10.0/filesystems/libgio.so
b4754000-b4758000 r-xAborted

```

Why is Ubuntu so flaky at the moment? Can anyone give me any pointers to what that stack trace is showing? A bug with libc ? A bug with GTK?

thanks

---

