---
title: "what's wrong with my open office??"
date: 2007-06-30
forum: General Help
---

### Post by voochee on 2007-06-30
when I run open office in a terminal, I got this message, and the open office is not respond. 
```
root@linux-laptop:/home/chee# ooffice 
*** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x080d02c8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6cc67cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6cc9e30]
/usr/lib/openoffice/program/libuno_sal.so.3(rtl_freeMemory+0x1d)[0xb731e0bd]
/usr/lib/openoffice/program/soffice.bin[0x809192e]
/usr/lib/openoffice/program/soffice.bin(_ZdlPv+0x26)[0x8091966]
/usr/lib/libscim-1.0.so.8[0xa97d1156]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xa97d1f77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xa97ccf05]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so[0xa9872f7b]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x381)[0xb5ccfb41]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0xa2f)[0xb5cb61cf]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb5cb65ef]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb5cb67a0]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(_Z23gtk_im_context_scim_newv+0x67)[0xa9867b57]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(im_module_create+0x3c)[0xa987727c]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_im_module_create+0xb9)[0xb57acd29]
/usr/lib/libgtk-x11-2.0.so.0[0xb57ad93b]
/usr/lib/libgtk-x11-2.0.so.0[0xb57adb39]
/usr/lib/libgtk-x11-2.0.so.0(gtk_im_context_set_client_window+0x4e)[0xb57aaf0e]
/usr/lib/libgtk-x11-2.0.so.0[0xb575471f]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb5cbd9d9]
/usr/lib/libgobject-2.0.so.0[0xb5caee49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5cb062b]
/usr/lib/libgobject-2.0.so.0[0xb5cc159a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5cc2627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5cc27e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xba)[0xb58e8bea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x1de)[0xb58e91ce]
/usr/lib/libgtk-x11-2.0.so.0(gtk_fixed_put+0xd3)[0xb5781ec3]
/usr/lib/libgtk-x11-2.0.so.0[0xb5781f08]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x59)[0xb5cbcee9]
/usr/lib/libgobject-2.0.so.0[0xb5caee49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5cb062b]
/usr/lib/libgobject-2.0.so.0[0xb5cc159a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5cc2627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5cc27e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_add+0x12c)[0xb57381bc]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a1b2bd]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a1d043]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a27abd]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e79ff5]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e0709b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11ModalDialogC2EP6WindowRK5ResId+0x67)[0xb7e07ac7]
/usr/lib/openoffice/program/libsvt680li.so(_ZN12WizardDialogC2EP6WindowRK5ResIdhs+0x3e)[0xb78d499e]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt14OWizardMachineC2EP6WindowRK5ResIdmhhs+0x4a)[0xb78a61da]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt13RoadmapWizardC2EP6WindowRK5ResIdmS5_h+0x4f)[0xb78a355f]
/usr/lib/openoffice/program/libspl680li.so[0xa997b926]
/usr/lib/openoffice/program/libspl680li.so[0xa9972024]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0xd59)[0x806bc39]
/usr/lib/openoffice/program/libvcl680li.so[0xb7c87c3c]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7c87d45]
/usr/lib/openoffice/program/soffice.bin(main+0x65)[0x805ff85]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb6c74ebc]
/usr/lib/openoffice/program/soffice.bin(__gxx_personality_v0+0x249)[0x805fe11]
======= Memory map: ========
08048000-0809c000 r-xp 00000000 03:02 1902996    /usr/lib/openoffice/program/soffice.bin
0809c000-0809e000 rw-p 00053000 03:02 1902996    /usr/lib/openoffice/program/soffice.bin
0809e000-0835f000 rw-p 0809e000 00:00 0          [heap]
a9600000-a9621000 rw-p a9600000 00:00 0 
a9621000-a9700000 ---p a9621000 00:00 0 
a9769000-a983d000 r-xp 00000000 03:02 1806338    /usr/lib/libscim-1.0.so.8.1.0
a983d000-a984b000 rw-p 000d4000 03:02 1806338    /usr/lib/libscim-1.0.so.8.1.0
a985b000-a987c000 r-xp 00000000 03:02 1869658    /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
a987c000-a987d000 rw-p 00021000 03:02 1869658    /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
a987d000-a98dd
** (process:12639): WARNING **: Unknown error forking main binary / abnormal early exit ...

```
any ideas?

---

### Post by dexter on 2007-06-30
Why are you running OpenOffice as root ? What happens if you run it as a normal user.
It seems like openoffice is trying to free a misplaced pointer. This could be caused by bad memory. Try testing it with memtest. You can also try to reïnstall OpenOffice.

---

### Post by voochee on 2007-06-30
hi, if a run it as a normal user, i get this```
chee@linux-laptop:~$ ooffice 
Failed to open display
chee@linux-laptop:~$ /usr/lib/openoffice/program/soffice.bin X11 error: Can't open display: 
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server
   (See "man X" resp. "man xhost" for details)

```
the system will mess up if I reinstall it.

---

### Post by voochee on 2007-06-30
hi, if a run it as a normal user, i get this```
chee@linux-laptop:~$ ooffice 
Failed to open display
chee@linux-laptop:~$ /usr/lib/openoffice/program/soffice.bin X11 error: Can't open display: 
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server
   (See "man X" resp. "man xhost" for details)

```
the system will mess up if I reinstall it.

---

### Post by voochee on 2007-06-30
hi, if a run it as a normal user, i get this```
chee@linux-laptop:~$ ooffice 
Failed to open display
chee@linux-laptop:~$ /usr/lib/openoffice/program/soffice.bin X11 error: Can't open display: 
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server
   (See "man X" resp. "man xhost" for details)

```
the system will mess up if I reinstall it.

---

### Post by voochee on 2007-06-30
hi, if a run it as a normal user, i get this```
chee@linux-laptop:~$ ooffice 
Failed to open display
chee@linux-laptop:~$ /usr/lib/openoffice/program/soffice.bin X11 error: Can't open display: 
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server
   (See "man X" resp. "man xhost" for details)

```
the system will mess up if I reinstall it.

---

