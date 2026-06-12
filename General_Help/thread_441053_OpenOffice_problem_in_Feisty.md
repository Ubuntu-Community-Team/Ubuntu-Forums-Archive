---
title: "OpenOffice problem in Feisty"
date: 2007-05-12
forum: General Help
---

### Post by vatzcar on 2007-05-12
I was using Feisty without any problem. Today I've installed Adobe Reader 7.1 and now I can't run OO apps. not even Adobe Reader as well. when I'm trying to run OO apps. from terminal following error is showing:

```
*** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x080d0a18 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6cc27cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6cc5e30]
/usr/lib/openoffice/program/libuno_sal.so.3(rtl_freeMemory+0x1d)[0xb73180bd]
/usr/lib/openoffice/program/soffice.bin[0x809192e]
/usr/lib/openoffice/program/soffice.bin(_ZdlPv+0x26)[0x8091966]
/usr/lib/libscim-1.0.so.8[0xad799156]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xad799f77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xad794f05]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so[0xad838f7b]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x381)[0xb5ccbb41]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0xa2f)[0xb5cb21cf]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb5cb25ef]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb5cb27a0]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(_Z23gtk_im_context_scim_newv+0x67)[0xad82db57]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(im_module_create+0x3c)[0xad83d27c]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_im_module_create+0xb9)[0xb57aad29]
/usr/lib/libgtk-x11-2.0.so.0[0xb57ab93b]
/usr/lib/libgtk-x11-2.0.so.0[0xb57abb39]
/usr/lib/libgtk-x11-2.0.so.0(gtk_im_context_set_client_window+0x4e)[0xb57a8f0e]
/usr/lib/libgtk-x11-2.0.so.0[0xb575271f]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb5cb99d9]
/usr/lib/libgobject-2.0.so.0[0xb5caae49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5cac62b]
/usr/lib/libgobject-2.0.so.0[0xb5cbd59a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5cbe627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5cbe7e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xba)[0xb58e6bea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x1de)[0xb58e71ce]
/usr/lib/libgtk-x11-2.0.so.0(gtk_fixed_put+0xd3)[0xb577fec3]
/usr/lib/libgtk-x11-2.0.so.0[0xb577ff08]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x59)[0xb5cb8ee9]
/usr/lib/libgobject-2.0.so.0[0xb5caae49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5cac62b]
/usr/lib/libgobject-2.0.so.0[0xb5cbd59a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5cbe627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5cbe7e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_add+0x12c)[0xb57361bc]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a172bd]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a19043]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a23abd]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e73ff5]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e0109b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11ModalDialogC2EP6WindowRK5ResId+0x67)[0xb7e01ac7]
/usr/lib/openoffice/program/libsvt680li.so(_ZN12WizardDialogC2EP6WindowRK5ResIdhs+0x3e)[0xb78ce99e]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt14OWizardMachineC2EP6WindowRK5ResIdmhhs+0x4a)[0xb78a01da]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt13RoadmapWizardC2EP6WindowRK5ResIdmS5_h+0x4f)[0xb789d55f]
/usr/lib/openoffice/program/libspl680li.so[0xad941926]
/usr/lib/openoffice/program/libspl680li.so[0xad938024]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0xd59)[0x806bc39]
/usr/lib/openoffice/program/libvcl680li.so[0xb7c81c3c]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7c81d45]
/usr/lib/openoffice/program/soffice.bin(main+0x65)[0x805ff85]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb6c70ebc]
/usr/lib/openoffice/program/soffice.bin(__gxx_personality_v0+0x249)[0x805fe11]
======= Memory map: ========
08048000-0809c000 r-xp 00000000 08:07 1227406    /usr/lib/openoffice/program/soffice.bin
0809c000-0809e000 rw-p 00053000 08:07 1227406    /usr/lib/openoffice/program/soffice.bin
0809e000-08377000 rw-p 0809e000 00:00 0          [heap]
ad600000-ad621000 rw-p ad600000 00:00 0 
ad621000-ad700000 ---p ad621000 00:00 0 
ad731000-ad805000 r-xp 00000000 08:07 1162914    /usr/lib/libscim-1.0.so.8.1.0
ad805000-ad813000 rw-p 000d4000 08:07 1162914    /usr/lib/libscim-1.0.so.8.1.0
ad821000-ad842000 r-xp 00000000 08:07 1210424    /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
ad842000-ad843000 rw-p 00021000 08:07 1210424    /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
ad843000-ad8a3000 rw-s 00000000 00:08 1441809    /SYSV00000000 (deleted)
ad8a3000-ad8b3000 r-xp 00000000 08:07 1227199    /usr/lib/openoffice/program/libfileacc.so
ad8b3000-ad8b4000 rw-p 00010000 08:07 1227199 
** (process:6235): WARNING **: Unknown error forking main binary / abnormal early exit ...

```

I can't uninstall Adobe Reader. How can I resolve the problem?

---

### Post by aldeby on 2007-05-28
If you installed SCIM imput for non latin languages this fix done the job for me: 
> [http://ubuntuforums.org/showpost.php?p=2568329](http://ubuntuforums.org/showpost.php?p=2568329)
Hope it helps. It has been a very annoying bug.

---

