---
title: "Core Dump? Whats happening?"
date: 2007-08-12
forum: General Help
---

### Post by jusmurph on 2007-08-12
I just reinstalled Ubuntu and I'm getting the following errors:


Rhythmbox (happens when i try to point ot my library.
```
anth@smurph:~$ rhythmbox
*** glibc detected *** rhythmbox: double free or corruption (fasttop): 0x00000000014e90f0 
***
======= Backtrace: =========
/lib/libc.so.6[0x2b7d00f9eb23]
/lib/libc.so.6(cfree+0x8c)[0x2b7d00fa226c]
/usr/lib/libglib-2.0.so.0(g_slist_foreach+0x1d)[0x2b7d006861ad]
/usr/lib/librhythmbox-core.so.0(rb_slist_deep_free+0x12)[0x2b7cf8138212]
rhythmbox[0x4473a1]
rhythmbox[0x4474d8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10a)[0x2b7cff8b37da]
/usr/lib/libgobject-2.0.so.0[0x2b7cff8c3408]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x833)[0x2b7cff8c4843]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x2b7cff8c4a13]
/usr/lib/libgtk-x11-2.0.so.0[0x2b7cfc514689]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10a)[0x2b7cff8b37da]
/usr/lib/libgobject-2.0.so.0[0x2b7cff8c384d]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x833)[0x2b7cff8c4843]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x2b7cff8c4a13]
/usr/lib/libgtk-x11-2.0.so.0[0x2b7cfc512f09]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5d)[0x2b7cfc5d068d]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10a)[0x2b7cff8b37da]
/usr/lib/libgobject-2.0.so.0[0x2b7cff8c3a18]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x607)[0x2b7cff8c4617]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x2b7cff8c4a13]
/usr/lib/libgtk-x11-2.0.so.0[0x2b7cfc6ce13e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0xfd)[0x2b7cfc5c9c7d]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x321)[0x2b7cfc5cac91]
/usr/lib/libgdk-x11-2.0.so.0[0x2b7cfca7045c]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1b4)[0x2b7d0066fa14]
/usr/lib/libglib-2.0.so.0[0x2b7d0067285d]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0x2b7d00672b6a]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa3)[0x2b7cfc5cb023]
rhythmbox(main+0x3db)[0x42345b]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2b7d00f4c8e4]
rhythmbox[0x422fe9]
======= Memory map: ========
00400000-004b9000 r-xp 00000000 08:01 4161698                            /usr/bin/rhythmbox
006b8000-006c4000 rw-p 000b8000 08:01 4161698                            /usr/bin/rhythmbox
006c4000-01aa7000 rw-p 006c4000 00:00 0                                  [heap]
41803000-41804000 ---p 41803000 00:00 0 
41804000-42004000 rw-p 41804000 00:00 0 
42004000-42005000 ---p 42004000 00:00 0 
42005000-42805000 rw-p 42005000 00:00 0 
42805000-42806000 ---p 42805000 00:00 0 
42806000-43006000 rw-p 42806000 00:00 0 
43006000-43007000 ---p 43006000 00:00 0 
43007000-43807000 rw-p 43007000 00:00 0 
43807000-43808000 ---p 43807000 00:00 0 
43808000-44008000 rw-p 43808000 00:00 0 
2aaaaaaab000-2aaaaaaad000 r-xp 00000000 08:01 803267                     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
2aaaaaaad000-2aaaaabac000 ---p 00002000 08:01 803267                     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
2aaaaabac000-2aaaaabad000 rw-p 00001000 08:01 803267                     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
2aaaaabad000-2aaaaabdf000 r-xp 00000000 08:01 4211091                    /usr/lib/librsvg-2.so.2.16.0
2aaaaabdf000-2aaaaacde000 ---p 00032000 08:01 4211091                    /usr/lib/librsvg-2.so.2.16.0
2aaaaacde000-2aaaaace0000 rw-p 00031000 08:01 4211091                    /usr/lib/librsvg-2.so.2.16.0
2aaaaace0000-2aaaaad11000 r-xp 00000000 08:01 4210823                    /usr/lib/libgsf-1.so.114.0.3
2aaaaad11000-2aaaaaf11000 ---p 00031000 08:01 4210823                    /usr/lib/libgsf-1.so.114.0.3
2aaaaaf11000-2aaaaaf15000 rw-p 00031000 08:01 4210823                    /usr/lib/libgsf-1.so.114.0.3
2aaaaaf15000-2aaaaaf16000 rw-p 2aaaaaf15000 00:00 0 
2aaaaaf16000-2aaaaaf4d000 r-xp 00000000 08:01 755053                     /usr/lib/libcroco-0.6.so.3.0.1
2aaaaaf4d000-2aaaab04c000 ---p 00037000 08:01 755053                     /usr/lib/libcroco-0.6.so.3.0.1
2aaaab04c000-2aaaab050000 rw-p 00036000 08:01 755053                     /usr/lib/libcroco-0.6.so.3.0.1
2aaaab050000-2aaaab051000 r--p 00000000 08:01 1114916                    /usr/share/locale-langpack/en_AU/LC_MESSAGES/launchpad-integration.mo
2aaaab05f000-2aaaab06e000 r-xp 00000000 08:01 3948580                    /lib/libbz2.so.1.0.3
2aaaab06e000-2aaaab26d000 ---p 0000f000 08:01 3948580                    /lib/libbz2.so.1.0.3
2aaaab26d000-2aaaab26f000 rw-p 0000e000 08:01 3948580                    /lib/libbz2.so.1.0.3
2aaaab26f000-2aaaab27d000 r-xp 00000000 08:01 803182                     /usr/lib/gnome-vfs-2.0/modules/libfile.so
2aaaab27d000-2aaaab47c000 ---p 0000e000 08:01 803182                     /usr/lib/gnome-vfs-2.0/modules/libfile.so
2aaaab47c000-2aaaab47d000 rw-p 0000d000 08:01 803182                     /usr/lib/gnome-vfs-2.0/modules/libfile.so
2aaaab47d000-2aaaab481000 r-xp 00000000 08:01 3948573                    /lib/libattr.so.1.1.0
2aaaab481000-2aaaab680000 ---p 00004000 08:01 3948573                    /lib/libattr.so.1.1.0
2aaaab680000-2aaaab681000 rw-p 00003000 08:01 3948573                    /lib/libattr.so.1.1.0
2aaaab681000-2aaaab687000 r-xp 00000000 08:01 3948569                    /lib/libacl.so.1.1.0
2aaaab687000-2aaaab886000 ---p 00006000 08:01 3948569                    /lib/libacl.so.1.1.0
2aaaab886000-2aaaab887000 rw-p 00005000 08:01 3Aborted (core dumped)

```

AVN (Won't even launch, it did for a while then just stopped)
```
anth@smurph:~$ avant-window-navigator
52,52
New width = 58LOADED : /usr/share/applications/firefox.desktop
Segmentation fault (core dumped
```

---

