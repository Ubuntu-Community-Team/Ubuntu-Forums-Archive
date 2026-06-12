---
title: "Evolution won't launch"
date: 2008-07-09
forum: General Help
---

### Post by ztirffritz on 2008-07-09
I've found that Evolution suddenly will not start.  When I try to launch it from the icon it shows that it is trying then just quits.  If I try to launch it from the command line I get the stuff below.  The only thing that I changed that I can recall is I tried to connect to a public Exchange folder.  It didn't appear to work.  Other than uninstalling Evolution and re-installing and configuring it does anyone know how to jump start it?

> frankh@60-ITMngr:~$ evolution
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
*** glibc detected *** evolution: munmap_chunk(): invalid pointer: 0x00000000007afd40 ***
======= Backtrace: =========
/lib/libc.so.6(cfree+0x1b6)[0x7f08e51d6d46]
/usr/lib/libexchange-storage-1.2.so.3[0x7f08de11d2a0]
/usr/lib/libexchange-storage-1.2.so.3(e2k_results_free+0x2f)[0x7f08de11d2ef]
/usr/lib/libexchange-storage-1.2.so.3[0x7f08de10a79e]
/usr/lib/libexchange-storage-1.2.so.3[0x7f08de10bfe7]
/usr/lib/libexchange-storage-1.2.so.3[0x7f08de106732]
/usr/lib/libexchange-storage-1.2.so.3(exchange_account_connect+0x54b)[0x7f08de106f1b]
/usr/lib/evolution/2.22/plugins/liborg-gnome-exchange-operations.so(exchange_config_listener_authenticate+0xdd)[0x7f08debb3fed]
/usr/lib/evolution/2.22/plugins/liborg-gnome-exchange-operations.so[0x7f08debb4e1b]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f)[0x7f08e5993bcf]
/usr/lib/libgobject-2.0.so.0[0x7f08e59a7aa8]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875)[0x7f08e59a90d5]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f08e59a9483]
/usr/lib/libedataserver-1.2.so.9[0x7f08eb7ac9fe]
/usr/lib/evolution/2.22/plugins/liborg-gnome-exchange-operations.so[0x7f08debb3d0a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f2)[0x7f08e54f8262]
/usr/lib/libglib-2.0.so.0[0x7f08e54fb516]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1b7)[0x7f08e54fb7d7]
/usr/lib/libbonobo-2.so.0(bonobo_main+0x46)[0x7f08e9a8f466]
evolution[0x417485]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7f08e517d1c4]
evolution[0x40afc9]
======= Memory map: ========
00400000-00421000 r-xp 00000000 08:01 4047046                            /usr/bin/evolution
00620000-00624000 rw-p 00020000 08:01 4047046                            /usr/bin/evolution
00624000-007ed000 rw-p 00624000 00:00 0                                  [heap]
40ee0000-40ee1000 ---p 40ee0000 00:00 0 
40ee1000-416e1000 rw-p 40ee1000 00:00 0 
7f08dbdee000-7f08dbdf2000 r-xp 00000000 08:01 3989590                    /lib/libnss_dns-2.7.so
7f08dbdf2000-7f08dbff2000 ---p 00004000 08:01 3989590                    /lib/libnss_dns-2.7.so
7f08dbff2000-7f08dbff4000 rw-p 00004000 08:01 3989590                    /lib/libnss_dns-2.7.so
7f08dbff4000-7f08dbff6000 r-xp 00000000 08:01 3989598                    /lib/libnss_mdns4_minimal.so.2
7f08dbff6000-7f08dc1f5000 ---p 00002000 08:01 3989598                    /lib/libnss_mdns4_minimal.so.2
7f08dc1f5000-7f08dc1f6000 rw-p 00001000 08:01 3989598                    /lib/libnss_mdns4_minimal.so.2
7f08dc1f6000-7f08dc20e000 r-xp 00000000 08:01 4048903                    /usr/lib/libsasl2.so.2.0.22
7f08dc20e000-7f08dc40e000 ---p 00018000 08:01 4048903                    /usr/lib/libsasl2.so.2.0.22
7f08dc40e000-7f08dc40f000 rw-p 00018000 08:01 4048903                    /usr/lib/libsasl2.so.2.0.22
7f08dc40f000-7f08dc41d000 r-xp 00000000 08:01 4048930                    /usr/lib/liblber-2.4.so.2.0.5
7f08dc41d000-7f08dc61c000 ---p 0000e000 08:01 4048930                    /usr/lib/liblber-2.4.so.2.0.5
7f08dc61c000-7f08dc61d000 rw-p 0000d000 08:01 4048930                    /usr/lib/liblber-2.4.so.2.0.5
7f08dc61d000-7f08dc65e000 r-xp 00000000 08:01 4048946                    /usr/lib/libldap_r-2.4.so.2.0.5
7f08dc65e000-7f08dc85e000 ---p 00041000 08:01 4048946                    /usr/lib/libldap_r-2.4.so.2.0.5
7f08dc85e000-7f08dc860000 rw-p 00041000 08:01 4048946                    /usr/lib/libldap_r-2.4.so.2.0.5
7f08dc860000-7f08dc862000 rw-p 7f08dc860000 00:00 0 
7f08dc862000-7f08dc86b000 r-xp 00000000 08:01 4072235                    /usr/lib/evolution/2.22/libevolution-addressbook-importers.so.0.0.0
7f08dc86b000-7f08dca6a000 ---p 00009000 08:01 4072235                    /usr/lib/evolution/2.22/libevolution-addressbook-importers.so.0.0.0
7f08dca6a000-7f08dca6c000 rw-p 00008000 08:01 4072235                    /usr/lib/evolution/2.22/libevolution-addressbook-importers.so.0.0.0
7f08dca6c000-7f08dca71000 r-xp 00000000 08:01 4072234                    /usr/lib/evolution/2.22/libevolution-addressbook-a11y.so.0.0.0
7f08dca71000-7f08dcc71000 ---p 00005000 08:01 4072234                    /usr/lib/evolution/2.22/libevolution-addressbook-a11y.so.0.0.0
7f08dcc71000-7f08dcc72000 rw-p 00005000 08:01 4072234                    /usr/lib/evolution/2.22/libevolution-addressbook-a11y.so.0.0.0
7f08dcc72000-7f08dcc7c000 r-xp 00000000 08:01 4072296                    /usr/lib/evolution/2.22/libevolution-smime.so.0.0.0
7f08dcc7c000-7f08dce7b000 ---p 0000a000 08:01 4072296                    /usr/lib/evolution/2.22/libevolution-smime.so.0.0.0
7f08dce7b000-7f08dce7c000 rw-p 00009000 08:01 4072296                    /usr/lib/evolution/2.22/libevolution-smime.so.0.0.0
7f08dce7c000-7f08dce88000 r-xp 00000000 08:01 4072228                    /usr/lib/evolution/2.22/libessmime.so.0.0.0
7f08dce88000-7f08dd088000 ---p 0000c000 08:01 4072228                    /usr/lib/evolution/2.22/libessmime.so.0.0.0
7f08dd088000-7f08dd089000 rw-p 0000c000 08:01 4072228                    /usr/lib/evolution/2.22/libessmime.so.0.0.0
7f08dd089000-7f08dd090000 r-xp 00000000 08:01 4072295                    /usr/lib/evolution/2.22/libevolution-mail-importers.so.0.0.0
7f08dd090000-7f08dd290000 ---p 00007000 08:01 4072295                    /usr/lib/evolution/2.22/libevolution-mail-importers.so.0.0.0
7f08dd290000-7f08dd291000 rw-p 00007000 08:01 4072295                    /usr/lib/evolution/2.22/libevolution-mail-importers.so.0.0.0
7f08dd291000-7f08dd29b000 r-xp 00000000 08:01 4072139                    /usr/lib/evolution/2.22/libecontactlisteditor.so.0.0.0
7f08dd29b000-7f08dd49b000 ---p 0000a000 08:01 4072139                    /usr/lib/evolution/2.22/libecontactlisteditor.so.0.0.0
7f08dd49b000-7f08dd49c000 rw-p 0000a000 08:01 4072139                    /usr/lib/evolution/2.22/libecontactlisteditor.so.0.0.0
7f08dd49c000-7f08dd4b5000 r-xp 00000000 08:01 4072137                    /usr/lib/evolution/2.22/libecontacteditor.so.0.0.0
7f08dd4b5000-7f08dd6b5000 ---p 00019000 08:01 4072137                    /usr/lib/evolution/2.22/libecontacteditor.so.0.0.0
7f08dd6b5000-7f08dd6b7000 rw-p 00019000 08:01 4072137                    /usr/lib/evolution/2.22/libecontacteditor.so.0.0.0
7f08dd6b7000-7f08dd6ca000 r-xp 00000000 08:01 4072293                    /usr/lib/evolution/2.22/libevolution-calendar-a11y.so.0.0.0
7f08dd6ca000-7f08dd8c9000 ---p 00013000 08:01 4072293                    /usr/lib/evolution/2.22/libevolution-calendar-a11y.so.0.0.0
7f08dd8c9000-7f08dd8cb000 rw-p 00012000 08:01 4072293                    /usr/lib/evolution/2.22/libevolution-calendar-a11y.so.0.0.0
7f08dd8cb000-7f08dd8d1000 r-xp 00000000 08:01 4072220                    /usr/lib/evolution/2.22/libefilterbar.so.0.0.0
7f08dd8d1000-7f08ddad1000 ---p 00006000 08:01 4072220                    /usr/lib/evolution/2.22/libefilterbar.so.0.0.0
7f08ddad1000-7f08ddad2000 rw-p 00006000 08:01 4072220                    /usr/lib/evolution/2.22/libefilterbar.so.0.0.0
7f08ddad2000-7f08ddad8000 r-xp 00000000 08:01 4072294                    /usr/lib/evolution/2.22/libevolution-calendar-importers.so.0.0.0
7f08ddad8000-7f08ddcd7000 ---p 00006000 08:01 4072294                    /usr/lib/evolution/2.22/libevolution-calendar-importers.so.0.0.0
7f08ddcd7000-7f08ddcd8000 rw-p 00005000 08:01 4072294                    /usr/lib/evolution/2.22/libevolution-calendar-importers.so.0.0.0
7f08ddcd8000-7f08ddcdb000 r-xp 00000000 08:01 4072133                    /usr/lib/evolution/2.22/libeabutil.so.0.0.0
7f08ddcdb000-7f08ddeda000 ---p 00003000 08:01 4072133                    /usr/lib/evolution/2.22/libeabutil.so.0.0.0
7f08ddeda000-7f08ddedb000 rw-p 00002000 08:01 4072133                    /usr/lib/evolution/2.22/libeabutil.so.0.0.0
7f08ddedb000-7f08ddeec000 r-xp 00000000 08:01 4072299                    /usr/lib/evolution/2.22/libmenus.so.0.0.0
7f08ddeec000-7f08de0ec000 ---p 00011000 08:01 4072299                    /usr/lib/evolution/2.22/libmenus.so.0.0.0
7f08de0ec000-7f08de0ed000 rw-p 00011000 08:01 4072299                    /usr/lib/evolution/2.22/libmenus.so.0.0.0
7f08de0ed000-7f08de135000 r-xp 00000000 08:01 616889                     /usr/lib/libexchange-storage-1.2.so.3.0.0
7f08de135000-7f08de335000 ---p 00048000 08:01 616889                     /usr/lib/libexchange-storage-1.2.so.3.0.0
7f08de335000-7f08de338000 rw-p 00048000 08:01 616889                     /usr/lib/libexchange-storage-1.2.so.3.0.0
7f08de338000-7f08de37d000 r-xp 00000000 08:01 4072300                    /usr/lib/evolution/2.22/components/libevolution-addressbook.so
7f08de37d000-7f08de57c000 ---p 00045000 08:01 4072300                    /usr/lib/evolution/2.22/components/libevolution-addressbook.so
7f08de5Aborted


---

### Post by Kango_V on 2008-07-23
Mine does this every time.  I've tried reinstalling but no joy yet.

---

### Post by ztirffritz on 2008-07-23
I've reported a bug on this issue here:

[https://bugs.launchpad.net/bugs/247067](https://bugs.launchpad.net/bugs/247067)

They seem to have confirmed the bug, but I still can not launch evolution, unless I disable all plugins (primarily the Exchange plugin).  This makes Evolution useless to me.  Please feel free to visit the bug and toss your name into the hat so that they see it affects more than just me.

There is also an upstream bug report here:
[http://bugzilla.gnome.org/show_bug.cgi?id=543663](http://bugzilla.gnome.org/show_bug.cgi?id=543663)

---

