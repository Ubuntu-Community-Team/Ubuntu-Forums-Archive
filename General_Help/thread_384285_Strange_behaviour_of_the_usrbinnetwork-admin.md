---
title: "Strange behaviour of the /usr/bin/network-admin"
date: 2007-03-14
forum: General Help
---

### Post by fantan on 2007-03-14
Hi, 

Today the network-admin in my system strange acts. When I start it, instead of opening the program, starts the Bug Buddy and scans my system, after that I get the following error message:
"Memory status: size: 32739328 vsize: 0 resident: 32739328 share: 0 rss: 12746752 rss_rlim: 0
CPU usage: start_time: 1173879294 rtime: 0 utime: 92 stime: 0 cutime:79 cstime: 0 timeout: 13 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/network-admin'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1"." The message continues as follows:
"Thread debugging using libthread_db enabled]
[New Thread -1225557616 (LWP 5217)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb734a323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ede1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb75fd8f0 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
#5  0xb784986e in pango_glyph_string_new () from /usr/lib/libpango-1.0.so.0
#6  0xb785357a in pango_layout_set_width () from /usr/lib/libpango-1.0.so.0
#7  0xb78560d5 in pango_layout_iter_get_char_extents ()
   from /usr/lib/libpango-1.0.so.0
#8  0xb7856636 in pango_layout_iter_get_char_extents ()
   from /usr/lib/libpango-1.0.so.0
#9  0xb7856f6b in pango_layout_iter_get_char_extents ()
   from /usr/lib/libpango-1.0.so.0
#10 0xb7a5bec0 in gtk_label_new () from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#12 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#13 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#14 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#15 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#16 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#17 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#18 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#19 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#20 0xb7a2e040 in gtk_hbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#21 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#22 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#23 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#24 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#25 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#26 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#27 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#28 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#29 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#30 0xb799506f in gtk_alignment_new () from /usr/lib/libgtk-x11-2.0.so.0
#31 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#32 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#33 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#34 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#35 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#36 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#37 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#38 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#39 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#40 0xb79a224f in gtk_button_set_alignment ()
   from /usr/lib/libgtk-x11-2.0.so.0
#41 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#42 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#43 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#44 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#45 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#46 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#47 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#48 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#49 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#50 0xb799a7c4 in _gtk_button_box_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#51 0xb7b7ebf0 in gtk_vbutton_box_new () from /usr/lib/libgtk-x11-2.0.so.0
#52 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#53 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#54 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#55 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#56 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#57 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#58 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#59 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#60 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#61 0xb7a2e040 in gtk_hbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#62 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#63 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#64 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#65 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#66 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#67 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#68 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#69 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#70 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#71 0xb7a8c0de in gtk_notebook_new () from /usr/lib/libgtk-x11-2.0.so.0
#72 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#73 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#74 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#75 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#76 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#77 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#78 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#79 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#80 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#81 0xb7b7f450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#82 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#83 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#84 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#85 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#86 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#87 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#88 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#89 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#90 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#91 0xb7b7f450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#92 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#93 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#94 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#95 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#96 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#97 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#98 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#99 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#100 0xb7b88b2c in gtk_widget_size_request ()
   from /usr/lib/libgtk-x11-2.0.so.0
#101 0xb7b90990 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
#102 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#103 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#104 0xb76b179b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#105 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#106 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#107 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#108 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#109 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#110 0xb7b88b2c in gtk_widget_size_request ()
   from /usr/lib/libgtk-x11-2.0.so.0
#111 0xb7b90d10 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
#112 0xb7b99fc1 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
#113 0xb76beb29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#114 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#115 0xb76b179b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#116 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#117 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#118 0xb76c3279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#119 0xb7b89b18 in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
#120 0x08057f19 in ?? ()
#121 0x080ff818 in ?? ()
#122 0x08088af8 in ?? ()
#123 0x08054d50 in ?? ()
#124 0x00000000 in ?? ()

Thread 1 (Thread -1225557616 (LWP 5217)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb734a323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ede1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb75fd8f0 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#5  0xb784986e in pango_glyph_string_new () from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#6  0xb785357a in pango_layout_set_width () from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#7  0xb78560d5 in pango_layout_iter_get_char_extents ()
   from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#8  0xb7856636 in pango_layout_iter_get_char_extents ()
   from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#9  0xb7856f6b in pango_layout_iter_get_char_extents ()
   from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#10 0xb7a5bec0 in gtk_label_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#12 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#13 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#14 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#15 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#16 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#17 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#19 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#20 0xb7a2e040 in gtk_hbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#21 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#22 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#23 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#24 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#25 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#26 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#27 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#28 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#29 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#30 0xb799506f in gtk_alignment_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#31 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#32 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#33 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#34 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#35 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#36 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#37 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#38 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#39 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#40 0xb79a224f in gtk_button_set_alignment ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#41 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#42 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#43 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#44 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#45 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#46 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#47 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#48 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#49 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#50 0xb799a7c4 in _gtk_button_box_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#51 0xb7b7ebf0 in gtk_vbutton_box_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#52 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#53 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#54 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#55 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#56 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#57 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#58 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#59 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#60 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#61 0xb7a2e040 in gtk_hbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#62 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#63 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#64 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#65 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#66 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#67 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#68 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#69 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#70 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#71 0xb7a8c0de in gtk_notebook_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#72 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#73 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#74 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#75 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#76 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#77 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#78 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#79 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#80 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#81 0xb7b7f450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#82 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#83 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#84 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#85 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#86 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#87 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#88 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#89 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#90 0xb7b88b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#91 0xb7b7f450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#92 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#93 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#94 0xb76b187d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#95 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#96 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#97 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#98 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#99 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#100 0xb7b88b2c in gtk_widget_size_request ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#101 0xb7b90990 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#102 0xb76be199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#103 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#104 0xb76b179b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#105 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#106 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#107 0xb76c5e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#108 0xb7ad3cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#109 0xb7ad3f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#110 0xb7b88b2c in gtk_widget_size_request ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#111 0xb7b90d10 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#112 0xb7b99fc1 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#113 0xb76beb29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#114 0xb76affb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#115 0xb76b179b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#116 0xb76c202a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#117 0xb76c30b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#118 0xb76c3279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#119 0xb7b89b18 in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#120 0x08057f19 in ?? ()
No symbol table info available.
#121 0x080ff818 in ?? ()
No symbol table info available.
#122 0x08088af8 in ?? ()
No symbol table info available.
#123 0x08054d50 in ?? ()
No symbol table info available.
#124 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
"
What happened? Till now on my system everything went without errors. Please anybody help me, how to repair the network-admin?

---

### Post by Gnowm on 2007-03-17
Same error here too.

I have tried to use Synaptic to uninstall/reinstall network-manager package and the network-manager-gnome packages. Still no resolution.

Managed to convert from DHCP to static IP's (the only reason i found out network-admin was broken) by editing by hand the file /etc/network/interfaces thusly

```
# 
The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth1 inet static
        address 192.168.0.3
        netmask 255.255.255.0
        gateway 192.168.0.1
auto eth1

```


Any assistance to get the gui version of the manager back would be appreciated by this user (for future reference)

Gnowm

---

