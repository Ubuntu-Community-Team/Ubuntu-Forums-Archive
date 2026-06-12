---
title: "Open Office Crash"
date: 2006-10-03
forum: General Help
---

### Post by smiggs on 2006-10-03
Whenever I try to run an open office application they don't run properly, I've tried uninstalling and reinstalling but to no avail. I ran Open Writer from the command line and got this error message

> Fatal exception: Signal 11
Stack:
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c51f]
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c83f]
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c8dd]
[0xffffe500]
/usr/lib32/libfreetype.so.6(FT_Add_Default_Modules+0x2f)[0x567aaf03]
/usr/lib32/libfreetype.so.6(FT_Init_FreeType+0x66)[0x567aaf7b]
/usr/lib/openoffice/program/libvcl680li.so[0x55797e06]
/usr/lib/openoffice/program/libvcl680li.so(_ZN10GlyphCacheC1Em+0x52)[0x55791f8a]
/usr/lib/openoffice/program/libvcl680li.so(_ZN10GlyphCache11GetInstanceEv+0x3b)[0x55791fd3]
/usr/lib/openoffice/program/libvcl680li.so(_ZN10GlyphCache14EnsureInstanceER14GlyphCachePeerb+0x21)[0x5579201f]
/usr/lib/openoffice/program/libvclplug_gen680li.so(_ZN14X11SalGraphics14GetDevFontListEP15ImplDevFontList+0xa0)[0x597b39de]
/usr/lib/openoffice/program/libvcl680li.so[0x5565e376]
/usr/lib/openoffice/program/libvcl680li.so[0x5572c5b1]
/usr/lib/openoffice/program/libvcl680li.so[0x557352bb]
/usr/lib/openoffice/program/libvcl680li.so[0x557365bd]
/usr/lib/openoffice/program/libvcl680li.so[0x556e8c39]
/usr/lib/openoffice/program/libvcl680li.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x76)[0x55715b34]
/usr/lib/openoffice/program/libsvx680li.so[0x5b149b62]
/usr/lib/openoffice/program/libsvx680li.so[0x5b260c88]
/usr/lib/openoffice/program/libsvx680li.so[0x5b2613fd]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop19impl_callRecoveryUIEhhh+0x279)[0x8069d29]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop9SaveTasksEl+0xe)[0x806abe0]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop9ExceptionEt+0xa6)[0x806b102]
/usr/lib/openoffice/program/libvcl680li.so[0x555f49de]
/usr/lib/openoffice/program/libvos3gcc3.so(_ZN3vos28_cpp_OSignalHandler_FunctionEPvP13oslSignalInfo+0xf)[0x55dba8f7]
/usr/lib/openoffice/program/libvos3gcc3.so(_Z24_OSignalHandler_FunctionPvP13oslSignalInfo+0x1a)[0x55dba914]
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c58b]
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c8c9]
[0xffffe500]
/usr/lib32/libfreetype.so.6(FT_Add_Default_Modules+0x2f)[0x567aaf03]
/usr/lib32/libfreetype.so.6(FT_Init_FreeType+0x66)[0x567aaf7b]
/usr/lib32/libpangocairo-1.0.so.0[0x596b5cb2]
/usr/lib32/libgobject-2.0.so.0(g_type_create_instance+0x490)[0x5815f382]
/usr/lib32/libgobject-2.0.so.0[0x58145aa2]
/usr/lib32/libgobject-2.0.so.0(g_object_newv+0x1d6)[0x58146115]
/usr/lib32/libgobject-2.0.so.0(g_object_new_valist+0x214)[0x58146ca5]
/usr/lib32/libgobject-2.0.so.0(g_object_new+0x3c)[0x58146e4e]
/usr/lib32/libpangocairo-1.0.so.0(pango_cairo_font_map_new+0x2c)[0x596b35d1]
/usr/lib32/libpangocairo-1.0.so.0(pango_cairo_font_map_get_default+0x27)[0x596b35fe]
/usr/lib32/libgdk-x11-2.0.so.0(gdk_pango_context_get_for_screen+0x42)[0x59623c77]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_widget_create_pango_context+0x4d)[0x59534bad]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_widget_get_pango_context+0x92)[0x59534c9a]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_widget_create_pango_layout+0x45)[0x59534d0b]
/usr/lib32/libgtk-x11-2.0.so.0[0x593e11e5]
/usr/lib32/libgtk-x11-2.0.so.0[0x593e1c24]
/usr/lib32/libgtk-x11-2.0.so.0[0x593e2ca0]
/usr/lib32/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x43)[0x5814c423]
/usr/lib32/libgobject-2.0.so.0[0x5814016f]
/usr/lib32/libgobject-2.0.so.0(g_closure_invoke+0x11e)[0x5814079f]
/usr/lib32/libgobject-2.0.so.0[0x5814f5cc]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit_valist+0x6b0)[0x58150b19]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit+0x29)[0x58150e89]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_widget_realize+0xa9)[0x595383d1]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x235)[0x59538a8e]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_fixed_put+0xc6)[0x5940d69b]
/usr/lib32/libgtk-x11-2.0.so.0[0x5940dc90]
/usr/lib32/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x53)[0x5814cdb7]
/usr/lib32/libgobject-2.0.so.0[0x5814016f]
/usr/lib32/libgobject-2.0.so.0(g_closure_invoke+0x11e)[0x5814079f]
/usr/lib32/libgobject-2.0.so.0[0x5814f5cc]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit_valist+0x6b0)[0x58150b19]
/usr/lib32/libgobject-2.0.so.0(g_signal_emit+0x29)[0x58150e89]
/usr/lib32/libgtk-x11-2.0.so.0(gtk_container_add+0x124)[0x593c61ae]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0x59307129]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0x5930d0e4]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0x5931002f]
/usr/lib/openoffice/program/libvcl680li.so[0x557365ab]
/usr/lib/openoffice/program/libvcl680li.so[0x556e8c39]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11ModalDialogC2EP6WindowRK5ResId+0x51)[0x556e8dad]
/usr/lib/openoffice/program/libsvt680li.so(_ZN12WizardDialogC2EP6WindowRK5ResIdhs+0x2b)[0x55a242e3]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt14OWizardMachineC2EP6WindowRK5ResIdmhhs+0x38)[0x55a077b4]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt13RoadmapWizardC2EP6WindowRK5ResIdmS5_h+0x2e)[0x55a05022]
/usr/lib/openoffice/program/libspl680li.so[0x5a2f7329]
/usr/lib/openoffice/program/libspl680li.so[0x5a2efedd]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0x9c1)[0x806bc6d]
/usr/lib/openoffice/program/libvcl680li.so[0x555f4c49]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x29)[0x555f4cf9]
/usr/lib/openoffice/program/soffice.bin(sal_main+0x47)[0x80646db]
/lib32/libc.so.6(__libc_start_main+0xd2)[0x564afea2]
/usr/lib/openoffice/program/soffice.bin(_ZN6Window11RequestHelpERK9HelpEvent+0x31)[0x8064615]
/usr/lib/openoffice/program/soffice: line 233:  5560 Aborted                 "$sd_prog/$sd_binary" "$@"

** (process:5547): WARNING **: Unknown error forking main binary / abnormal early exit ...


Any thoughts? Please be gentle with me I'm a relative newbie to Ubuntu and Linux generally.

---

### Post by henriquemaia on 2006-10-03
Try removing your ~/.openoffice.org2 folder and start it with its defauts configurations.

On a terminal, type:

```
mv ~/.openoffice.org2 ~/Desktop/openoffice.org2
```

(this command will move the OpenOffice configurations folder to your desktop, to keep it as backup).

After this, restart OpenOffice.org and check if it works.

---

### Post by smiggs on 2006-10-04
thanks for the suggestion but I get no joy Open Office pauses for a minute presumably to recreate the options folders but I get the same error message in the console.

---

