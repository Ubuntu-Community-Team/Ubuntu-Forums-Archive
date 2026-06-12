---
title: "Open Office crashes on startup in Feisty"
date: 2007-05-01
forum: General Help
---

### Post by dejavu_01 on 2007-05-01
Hello, I'm using Ubuntu Feisty but I'm unlucky to find that OOo, one of my critical apps crashed on splash screen.  One the progress bar on the splash screen went up to about 40 percent then poof, I'm back to empty desktop.  I try launching OOo by issuing soffice command in the terminal and this is what I got.   Do you see anything out of ordinary?   I installed Ubuntu on a somewhat middle of the road AMD desktop that runs Ubuntu snappy enought (AMD sempron2200  512ram   ATI 9600),   Any help would be appreciated.

vatin@vatin-desktop:~$ soffice
*** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x080d0388 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6cfe7cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6d01e30]
/usr/lib/openoffice/program/libuno_sal.so.3(rtl_freeMemory+0x1d)[0xb73500bd]
/usr/lib/openoffice/program/soffice.bin[0x809192e]
/usr/lib/openoffice/program/soffice.bin(_ZdlPv+0x26)[0x8091966]
/usr/lib/libscim-1.0.so.8[0xa8fba156]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xa8fbaf77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xa8fb5f05]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so[0xa9055f7b]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x381)[0xb5d07b41]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0xa2f)[0xb5cee1cf]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb5cee5ef]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb5cee7a0]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(_Z23gtk_im_context_scim_newv+0x67)[0xa904ab57]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(im_module_create+0x3c)[0xa905a27c]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_im_module_create+0xb9)[0xb57ebd29]
/usr/lib/libgtk-x11-2.0.so.0[0xb57ec93b]
/usr/lib/libgtk-x11-2.0.so.0[0xb57ecb39]
/usr/lib/libgtk-x11-2.0.so.0(gtk_im_context_set_client_window+0x4e)[0xb57e9f0e]
/usr/lib/libgtk-x11-2.0.so.0[0xb579371f]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb5cf59d9]
/usr/lib/libgobject-2.0.so.0[0xb5ce6e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5ce862b]
/usr/lib/libgobject-2.0.so.0[0xb5cf959a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5cfa627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5cfa7e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xba)[0xb5927bea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x1de)[0xb59281ce]
/usr/lib/libgtk-x11-2.0.so.0(gtk_fixed_put+0xd3)[0xb57c0ec3]
/usr/lib/libgtk-x11-2.0.so.0[0xb57c0f08]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x59)[0xb5cf4ee9]
/usr/lib/libgobject-2.0.so.0[0xb5ce6e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5ce862b]
/usr/lib/libgobject-2.0.so.0[0xb5cf959a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5cfa627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5cfa7e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_add+0x12c)[0xb57771bc]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a542bd]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a56043]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a60abd]
/usr/lib/openoffice/program/libvcl680li.so[0xb7eabff5]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e3909b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11ModalDialogC2EP6WindowRK5ResId+0x67)[0xb7e39ac7]
/usr/lib/openoffice/program/libsvt680li.so(_ZN12WizardDialogC2EP6WindowRK5ResIdhs+0x3e)[0xb790799e]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt14OWizardMachineC2EP6WindowRK5ResIdmhhs+0x4a)[0xb78d91da]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt13RoadmapWizardC2EP6WindowRK5ResIdmS5_h+0x4f)[0xb78d655f]
/usr/lib/openoffice/program/libspl680li.so[0xaa66f926]
/usr/lib/openoffice/program/libspl680li.so[0xaa666024]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0xd59)[0x806bc39]
/usr/lib/openoffice/program/libvcl680li.so[0xb7cb9c3c]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7cb9d45]
/usr/lib/openoffice/program/soffice.bin(main+0x65)[0x805ff85]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb6cacebc]
/usr/lib/openoffice/program/soffice.bin(__gxx_personality_v0+0x249)[0x805fe11]
======= Memory map: ========
08048000-0809c000 r-xp 00000000 03:01 193276     /usr/lib/openoffice/program/soffice.bin
0809c000-0809e000 rw-p 00053000 03:01 193276     /usr/lib/openoffice/program/soffice.bin
0809e000-08363000 rw-p 0809e000 00:00 0          [heap]
a8e00000-a8e21000 rw-p a8e00000 00:00 0 
a8e21000-a8f00000 ---p a8e21000 00:00 0 
a8f52000-a9026000 r-xp 00000000 03:01 48710      /usr/lib/libscim-1.0.so.8.1.0
a9026000-a9034000 rw-p 000d4000 03:01 48710      /usr/lib/libscim-1.0.so.8.1.0
a903e000-a905f000 r-xp 00000000 03:01 242290     /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
a905f000-a9060000 rw-p 00021000 03:01 242290     /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
a9060000-a90c0000 rw-s 00000000 00:08 2031634    /SYSV00000000 (deleted)
a90c0000-a9100000 rw-p a90c0000 00:00 0 
a9100000-a910e000 r-xp 00000000 03:01 258518     /usr/lib/openoffice/program/libgcc3_uno.so
a910e000-a910f000 rw-p 0000e000 03:01 258518     /usr/lib/openoffice/program/libgcc3_uno.so
a910f000-a93f3000 r-xp 00000000 03:01 258515     /usr/lib/openoffice/program/libfwk680li.so
a93f3000-a9403000 rw-p 002e3000 03:01 258515     /usr/lib/openoffice/program/libfwk680li.so
a9403000-a9404000 rw-p a9403000 00:00 0 
a9404000-a949f000 r-xp 00000000 03:01 193205     /usr/lib/openoffice/program/libxcr680li.so
a949f000-a94a4000 rw-p 0009a000 03:01 193205     /usr/lib/openoffice/program/libxcr680li.so
a94a4000-a9607000 r-xp 00000000 03:01 258583     /usr/lib/openoffice/program/libsb680li.so
a9607000-a9618000 rw-p 00163000 03:01 258583     /usr/lib/openoffice/program/libsb680li.so
a9618000-a9619000 rw-p a9618000 00:00 0 
a9619000-a96b3000 r-xp 00000000 03:01 258513     /usr/lib/openoffice/program/libfwe680li.so
a96b3000-a96b7000 rw-p 0009a000 03:01 258513     /usr/lib/openoffice/program/libfwe680li.so
a96b7000-a9a61000 r-xp 00000000 03:01 193157     /usr/lib/openoffice/program/libsfx680li.so
a9a61000-a9a7a000 rw-p 003a9000 03:01 193157     /usr/lib/openoffice/program/libsfx680li.so
a9a7a000-a9a7b000 rw-p a9a7a000 00:00 0 
a9a7b000-a9ad6000 r-xp 00000000 03:01 193186     /usr/lib/openoffice/program/libucpfile1.so
a9ad6000-a9ad9000 rw-p 0005a000 03:01 193186     /usr/lib/openoffice/program/libucpfile1.so
a9ad9000-a9b0f000 r-xp 00000000 03:01 418614     /lib/libsepol.so.1
a9b0f000-a9b10000 rw-p 00035000 03:01 418614     /lib/libsepol.so.1
a9b10000-a9b1a000 rw-p a9b10000 00:00 0 
a9b1a000-a9b1d000 r-xp 00000000 03:01 48415      /usr/lib/libgpg-error.so.0.3.0
a9b1d000-a9b1e000 rw-p 00002000 03:01 48415      /usr/lib/libgpg-error.so.0.3.0
a9b1e000-a9b6d000 r-xp 00000000 03:01 48303      /usr/lib/libgcrypt.so.11.2.2
a9b6d000-a9b6f000 rw-p 0004e000 03:01 48303      /usr/lib/libgcrypt.so.11.2.2
a9b6f000-a9b83000 r-xp 00000000 03:01 48759      /usr/lib/libtasn1.so.3.0.6
a9b83000-a9b84000 rw-p 00013000 03:01 48759      /usr/lib/libtasn1.so.3.0.6
a9b84000-a9b86000 r-xp 00000000 03:01 451697     /lib/tls/i686/cmov/libutil-2.5.so
a9b86000-a9b88000 rw-p 00001000 03:01 451697     /lib/tls/i686/cmov/libutil-2.5.so
a9b88000-a9b9c000 r-xp 00000000 03:01 418613     /lib/libselinux.so.1
a9b9c000-a9b9e000 rw-p 00013000 03:01 418613     /lib/libselinux.so.1
a9b9e000-a9bad000 r-xp 00000000 03:01 451691     /lib/tls/i686/cmov/libresolv-2.5.so
a9bad000-a9baf000 rw-p 0000f000 03:01 451691     /lib/tls/i686/cmov/libresolv-2.5.so
a9baf000-a9bb1000 rw-p a9baf000 00:00 0 
a9bb1000-a9bbf000 r-xp 00000000 03:01 210601     /usr/lib/libavahi-client.so.3.2.2
a9bbf000-a9bc0000 rw-p 0000e000 03:01 210601     /usr/lib/libavahi-client.so.3.2.2
a9bc0000-a9bca000 r-xp 00000000 03:01 210603     /usr/lib/libavahi-common.so.3.4.3
a9bca000-a9bcb000 rw-p 00009000 03:01 210603     /usr/lib/libavahi-common.so.3.4.3
a9bcb000-a9bcd000 r-xp 00000000 03:01 210607     /usr/lib/libavahi-glib.so.1.0.1
a9bcd000-a9bce000 rw-p 00001000 03:01 210607     /usr/lib/libavahi-glib.so.1.0.1
a9bce000-a9c38000 r-xp 00000000 03:01 48411      /usr/lib/libgnutls.so.13.0.9
a9c38000-a9c3e000 rw-p 0006a000 03:01 48411      /usr/lib/libgnutls.so.13.0.9
a9c3e000-a9c94000 r-xp 00000000 03:01 48403      /usr/lib/libgnomevfs-2.so.0.1800.1
a9c94000-a9c97000 rw-p 00055000 03:01 48403      /usr/lib/libgnomevfs-2.so.0.1800.1
a9c97000-a9c99000 r-xp 00000000 03:01 48714      /usr/lib/libscim-x11utils-1.0.so.8.1.0
a9c99000-a9c9a000 rw-p 00001000 03:01 48714      /usr/lib/libscim-x11utils-1.0.so.8.1.0
a9c9a000-a9ca0000 r-xp 00000000 03:01 258540     /usr/lib/openoffice/program/libj680li_g.so
a9ca0000-a9ca1000 rw-p 00006000 03:01 258540     /usr/lib/openoffice/program/libj680li_g.so
a9ca1000-a9cc5000 r-xp 00000000 03:01 193293     /usr/lib/openoffice/program/ucpgvfs1.uno.so
a9cc5000-a9cc7000 rw-p 00023000 03:01 193293     /usr/lib/openoffice/program/ucpgvfs1.uno.so
a9cc7000-a9d06000 r-xp 00000000 03:01 193182     /usr/lib/openoffice/program/libucb1.so
a9d06000-a9d09000 rw-p 0003e000 03:01 193182     /usr/lib/openoffice/program/libucb1.so
a9d09000-a9d0a000 ---p a9d09000 00:00 0 
a9d0a000-aa50a000 rwxp a9d0a000 00:00 0 
aa50a000-aa567000 rw-p aa50a000 00:00 0 
aa567000-aa577000 r-xp 00000000 03:01 258508     /usr/lib/openoffice/program/libfileacc.so
aa577000-aa578000 rw-p 00010000 03:01 258508     /usr/lib/openoffice/program/libfileacc.so
aa578000-aa5b2000 r-xp 00000000 03:01 258514     /usr/lib/openoffice/program/libfwi680li.so
aa5b2000-aa5b4000 rw-p 0003a000 03:01 258514     /usr/lib/openoffice/program/libfwi680li.so
aa5b4000-aa5d7000 r-xp 00000000 03:01 258516     /usr/lib/openoffice/program/libfwl680li.so
aa5d7000-aa5d8000 rw-p 00023000 03:01 258516     /usr/lib/openoffice/program/libfwl680li.so
aa5d8000-aa635000 r-xp 00000000 03:01 258565     /usr/lib/openoffice/program/libpackage2.so
aa635000-aa638000 rw-p 0005d000 03:01 258565     /usr/lib/openoffice/program/libpackage2.so
aa638000-aa654000 r-xp 00000000 03:01 242268     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
aa654000-aa655000 rw-p 0001b000 03:01 242268     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
aa655000-aa687000 r-xp 00000000 03:01 193164     /usr/lib/openoffice/program/libspl680li.so
aa687000-aa689000 rw-p 00032000 03:01 193164     /usr/lib/openoffice/program/libspl680li.so
aa689000-aa68a000 ---p aa689000 00:00 0 
aa68a000-aae8a000 rwxp aa68a000 00:00 0 
aae8a000-aae9c000 r-xp 00000000 03:01 193302     /usr/lib/openoffice/program/uriproc.uno.so
aae9c000-aae9e000 rw-p 00011000 03:01 193302     /usr/lib/openoffice/program/uriproc.uno.so
aae9e000-aae9f000 ---p aae9e000 00:00 0 
aae9f000-ab69f000 rwxp aae9f000 00:00 0 
ab69f000-ab6bb000 r-xp 00000000 03:01 193258     /usr/lib/openoffice/program/sax.uno.so
ab6bb000-ab6bc000 rw-p 0001c000 03:01 193258     /usr/lib/openoffice/program/sax.uno.so
ab6bc000-ab6c6000 r-xp 00000000 03:01 258417     /usr/lib/openoffice/program/behelper.uno.so
ab6c6000-ab6c7000 rw-p 00009000 03:01 258417     /usr/lib/openoffice/program/behelper.uno.so
ab6c7000-ab710000 r-xp 00000000 03:01 210504     /usr/lib/libORBit-2.so.0.1.0
ab710000-ab71a000 rw-p 00048000 03:01 210504     /usr/lib/libORBit-2.so.0.1.0
ab71a000-ab749000 r-xp 00000000 03:01 48301      /usr/lib/libgconf-2.so.4.1.2
ab749000-ab74c000 rw-p 0002e000 03:01 48301      /usr/lib/libgconf-2.so.4.1.2
ab74d000-ab755000 r-xp 00000000 03:01 193221     /usr/lib/openoffice/program/localebe1.uno.so
ab755000-ab756000 rw-p 00008000 03:01 193221     /usr/lib/openoffice/program/localebe1.uno.so
ab756000-ab765000 r-xp 00000000 03:01 258437     /usr/lib/openoffice/program/gconfbe1.uno.so
ab765000-ab766000 rw-p 0000f000 03:01 258437     /usr/lib/openoffice/program/gconfbe1.uno.so
ab766000-ab76a000 r-xp 00000000 03:01 258431     /usr/lib/openoffice/program/desktopbe1.uno.so
ab76a000-ab76b000 rw-p 00003000 03:01 258431     /usr/lib/openoffice/program/desktopbe1.uno.so
ab76b000-ab777000 r-xp 00000000 03:01 193285     /usr/lib/openoffice/program/sysmgr1.uno.so
ab777000-ab778000 rw-p 0000c000 03:01 193285     /usr/lib/openoffice/program/sysmgr1.uno.so
ab778000-ab780000 r-xp 00000000 03:01 193289     /usr/lib/openoffice/program/typeconverter.uno.so
ab780000-ab781000 rw-p 00008000 03:01 193289     /usr/lib/openoffice/program/typeconverter.uno.so
ab781000-ab995000 r-xp 00000000 03:01 258426     /usr/lib/openoffice/program/configmgr2.uno.so
ab995000-ab9a9000 rw-p 00213000 03:01 258426     /usr/lib/openoffice/program/configmgr2.uno.so
ab9a9000-ab9e2000 r-xp 00000000 03:01 193253     /usr/lib/openoffice/program/regtypeprov.uno.so
ab9e2000-ab9e6000 rw-p 00038000 03:01 193253     /usr/lib/openoffice/program/regtypeprov.uno.so
ab9e6000-abbee000 r--s 00000000 03:01 193266     /usr/lib/openoffice/program/services.rdb
abbee000-abf46000 r--s 00000000 03:01 193291     /usr/lib/openoffice/program/types.rdb
abf46000-abf86000 r--s 00000000 03:01 193230     /usr/lib/openoffice/program/oovbaapi.rdb
abf86000-abfa3000 r-xp 00000000 03:01 193263     /usr/lib/openoffice/program/security.uno.so
abfa3000-abfa5000 rw-p 0001c000 03:01 193263     /usr/lib/openoffice/program/security.uno.so
abfa5000-abfb9000 r-xp 00000000 03:01 258445     /usr/lib/openoffice/program/implreg.uno.so
abfb9000-abfba000 rw-p 00013000 03:01 258445     /usr/lib/openoffice/program/implreg.uno.so
abfba000-abfe2000 r-xp 00000000 03:01 193290     /usr/lib/openoffice/program/typemgr.uno.so
abfe2000-abfe4000 rw-p 00028000 03:01 193290     /usr/lib/openoffice/program/typemgr.uno.so
abfe4000-abff3000 r-xp 00000000 03:01 193226     /usr/lib/openoffice/program/nestedreg.uno.so
abff3000-abff4000 rw-p 0000f000 03:01 193226     /usr/lib/openoffice/program/nestedreg.uno.so
abff4000-ac005000 r-xp 00000000 03:01 193271     /usr/lib/openoffice/program/simplereg.uno.so
ac005000-ac006000 rw-p 00010000 03:01 193271     /usr/lib/openoffice/program/simplereg.uno.so
ac006000-ac00c000 r-xp 00000000 03:01 193270     /usr/lib/openoffice/program/shlibloader.uno.so
ac00c000-ac00d000 rw-p 00005000 03:01 193270     /usr/lib/openoffice/program/shlibloader.uno.so
ac00d000-ac02d000 r-xp 00000000 03:01 193265     /usr/lib/openoffice/program/servicemgr.uno.so
ac02d000-ac02f000 rw-p 0001f000 03:01 193265     /usr/lib/openoffice/program/servicemgr.uno.so
ac02f000-ac04b000 r-xp 00000000 03:01 193167     /usr/lib/openoffice/program/libstore.so.3
ac04b000-ac04c000 rw-p 0001b000 03:01 193167     /usr/lib/openoffice/program/libstore.so.3
ac04c000-ac06e000 r-xp 00000000 03:01 258577     /usr/lib/openoffice/program/libreg.so.3
ac06e000-ac06f000 rw-p 00021000 03:01 258577     /usr/lib/openoffice/program/libreg.so.3
ac06f000-ac080000 r-xp 00000000 03:01 258505     /usr/lib/openoffice/program/libexlink680li.so
ac080000-ac081000 rw-p 00011000 03:01 258505     /usr/lib/openoffice/program/libexlink680li.so
ac081000-ac1c1000 rw-s 0003b000 00:0d 16801      /dev/dri/card0
ac1c1000-ac801000 rw-s 00007000 00:0d 16801      /dev/dri/card0
ac801000-ac901000 rw-s 00006000 00:0d 16801      /dev/dri/card0
ac901000-ac902000 rw-s 00005000 00:0d 16801      /dev/dri/card0
ac902000-ac912000 rw-s 00004000 00:0d 16801      /dev/dri/card0
ac912000-b4912000 rw-s 00003000 00:0d 16801      /dev/dri/card0
b4912000-b49c2000 r-xp 00000000 03:01 48751      /usr/lib/libstdc++.so.5.0.7
b49c2000-b49c7000 rw-p 000af000 03:01 48751      /usr/lib/libstdc++.so.5.0.7
b49c7000-b49cc000 rw-p b49c7000 00:00 0 
b49cc000-b5229000 r-xp 00000000 03:01 225475     /usr/lib/dri/fglrx_dri.so
b5229000-b5273000 rw-p 0085d000 03:01 225475     /usr/lib/dri/fglrx_dri.so
b5273000-b52fd000 rw-p b5273000 00:00 0 
b52fd000-b5395000 r-xp 00000000 03:01 209975     /usr/lib/libGL.so.1.2
b5395000-b539a000 rw-p 00098000 03:01 209975     /usr/lib/libGL.so.1.2
b539a000-b539d000 rw-p b539a000 00:00 0 
b539d000-b53a6000 r-xp 00000000 03:01 451680     /lib/tls/i686/cmov/libnss_files-2.5.so
b53a6000-b53a8000 rw-p 00008000 03:01 451680     /lib/tls/i686/cmov/libnss_files-2.5.so
b53a8000-b53b0000 r-xp 00000000 03:01 451684     /lib/tls/i686/cmov/libnss_nis-2.5.so
b53b0000-b53b2000 rw-p 00007000 03:01 451684     /lib/tls/i686/cmov/libnss_nis-2.5.so
b53b2000-b53b9000 r-xp 00000000 03:01 451676     /lib/tls/i686/cmov/libnss_compat-2.5.so
b53b9000-b53bb000 rw-p 00006000 03:01 451676     /lib/tls/i686/cmov/libnss_compat-2.5.so
b53bb000-b53bc000 rwxp b53bb000 00:00 0 
b53bc000-b53be000 rw-s 00002000 00:0d 16801      /dev/dri/card0
b53be000-b53c5000 rwxp b53be000 00:00 0 
b53c5000-b549c000 r--p 00000000 03:01 243206     /usr/lib/locale/en_US.utf8/LC_COLLATE
b549c000-b54e9000 r-xp 00000000 03:01 210563     /usr/lib/libXt.so.6.0.0
b54e9000-b54ed000 rw-p 0004c000 03:01 210563     /usr/lib/libXt.so.6.0.0
b54ed000-b552f000 r-xp 00000000 03:01 210481     /usr/lib/libFLAC.so.7.0.0
b552f000-b5530000 rw-p 00041000 03:01 210481     /usr/lib/libFLAC.so.7.0.0
b5530000-b5538000 r-xp 00000000 03:01 48749      /usr/lib/libstartup-notification-1.so.0.0.0
b5538000-b5539000 rw-p 00007000 03:01 48749      /usr/lib/libstartup-notification-1.so.0.0.0
b5539000-b554e000 r-xp 00000000 03:01 210597     /usr/lib/libaudio.so.2.4
b554e000-b554f000 rw-p 00015000 03:01 210597     /usr/lib/libaudio.so.2.4
b554f000-b5555000 r-xp 00000000 03:01 48677      /usr/lib/libportaudio.so.0.0.18
b5555000-b5556000 rw-p 00005000 03:01 48677      /usr/lib/libportaudio.so.0.0.18
b5556000-b55ad000 r-xp 00000000 03:01 48733      /usr/lib/libsndfile.so.1.0.16
b55ad000-b55af000 rw-p 00056000 03:01 48733      /usr/lib/libsndfile.so.1.0.16
b55af000-b55b3000 rw-p b55af000 00:00 0 
b55b3000-b55c6000 r-xp 00000000 03:01 451674     /lib/tls/i686/cmov/libnsl-2.5.so
b55c6000-b55c8000 rw-p 00012000 03:01 451674     /lib/tls/i686/cmov/libnsl-2.5.so
b55c8000-b55ca000 rw-p b55c8000 00:00 0 
b55ca000-b5649000 r-xp 00000000 03:01 193201     /usr/lib/openoffice/program/libvclplug_gen680li.so
b5649000-b5651000 rw-p 0007f000 03:01 193201     /usr/lib/openoffice/program/libvclplug_gen680li.so
b5651000-b5652000 rw-p b5651000 00:00 0 
b5652000-b5683000 r-xp 00000000 03:01 210660     /usr/lib/libdbus-1.so.3.2.0
b5683000-b5684000 rw-p 00031000 03:01 210660     /usr/lib/libdbus-1.so.3.2.0
b5684000-b569e000 r-xp 00000000 03:01 210662     /usr/lib/libdbus-glib-1.so.2.1.0
b569e000-b569f000 rw-p 0001a000 03:01 210662     /usr/lib/libdbus-glib-1.so.2.1.0
b569f000-b56a6000 r-xp 00000000 03:01 451693     /lib/tls/i686/cmov/librt-2.5.so
b56a6000-b56a8000 rw-p 00006000 03:01 451693     /lib/tls/i686/cmov/librt-2.5.so
b56a8000-b56ac000 r-xp 00000000 03:01 48467      /usr/lib/libgthread-2.0.so.0.1200.11
b56ac000-b56ad000 rw-p 00003000 03:01 48467      /usr/lib/libgthread-2.0.so.0.1200.11
b56ad000-b56c6000 r-xp 00000000 03:01 210593     /usr/lib/libatk-1.0.so.0.1809.1
b56c6000-b56c8000 rw-p 00018000 03:01 210593     /usr/lib/libatk-1.0.so.0.1809.1
b56c8000-b5a19000 r-xp 00000000 03:01 48470      /usr/lib/libgtk-x11-2.0.so.0.1000.11
b5a19000-b5a1f000 rw-p 00351000 03:01 48470      /usr/lib/libgtk-x11-2.0.so.0.1000.11
b5a1f000-b5a20000 rw-p b5a1f000 00:00 0 
b5a20000-b5a21000 r-xp 00000000 03:01 226492     /usr/lib/gconv/ISO8859-1.so
b5a21000-b5a23000 rw-p 00000000 03:01 226492     /usr/lib/gconv/ISO8859-1.so
b5a23000-b5a24000 r--p 00000000 03:01 243212     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b5a24000-b5a25000 r--p 00000000 03:01 243215     /usr/lib/locale/en_US.utf8/LC_TIME
b5a25000-b5a26000 r--p 00000000 03:01 243210     /usr/lib/locale/en_US.utf8/LC_MONETARY
b5a26000-b5a27000 r--p 00000000 03:01 257607     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b5a27000-b5a28000 r--p 00000000 03:01 243213     /usr/lib/locale/en_US.utf8/LC_PAPER
b5a28000-b5a29000 r--p 00000000 03:01 243211     /usr/lib/locale/en_US.utf8/LC_NAME
b5a29000-b5a2a000 r--p 00000000 03:01 243205     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b5a2a000-b5a75000 r-xp 00000000 03:01 193202     /usr/lib/openoffice/program/libvclplug_gtk680li.so
b5a75000-b5a7b000 rw-p 0004a000 03:01 193202     /usr/lib/openoffice/program/libvclplug_gtk680li.so
b5a7b000-b5ab6000 r--p 00000000 03:01 243207     /usr/lib/locale/en_US.utf8/LC_CTYPE
b5ab6000-b5aba000 rw-p b5ab6000 00:00 0 
b5aba000-b5adc000 r-xp 00000000 03:01 48671      /usr/lib/libpng12.so.0.15.0
b5adc000-b5add000 rw-p 00021000 03:01 48671      /usr/lib/libpng12.so.0.15.0
b5add000-b5b07000 r-xp 00000000 03:01 48650      /usr/lib/libpangoft2-1.0.so.0.1600.2
b5b07000-b5b08000 rw-p 0002a000 03:01 48650      /usr/lib/libpangoft2-1.0.so.0.1600.2
b5b08000-b5b09000 rw-p b5b08000 00:00 0 
b5b09000-b5c20000 r-xp 00000000 03:01 48811      /usr/lib/libxml2.so.2.6.27
b5c20000-b5c26000 rw-p 00116000 03:01 48811      /usr/lib/libxml2.so.2.6.27
b5c26000-b5c44000 r-xp 00000000 03:01 210718     /usr/lib/libexpat.so.1.0.0
b5c44000-b5c46000 rw-p 0001d000 03:01 210718     /usr/lib/libexpat.so.1.0.0
b5c46000-b5cda000 r-xp 00000000 03:01 48359      /usr/lib/libglib-2.0.so.0.1200.11
b5cda000-b5cdb000 rw-p 00093000 03:01 48359      /usr/lib/libglib-2.0.so.0.1200.11
b5cdb000-b5cdd000 r-xp 00000000 03:01 48369      /usr/lib/libgmodule-2.0.so.0.1200.11
b5cdd000-b5cde000 rw-p 00002000 03:01 48369      /usr/lib/libgmodule-2.0.so.0.1200.11
b5cde000-b5d17000 r-xp 00000000 03:01 48413      /usr/lib/libgobject-2.0.so.0.1200.11
b5d17000-b5d18000 rw-p 00039000 03:01 48413      /usr/lib/libgobject-2.0.so.0.1200.11
b5d18000-b5d19000 rw-p b5d18000 00:00 0 
b5d19000-b5d87000 r-xp 00000000 03:01 210626     /usr/lib/libcairo.so.2.11.1
b5d87000-b5d89000 rw-p 0006d000 03:01 210626     /usr/lib/libcairo.so.2.11.1
b5d89000-b5dc5000 r-xp 00000000 03:01 48646      /usr/lib/libpango-1.0.so.0.1600.2
b5dc5000-b5dc7000 rw-p 0003b000 03:01 48646      /usr/lib/libpango-1.0.so.0.1600.2
b5dc7000-b5dcb000 r-xp 00000000 03:01 210539     /usr/lib/libXfixes.so.3.1.0
b5dcb000-b5dcc000 rw-p 00003000 03:01 210539     /usr/lib/libXfixes.so.3.1.0
b5dcc000-b5dd4000 r-xp 00000000 03:01 210529     /usr/lib/libXcursor.so.1.0.2
b5dd4000-b5dd5000 rw-p 00007000 03:01 210529     /usr/lib/libXcursor.so.1.0.2
b5dd5000-b5dda000 r-xp 00000000 03:01 210557     /usr/lib/libXrandr.so.2.1.0
b5dda000-b5ddb000 rw-p 00005000 03:01 210557     /usr/lib/libXrandr.so.2.1.0
b5ddb000-b5de2000 r-xp 00000000 03:01 210545     /usr/lib/libXi.so.6.0.0
b5de2000-b5de3000 rw-p 00006000 03:01 210545     /usr/lib/libXi.so.6.0.0
b5de3000-b5de4000 rw-p b5de3000 00:00 0 
b5de4000-b5de6000 r-xp 00000000 03:01 210547     /usr/lib/libXinerama.so.1.0.0
b5de6000-b5de7000 rw-p 00001000 03:01 210547     /usr/lib/libXinerama.so.1.0.0
b5de7000-b5dee000 r-xp 00000000 03:01 210559     /usr/lib/libXrender.so.1.3.0
b5dee000-b5def000 rw-p 00006000 03:01 210559     /usr/lib/libXrender.so.1.3.0
b5def000-b5df6000 r-xp 00000000 03:01 48648      /usr/lib/libpangocairo-1.0.so.0.1600.2
b5df6000-b5df7000 rw-p 00007000 03:01 48648      /usr/lib/libpangocairo-1.0.so.0.1600.2
b5df7000-b5e0d000 r-xp 00000000 03:01 48323      /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b5e0d000-b5e0e000 rw-p 00015000 03:01 48323      /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b5e0e000-b5e91000 r-xp 00000000 03:01 48321      /usr/lib/libgdk-x11-2.0.so.0.1000.11
b5e91000-b5e94000 rw-p 00083000 03:01 48321      /usr/lib/libgdk-x11-2.0.so.0.1000.11
b5e94000-b5e96000 r-xp 00000000 03:01 48658      /usr/lib/libpaper.so.1.1.2
b5e96000-b5e97000 rw-p 00001000 03:01 48658      /usr/lib/libpaper.so.1.1.2
b5e97000-b5e98000 rw-p b5e97000 00:00 0 
b5e98000-b6847000 r--p 00000000 03:01 48511      /usr/lib/libicudata.so.36.0
b6847000-b6848000 rw-p 009ae000 03:01 48511      /usr/lib/libicudata.so.36.0
b6848000-b684c000 r-xp 00000000 03:01 210533     /usr/lib/libXdmcp.so.6.0.0
b684c000-b684d000 rw-p 00003000 03:01 210533     /usr/lib/libXdmcp.so.6.0.0
b684d000-b684f000 r-xp 00000000 03:01 210522     /usr/lib/libXau.so.6.0.0
b684f000-b6850000 rw-p 00001000 03:01 210522     /usr/lib/libXau.so.6.0.0
b6850000-b6855000 r-xp 00000000 03:01 451667     /lib/tls/i686/cmov/libcrypt-2.5.so
b6855000-b6857000 rw-p 00004000 03:01 451667     /lib/tls/i686/cmov/libcrypt-2.5.so
b6857000-b687f000 rw-p b6857000 00:00 0 
b687f000-b6886000 r-xp 00000000 03:01 418594     /lib/libpam.so.0.79
b6886000-b6887000 rw-p 00007000 03:01 418594     /lib/libpam.so.0.79
b6887000-b688b000 r-xp 00000000 03:01 193193     /usr/lib/openoffice/program/libuno_salhelpergcc3.so.3
b688b000-b688c000 rw-p 00003000 03:01 193193     /usr/lib/openoffice/program/libuno_salhelpergcc3.so.3
b688c000-b68a3000 r-xp 00000000 03:01 258548     /usr/lib/openoffice/program/libjvmfwk.so.3
b68a3000-b68a4000 rw-p 00017000 03:01 258548     /usr/lib/openoffice/program/libjvmfwk.so.3
b68a4000-b68c2000 r-xp 00000000 03:01 48540      /usr/lib/libjpeg.so.62.0.0
b68c2000-b68c3000 rw-p 0001d000 03:01 48540      /usr/lib/libjpeg.so.62.0.0
b68c3000-b68c4000 rw-p b68c3000 00:00 0 
b68c4000-b68e7000 r-xp 00000000 03:01 210724     /usr/lib/libfontconfig.so.1.2.0
b68e7000-b68ef000 rw-p 00023000 03:01 210724     /usr/lib/libfontconfig.so.1.2.0
b68ef000-b6902000 r-xp 00000000 03:01 48817      /usr/lib/libz.so.1.2.3
b6902000-b6903000 rw-p 00012000 03:01 48817      /usr/lib/libz.so.1.2.3
b6903000-b696b000 r-xp 00000000 03:01 210734     /usr/lib/libfreetype.so.6.3.10
b696b000-b696e000 rw-p 00068000 03:01 210734     /usr/lib/libfreetype.so.6.3.10
b696e000-b6972000 r-xp 00000000 03:01 258547     /usr/lib/openoffice/program/libjvmaccessgcc3.so.3
b6972000-b6973000 rw-p 00003000 03:01 258547     /usr/lib/openoffice/program/libjvmaccessgcc3.so.3
b6973000-b6a18000 r-xp 00000000 03:01 258573     /usr/lib/openoffice/program/libpsp680li.so
b6a18000-b6a61000 rw-p 000a5000 03:01 258573     /usr/lib/openoffice/program/libpsp680li.so
b6a61000-b6a63000 rw-p b6a61000 00:00 0 
b6a63000-b6aa2000 r-xp 00000000 03:01 48517      /usr/lib/libicule.so.36.0
b6aa2000-b6aa4000 rw-p 0003f000 03:01 48517      /usr/lib/libicule.so.36.0
b6aa4000-b6aa5000 rw-p b6aa4000 00:00 0 
b6aa5000-b6bbb000 r-xp 00000000 03:01 48523      /usr/lib/libicuuc.so.36.0
b6bbb000-b6bc2000 rw-p 00116000 03:01 48523      /usr/lib/libicuuc.so.36.0
b6bc2000-b6bc4000 rw-p b6bc2000 00:00 0 
b6bc4000-b6c3a000 r-xp 00000000 03:01 258464     /usr/lib/openoffice/program/libbasegfx680li.so
b6c3a000-b6c3b000 rw-p 00076000 03:01 258464     /usr/lib/openoffice/program/libbasegfx680li.so
b6c3b000-b6c94000 r-xp 00000000 03:01 193161     /usr/lib/openoffice/program/libsot680li.so
b6c94000-b6c97000 rw-p 00059000 03:01 193161     /usr/lib/openoffice/program/libsot680li.so
b6c97000-b6dd2000 r-xp 00000000 03:01 451663     /lib/tls/i686/cmov/libc-2.5.so
b6dd2000-b6dd3000 r--p 0013b000 03:01 451663     /lib/tls/i686/cmov/libc-2.5.so
b6dd3000-b6dd5000 rw-p 0013c000 03:01 451663     /lib/tls/i686/cmov/libc-2.5.so
b6dd5000-b6dd8000 rw-p b6dd5000 00:00 0 
b6dd8000-b6de3000 r-xp 00000000 03:01 418560     /lib/libgcc_s.so.1
b6de3000-b6de4000 rw-p 0000a000 03:01 418560     /lib/libgcc_s.so.1
b6de4000-b6de5000 rw-p b6de4000 00:00 0 
b6de5000-b6e0a000 r-xp 00000000 03:01 451671     /lib/tls/i686/cmov/libm-2.5.so
b6e0a000-b6e0c000 rw-p 00024000 03:01 451671     /lib/tls/i686/cmov/libm-2.5.so
b6e0c000-b6eeb000 r-xp 00000000 03:01 48753      /usr/lib/libstdc++.so.6.0.8
b6eeb000-b6eee000 r--p 000de000 03:01 48753      /usr/lib/libstdc++.so.6.0.8
b6eee000-b6ef0000 rw-p 000e1000 03:01 48753      /usr/lib/libstdc++.so.6.0.8
b6ef0000-b6ef6000 rw-p b6ef0000 00:00 0 
b6ef6000-b6f88000 r-xp 00000000 03:01 48755      /usr/lib/libstlport.so.5.1.0
b6f88000-b6f8c000 rw-p 00091000 03:01 48755      /usr/lib/libstlport.so.5.1.0
b6f8c000-b6f90000 rw-p b6f8c000 00:00 0 
b6f90000-b6fa3000 r-xp 00000000 03:01 451689     /lib/tls/i686/cmov/libpthread-2.5.so
b6fa3000-b6fa5000 rw-p 00013000 03:01 451689     /lib/tls/i686/cmov/libpthread-2.5.so
b6fa5000-b6fa7000 rw-p b6fa5000 00:00 0 
b6fa7000-b6fa9000 r-xp 00000000 03:01 451669     /lib/tls/i686/cmov/libdl-2.5.so
b6fa9000-b6fab000 rw-p 00001000 03:01 451669     /lib/tls/i686/cmov/libdl-2.5.so
b6fab000-b7098000 r-xp 00000000 03:01 210516     /usr/lib/libX11.so.6.2.0
b7098000-b709c000 rw-p 000ed000 03:01 210516     /usr/lib/libX11.so.6.2.0
b709c000-b709d000 rw-p b709c000 00:00 0 
b709d000-b70b2000 r-xp 00000000 03:01 210494     /usr/lib/libICE.so.6.3.0
b70b2000-b70b4000 rw-p 00014000 03:01 210494     /usr/lib/libICE.so.6.3.0
b70b4000-b70b5000 rw-p b70b4000 00:00 0 
b70b5000-b70bd000 r-xp 00000000 03:01 210512     /usr/lib/libSM.so.6.0.0
b70bd000-b70be000 rw-p 00007000 03:01 210512     /usr/lib/libSM.so.6.0.0
b70be000-b70cb000 r-xp 00000000 03:01 210537     /usr/lib/libXext.so.6.4.0
b70cb000-b70cc000 rw-p 0000d000 03:01 210537     /usr/lib/libXext.so.6.4.0
b70cc000-b70cd000 r--p 00000000 03:01 243214     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b70cd000-b70ce000 r--p 00000000 03:01 243209     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b70ce000-b70cf000 r--p 00000000 03:01 243208     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b70cf000-b70d6000 r--s 00000000 03:01 226545     /usr/lib/gconv/gconv-modules.cache
b70d6000-b7307000 r-xp 00000000 03:01 193179     /usr/lib/openoffice/program/libtk680li.so
b7307000-b732f000 rw-p 00231000 03:01 193179     /usr/lib/openoffice/program/libtk680li.so
b732f000-b7331000 rw-p b732f000 00:00 0 
b7331000-b737e000 r-xp 00000000 03:01 193192     /usr/lib/openoffice/program/libuno_sal.so.3
b737e000-b7381000 rw-p 0004c000 03:01 193192     /usr/lib/openoffice/program/libuno_sal.so.3
b7381000-b7383000 rw-p b7381000 00:00 0 
b7383000-b73b1000 r-xp 00000000 03:01 193190     /usr/lib/openoffice/program/libuno_cppu.so.3
b73b1000-b73b2000 rw-p 0002d000 03:01 193190     /usr/lib/openoffice/program/libuno_cppu.so.3
b73b2000-b73b3000 rw-p b73b2000 00:00 0 
b73b3000-b741f000 r-xp 00000000 03:01 193191     /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
b741f000-b7422000 rw-p 0006c000 03:01 193191     /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
b7422000-b7444000 r-xp 00000000 03:01 193203     /usr/lib/openoffice/program/libvos3gcc3.so
b7444000-b7446000 rw-p 00022000 03:01 193203     /usr/lib/openoffice/program/libvos3gcc3.so
b7446000-b74c1000 r-xp 00000000 03:01 193183     /usr/lib/openoffice/program/libucbhelper3gcc3.so
b74c1000-b74c5000 rw-p 0007b000 03:01 193183     /usr/lib/openoffice/program/libucbhelper3gcc3.so
b74c5000-b75c1000 r-xp 00000000 03:01 258470     /usr/lib/openoffice/program/libcomphelp4gcc3.so
b75c1000-b75c9000 rw-p 000fc000 03:01 258470     /usr/lib/openoffice/program/libcomphelp4gcc3.so
b75c9000-b75ca000 rw-p b75c9000 00:00 0 
b75ca000-b75ce000 r-xp 00000000 03:01 258524     /usr/lib/openoffice/program/libi18nisolang1gcc3.so
b75ce000-b75cf000 rw-p 00004000 03:01 258524     /usr/lib/openoffice/program/libi18nisolang1gcc3.so
b75cf000-b75d0000 rw-p b75cf000 00:00 0 
b75d0000-b766f000 r-xp 00000000 03:01 193180     /usr/lib/openoffice/program/libtl680li.so
b766f000-b7672000 rw-p 0009e000 03:01 193180     /usr/lib/openoffice/program/libtl680li.so
b7672000-b76ff000 r-xp 00000000 03:01 193197     /usr/lib/openoffice/program/libutl680li.so
b76ff000-b7704000 rw-p 0008c000 03:01 193197     /usr/lib/openoffice/program/libutl680li.so
b7704000-b7ae6000 r-xp 00000000 03:01 193171     /usr/lib/openoffice/program/libsvt680li.so
b7ae6000-b7b0b000 rw-p 003e1000 03:01 193171     /usr/lib/openoffice/program/libsvt680li.so
b7b0b000-b7b0c000 rw-p b7b0b000 00:00 0 
b7b0c000-b7c20000 r-xp 00000000 03:01 193170     /usr/lib/openoffice/program/libsvl680li.so
b7c20000-b7c26000 rw-p 00114000 03:01 193170     /usr/lib/openoffice/program/libsvl680li.so
b7c26000-b7f94000 r-xp 00000000 03:01 193200     /usr/lib/openoffice/program/libvcl680li.so
b7f94000-b7fa8000 rw-p 0036e000 03:01 193200     /usr/lib/openoffice/program/libvcl680li.so
b7fa8000-b7fab000 rw-p b7fa8000 00:00 0 
b7fab000-b7fc4000 r-xp 00000000 03:01 418517     /lib/ld-2.5.so
b7fc4000-b7fc6000 rw-p 00019000 03:01 418517     /lib/ld-2.5.so
bf91f000-bf964000 rwxp bf91f000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
vatin@vatin-desktop:~$

---

### Post by mvaniersel on 2007-05-01
Well, this definitely shouldn't happen. Does this happen each time you start open office? Do you have any out-of-the-ordinary hardware that could be causing this? If the problem persists I recommend going to launchpad.net and filing a bug report.

---

### Post by dejavu_01 on 2007-05-02
it happens every time, exactly like described above. I'll look into filing bug report once I get home. Thanks

---

### Post by dcstar on 2007-05-02
> **dejavu_01 said:**
> it happens every time, exactly like described above. I'll look into filing bug report once I get home. Thanks

There is a known issue with OO and CUPS when opening Spreadsheets, try disabling CUPS (if you have it running) and see if it makes any difference.

---

### Post by dejavu_01 on 2007-05-02
I've tried uncheck CUPs service and HP printing service in System -> admin -> service dialog box. Despite that the crash persist.  I'm heading to launchpad for bug report

---

### Post by brodiepearce on 2007-05-12
I'm having the same problem, get's to 40% progress and poof gone.  In the system monitor ooffice and ooqstart pop up with status "Starting" then dissapear as soon as the progress bar reaches about 40% as described.  Post back here if you get this fixed pleeeease.

*edit*
Here's my soffice output:

```

brodiepearce@ubuntu:~$ soffice
*** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x080d0618 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6d197cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6d1ce30]
/usr/lib/openoffice/program/libuno_sal.so.3(rtl_freeMemory+0x1d)[0xb736c0bd]
/usr/lib/openoffice/program/soffice.bin[0x809192e]
/usr/lib/openoffice/program/soffice.bin(_ZdlPv+0x26)[0x8091966]
/usr/lib/libscim-1.0.so.8[0xa8f79156]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xa8f79f77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xa8f74f05]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so[0xa9015f7b]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x381)[0xb5d22b41]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0xa2f)[0xb5d091cf]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb5d095ef]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb5d097a0]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(_Z23gtk_im_context_scim_newv+0x67)[0xa900ab57]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(im_module_create+0x3c)[0xa901a27c]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_im_module_create+0xb9)[0xb5805d29]
/usr/lib/libgtk-x11-2.0.so.0[0xb580693b]
/usr/lib/libgtk-x11-2.0.so.0[0xb5806b39]
/usr/lib/libgtk-x11-2.0.so.0(gtk_im_context_set_client_window+0x4e)[0xb5803f0e]
/usr/lib/libgtk-x11-2.0.so.0[0xb57ad71f]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb5d109d9]
/usr/lib/libgobject-2.0.so.0[0xb5d01e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5d0362b]
/usr/lib/libgobject-2.0.so.0[0xb5d1459a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5d15627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5d157e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xba)[0xb5941bea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x1de)[0xb59421ce]
/usr/lib/libgtk-x11-2.0.so.0(gtk_fixed_put+0xd3)[0xb57daec3]
/usr/lib/libgtk-x11-2.0.so.0[0xb57daf08]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x59)[0xb5d0fee9]
/usr/lib/libgobject-2.0.so.0[0xb5d01e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5d0362b]
/usr/lib/libgobject-2.0.so.0[0xb5d1459a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5d15627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5d157e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_add+0x12c)[0xb57911bc]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a6f2bd]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a71043]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a7babd]
/usr/lib/openoffice/program/libvcl680li.so[0xb7ec7ff5]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e5509b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11ModalDialogC2EP6WindowRK5ResId+0x67)[0xb7e55ac7]
/usr/lib/openoffice/program/libsvt680li.so(_ZN12WizardDialogC2EP6WindowRK5ResIdhs+0x3e)[0xb792399e]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt14OWizardMachineC2EP6WindowRK5ResIdmhhs+0x4a)[0xb78f51da]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt13RoadmapWizardC2EP6WindowRK5ResIdmS5_h+0x4f)[0xb78f255f]
/usr/lib/openoffice/program/libspl680li.so[0xaa626926]
/usr/lib/openoffice/program/libspl680li.so[0xaa61d024]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0xd59)[0x806bc39]
/usr/lib/openoffice/program/libvcl680li.so[0xb7cd5c3c]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7cd5d45]
/usr/lib/openoffice/program/soffice.bin(main+0x65)[0x805ff85]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb6cc7ebc]
/usr/lib/openoffice/program/soffice.bin(__gxx_personality_v0+0x249)[0x805fe11]
======= Memory map: ========
08048000-0809c000 r-xp 00000000 08:05 115133     /usr/lib/openoffice/program/soffice.bin
0809c000-0809e000 rw-p 00053000 08:05 115133     /usr/lib/openoffice/program/soffice.bin
0809e000-0835f000 rw-p 0809e000 00:00 0          [heap]
a8e00000-a8e21000 rw-p a8e00000 00:00 0 
a8e21000-a8f00000 ---p a8e21000 00:00 0 
a8f11000-a8fe5000 r-xp 00000000 08:05 4218101    /usr/lib/libscim-1.0.so.8.1.0
a8fe5000-a8ff3000 rw-p 000d4000 08:05 4218101    /usr/lib/libscim-1.0.so.8.1.0
a8ffe000-a901f000 r-xp 00000000 08:05 51571      /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
a901f000-a9020000 rw-p 00021000 08:05 51571      /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
a9020000-a9080000 rw-s 00000000 00:08 6455316    /SYSV00000000 (deleted)
a9080000-a90c0000 rw-p a9080000 00:00 0 
a90c0000-a90ce000 r-xp 00000000 08:05 115256     /usr/lib/openoffice/program/libgcc3_uno.so
a90ce000-a90cf000 rw-p 0000e000 08:05 115256     /usr/lib/openoffice/program/libgcc3_uno.so
a90cf000-a93b3000 r-xp 00000000 08:05 115171     /usr/lib/openoffice/program/libfwk680li.so
a93b3000-a93c3000 rw-p 002e3000 08:05 115171     /usr/lib/openoffice/program/libfwk680li.so
a93c3000-a93c4000 rw-p a93c3000 00:00 0 
a93c4000-a945f000 r-xp 00000000 08:05 115211     /usr/lib/openoffice/program/libxcr680li.so
a945f000-a9464000 rw-p 0009a000 08:05 115211     /usr/lib/openoffice/program/libxcr680li.so
a9464000-a95c7000 r-xp 00000000 08:05 115186     /usr/lib/openoffice/program/libsb680li.so
a95c7000-a95d8000 rw-p 00163000 08:05 115186     /usr/lib/openoffice/program/libsb680li.so
a95d8000-a95d9000 rw-p a95d8000 00:00 0 
a95d9000-a9673000 r-xp 00000000 08:05 115169     /usr/lib/openoffice/program/libfwe680li.so
a9673000-a9677000 rw-p 0009a000 08:05 115169     /usr/lib/openoffice/program/libfwe680li.so
a9677000-a9a21000 r-xp 00000000 08:05 115191     /usr/lib/openoffice/program/libsfx680li.so
a9a21000-a9a3a000 rw-p 003a9000 08:05 115191     /usr/lib/openoffice/program/libsfx680li.so
a9a3a000-a9a3b000 rw-p a9a3a000 00:00 0 
a9a3b000-a9a96000 r-xp 00000000 08:05 115313     /usr/lib/openoffice/program/libucpfile1.so
a9a96000-a9a99000 rw-p 0005a000 08:05 115313     /usr/lib/openoffice/program/libucpfile1.so
a9a99000-a9acf000 r-xp 00000000 08:05 671810     /lib/libsepol.so.1
a9acf000-a9ad0000 rw-p 00035000 08:05 671810     /lib/libsepol.so.1
a9ad0000-a9ada000 rw-p a9ad0000 00:00 0 
a9ada000-a9add000 r-xp 00000000 08:05 4213360    /usr/lib/libgpg-error.so.0.3.0
a9add000-a9ade000 rw-p 00002000 08:05 4213360    /usr/lib/libgpg-error.so.0.3.0
a9ade000-a9b2d000 r-xp 00000000 08:05 4213358    /usr/lib/libgcrypt.so.11.2.2
a9b2d000-a9b2f000 rw-p 0004e000 08:05 4213358    /usr/lib/libgcrypt.so.11.2.2
a9b2f000-a9b43000 r-xp 00000000 08:05 4213869    /usr/lib/libtasn1.so.3.0.6
a9b43000-a9b44000 rw-p 00013000 08:05 4213869    /usr/lib/libtasn1.so.3.0.6
a9b44000-a9b46000 r-xp 00000000 08:05 671927     /lib/tls/i686/cmov/libutil-2.5.so
a9b46000-a9b48000 rw-p 00001000 08:05 671927     /lib/tls/i686/cmov/libutil-2.5.so
a9b48000-a9b5c000 r-xp 00000000 08:05 671808     /lib/libselinux.so.1
a9b5c000-a9b5e000 rw-p 00013000 08:05 671808     /lib/libselinux.so.1
a9b5e000-a9b6d000 r-xp 00000000 08:05 671915     /lib/tls/i686/cmov/libresolv-2.5.so
a9b6d000-a9b6f000 rw-p 0000f000 08:05 671915     /lib/tls/i686/cmov/libresolv-2.5.so
a9b6f000-a9b71000 rw-p a9b6f000 00:00 0 
a9b71000-a9b7f000 r-xp 00000000 08:05 4215293    /usr/lib/libavahi-client.so.3.2.2
a9b7f000-a9b80000 rw-p 0000e000 08:05 4215293    /usr/lib/libavahi-client.so.3.2.2
a9b80000-a9b8a000 r-xp 00000000 08:05 4215291    /usr/lib/libavahi-common.so.3.4.3
a9b8a000-a9b8b000 rw-p 00009000 08:05 4215291    /usr/lib/libavahi-common.so.3.4.3
a9b8b000-a9b8d000 r-xp 00000000 08:05 4215295    /usr/lib/libavahi-glib.so.1.0.1
a9b8d000-a9b8e000 rw-p 00001000 08:05 4215295    /usr/lib/libavahi-glib.so.1.0.1
a9b8e000-a9bf8000 r-xp 00000000 08:05 4213296    /usr/lib/libgnutls.so.13.0.9
a9bf8000-a9bfe000 rw-p 0006a000 08:05 4213296    /usr/lib/libgnutls.so.13.0.9
a9bfe000-a9c54000 r-xp 00000000 08:05 4215337    /usr/lib/libgnomevfs-2.so.0.1800.1
a9c54000-a9c57000 rw-p 00055000 08:05 4215337    /usr/lib/libgnomevfs-2.so.0.1800.1
a9c58000-a9c5a000 r-xp 00000000 08:05 4218102    /usr/lib/libscim-x11utils-1.0.so.8.1.0
a9c5a000-a9c5b000 rw-p 00001000 08:05 4218102    /usr/lib/libscim-x11utils-1.0.so.8.1.0
a9c5b000-a9c61000 r-xp 00000000 08:05 115175     /usr/lib/openoffice/program/libj680li_g.so
a9c61000-a9c62000 rw-p 00006000 08:05 115175     /usr/lib/openoffice/program/libj680li_g.so
a9c62000-a9c86000 r-xp 00000000 08:05 115651     /usr/lib/openoffice/program/ucpgvfs1.uno.so
a9c86000-a9c88000 rw-p 00023000 08:05 115651     /usr/lib/openoffice/program/ucpgvfs1.uno.so
a9c88000-a9cc7000 r-xp 00000000 08:05 115309     /usr/lib/openoffice/program/libucb1.so
a9cc7000-a9cca000 rw-p 0003e000 08:05 115309     /usr/lib/openoffice/program/libucb1.so
a9cca000-a9ccb000 ---p a9cca000 00:00 0 
a9ccb000-aa4cb000 rwxp a9ccb000 00:00 0 
aa4cb000-aa528000 rw-p aa4cb000 00:00 0 
aa528000-aa538000 r-xp 00000000 08:05 115251     /usr/lib/openoffice/program/libfileacc.so
aa538000-aa539000 rw-p 00010000 08:05 115251     /usr/lib/openoffice/program/libfileacc.so
aa539000-aa573000 r-xp 00000000 08:05 115170     /usr/lib/openoffice/program/libfwi680li.so
aa573000-aa575000 rw-p 0003a000 08:05 115170     /usr/lib/openoffice/program/libfwi680li.so
aa575000-aa598000 r-xp 00000000 08:05 115172     /usr/lib/openoffice/program/libfwl680li.so
aa598000-aa599000 rw-p 00023000 08:05 115172     /usr/lib/openoffice/program/libfwl680li.so
aa599000-aa5f6000 r-xp 00000000 08:05 115281     /usr/lib/openoffice/program/libpackage2.so
aa5f6000-aa5f9000 rw-p 0005d000 08:05 115281     /usr/lib/openoffice/program/libpackage2.so
aa5f9000-aa60b000 r-xp 00000000 08:05 88363      /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
aa60b000-aa60c000 rw-p 00011000 08:05 88363      /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
aa60c000-aa63e000 r-xp 00000000 08:05 115196     /usr/lib/openoffice/program/libspl680li.so
aa63e000-aa640000 rw-p 00032000 08:05 115196     /usr/lib/openoffice/program/libspl680li.so
aa640000-aa641000 ---p aa640000 00:00 0 
aa641000-aae41000 rwxp aa641000 00:00 0 
aae41000-aae53000 r-xp 00000000 08:05 115319     /usr/lib/openoffice/program/uriproc.uno.so
aae53000-aae55000 rw-p 00011000 08:05 115319     /usr/lib/openoffice/program/uriproc.uno.so
aae55000-aae56000 ---p aae55000 00:00 0 
aae56000-ab656000 rwxp aae56000 00:00 0 
ab656000-ab65e000 r-xp 00000000 08:05 115303     /usr/lib/openoffice/program/localebe1.uno.so
ab65e000-ab65f000 rw-p 00008000 08:05 115303     /usr/lib/openoffice/program/localebe1.uno.so
ab65f000-ab67b000 r-xp 00000000 08:05 115293     /usr/lib/openoffice/program/sax.uno.so
ab67b000-ab67c000 rw-p 0001c000 08:05 115293     /usr/lib/openoffice/program/sax.uno.so
ab67c000-ab6c5000 r-xp 00000000 08:05 4215212    /usr/lib/libORBit-2.so.0.1.0
ab6c5000-ab6cf000 rw-p 00048000 08:05 4215212    /usr/lib/libORBit-2.so.0.1.0
ab6cf000-ab6fe000 r-xp 00000000 08:05 4215231    /usr/lib/libgconf-2.so.4.1.2
ab6fe000-ab701000 rw-p 0002e000 08:05 4215231    /usr/lib/libgconf-2.so.4.1.2
ab701000-ab70b000 r-xp 00000000 08:05 115230     /usr/lib/openoffice/program/behelper.uno.so
ab70b000-ab70c000 rw-p 00009000 08:05 115230     /usr/lib/openoffice/program/behelper.uno.so
ab70c000-ab71b000 r-xp 00000000 08:05 115646     /usr/lib/openoffice/program/gconfbe1.uno.so
ab71b000-ab71c000 rw-p 0000f000 08:05 115646     /usr/lib/openoffice/program/gconfbe1.uno.so
ab71c000-ab720000 r-xp 00000000 08:05 115120     /usr/lib/openoffice/program/desktopbe1.uno.so
ab720000-ab721000 rw-p 00003000 08:05 115120     /usr/lib/openoffice/program/desktopbe1.uno.so
ab721000-ab72d000 r-xp 00000000 08:05 115229     /usr/lib/openoffice/program/sysmgr1.uno.so
ab72d000-ab72e000 rw-p 0000c000 08:05 115229     /usr/lib/openoffice/program/sysmgr1.uno.so
ab72e000-ab736000 r-xp 00000000 08:05 115304     /usr/lib/openoffice/program/typeconverter.uno.so
ab736000-ab737000 rw-p 00008000 08:05 115304     /usr/lib/openoffice/program/typeconverter.uno.so
ab737000-ab94b000 r-xp 00000000 08:05 115228     /usr/lib/openoffice/program/configmgr2.uno.so
ab94b000-ab95f000 rw-p 00213000 08:05 115228     /usr/lib/openoffice/program/configmgr2.uno.so
ab95f000-ab998000 r-xp 00000000 08:05 115287     /usr/lib/openoffice/program/regtypeprov.uno.so
ab998000-ab99c000 rw-p 00038000 08:05 115287     /usr/lib/openoffice/program/regtypeprov.uno.so
ab99c000-abba4000 r--s 00000000 08:05 115137     /usr/lib/openoffice/program/services.rdb
abba4000-abefc000 r--s 00000000 08:05 115136     /usr/lib/openoffice/program/types.rdb
abefc000-abf3c000 r--s 00000000 08:05 115118     /usr/lib/openoffice/program/oovbaapi.rdb
abf3c000-abf59000 r-xp 00000000 08:05 115295     /usr/lib/openoffice/program/security.uno.so
abf59000-abf5b000 rw-p 0001c000 08:05 115295     /usr/lib/openoffice/program/security.uno.so
abf5b000-abf6f000 r-xp 00000000 08:05 115264     /usr/lib/openoffice/program/implreg.uno.so
abf6f000-abf70000 rw-p 00013000 08:05 115264     /usr/lib/openoffice/program/implreg.uno.so
abf70000-abf98000 r-xp 00000000 08:05 115305     /usr/lib/openoffice/program/typemgr.uno.so
abf98000-abf9a000 rw-p 00028000 08:05 115305     /usr/lib/openoffice/program/typemgr.uno.so
abf9a000-abfa9000 r-xp 00000000 08:05 115239     /usr/lib/openoffice/program/nestedreg.uno.so
abfa9000-abfaa000 rw-p 0000f000 08:05 115239     /usr/lib/openoffice/program/nestedreg.uno.so
abfaa000-abfbb000 r-xp 00000000 08:05 115296     /usr/lib/openoffice/program/simplereg.uno.so
abfbb000-abfbc000 rw-p 00010000 08:05 115296     /usr/lib/openoffice/program/simplereg.uno.so
abfbc000-abfdc000 r-xp 00000000 08:05 115297     /usr/lib/openoffice/program/servicemgr.uno.so
abfdc000-abfde000 rw-p 0001f000 08:05 115297     /usr/lib/openoffice/program/servicemgr.uno.so
abfde000-abffa000 r-xp 00000000 08:05 115300     /usr/lib/openoffice/program/libstore.so.3
abffa000-abffb000 rw-p 0001b000 08:05 115300     /usr/lib/openoffice/program/libstore.so.3
abffb000-ac01d000 r-xp 00000000 08:05 115289     /usr/lib/openoffice/program/libreg.so.3
ac01d000-ac01e000 rw-p 00021000 08:05 115289     /usr/lib/openoffice/program/libreg.so.3
ac01e000-ac02f000 r-xp 00000000 08:05 115119     /usr/lib/openoffice/program/libexlink680li.so
ac02f000-ac030000 rw-p 00011000 08:05 115119     /usr/lib/openoffice/program/libexlink680li.so
ac030000-ac1e0000 rw-s 00044000 00:0d 15464      /dev/dri/card0
ac1e0000-ac820000 rw-s 0001f000 00:0d 15464      /dev/dri/card0
ac820000-ac920000 rw-s 0001e000 00:0d 15464      /dev/dri/card0
ac920000-ac921000 rw-s 0001d000 00:0d 15464      /dev/dri/card0
ac921000-ac931000 rw-s 0001c000 00:0d 15464      /dev/dri/card0
ac931000-b4911000 rw-s 0001b000 00:0d 15464      /dev/dri/card0
b4911000-b49c1000 r-xp 00000000 08:05 4218105    /usr/lib/libstdc++.so.5.0.7
b49c1000-b49c6000 rw-p 000af000 08:05 4218105    /usr/lib/libstdc++.so.5.0.7
b49c6000-b49cb000 rw-p b49c6000 00:00 0 
b49cb000-b5228000 r-xp 00000000 08:05 363483     /usr/lib/dri/fglrx_dri.so
b5228000-b5272000 rw-p 0085d000 08:05 363483     /usr/lib/dri/fglrx_dri.so
b5272000-b52fc000 rw-p b5272000 00:00 0 
b52fc000-b5394000 r-xp 00000000 08:05 4218564    /usr/lib/libGL.so.1.2
b5394000-b5399000 rw-p 00098000 08:05 4218564    /usr/lib/libGL.so.1.2
b5399000-b539c000 rw-p b5399000 00:00 0 
b539e000-b53a4000 r-xp 00000000 08:05 115236     /usr/lib/openoffice/program/shlibloader.uno.so
b53a4000-b53a5000 rw-p 00005000 08:05 115236     /usr/lib/openoffice/program/shlibloader.uno.so
b53a5000-b53a7000 rw-s 0001a000 00:0d 15464      /dev/dri/card0
b53a7000-b53b0000 r-xp 00000000 08:05 671906     /lib/tls/i686/cmov/libnss_files-2.5.so
b53b0000-b53b2000 rw-p 00008000 08:05 671906     /lib/tls/i686/cmov/libnss_files-2.5.so
b53b2000-b53ba000 r-xp 00000000 08:05 671909     /lib/tls/i686/cmov/libnss_nis-2.5.so
b53ba000-b53bc000 rw-p 00007000 08:05 671909     /lib/tls/i686/cmov/libnss_nis-2.5.so
b53bc000-b53c3000 r-xp 00000000 08:05 671904     /lib/tls/i686/cmov/libnss_compat-2.5.so
b53c3000-b53c5000 rw-p 00006000 08:05 671904     /lib/tls/i686/cmov/libnss_compat-2.5.so
b53c5000-b53cd000 rwxp b53c5000 00:00 0 
b53cd000-b53ce000 r-xp 00000000 08:05 4213390    /usr/lib/gconv/ISO8859-1.so
b53ce000-b53d0000 rw-p 00000000 08:05 4213390    /usr/lib/gconv/ISO8859-1.so
b53d0000-b53df000 r--p 00000000 08:05 4264601    /usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk20.mo
b53df000-b54b6000 r--p 00000000 08:05 4244608    /usr/lib/locale/en_AU.utf8/LC_COLLATE
b54b6000-b5503000 r-xp 00000000 08:05 4214850    /usr/lib/libXt.so.6.0.0
b5503000-b5507000 rw-p 0004c000 08:05 4214850    /usr/lib/libXt.so.6.0.0
b5507000-b5549000 r-xp 00000000 08:05 4215812    /usr/lib/libFLAC.so.7.0.0
b5549000-b554a000 rw-p 00041000 08:05 4215812    /usr/lib/libFLAC.so.7.0.0
b554a000-b5552000 r-xp 00000000 08:05 4215353    /usr/lib/libstartup-notification-1.so.0.0.0
b5552000-b5553000 rw-p 00007000 08:05 4215353    /usr/lib/libstartup-notification-1.so.0.0.0
b5553000-b5568000 r-xp 00000000 08:05 4216098    /usr/lib/libaudio.so.2.4
b5568000-b5569000 rw-p 00015000 08:05 4216098    /usr/lib/libaudio.so.2.4
b5569000-b556f000 r-xp 00000000 08:05 4216127    /usr/lib/libportaudio.so.0.0.18
b556f000-b5570000 rw-p 00005000 08:05 4216127    /usr/lib/libportaudio.so.0.0.18
b5570000-b55c7000 r-xp 00000000 08:05 4216129    /usr/lib/libsndfile.so.1.0.16
b55c7000-b55c9000 rw-p 00056000 08:05 4216129    /usr/lib/libsndfile.so.1.0.16
b55c9000-b55cd000 rw-p b55c9000 00:00 0 
b55cd000-b55e0000 r-xp 00000000 08:05 671903     /lib/tls/i686/cmov/libnsl-2.5.so
b55e0000-b55e2000 rw-p 00012000 08:05 671903     /lib/tls/i686/cmov/libnsl-2.5.so
b55e2000-b55e4000 rw-p b55e2000 00:00 0 
b55e4000-b5663000 r-xp 00000000 08:05 115184     /usr/lib/openoffice/program/libvclplug_gen680li.so
b5663000-b566b000 rw-p 0007f000 08:05 115184     /usr/lib/openoffice/program/libvclplug_gen680li.so
b566b000-b566c000 rw-p b566b000 00:00 0 
b566c000-b569d000 r-xp 00000000 08:05 4213218    /usr/lib/libdbus-1.so.3.2.0
b569d000-b569e000 rw-p 00031000 08:05 4213218    /usr/lib/libdbus-1.so.3.2.0
b569e000-b56b8000 r-xp 00000000 08:05 4215297    /usr/lib/libdbus-glib-1.so.2.1.0
b56b8000-b56b9000 rw-p 0001a000 08:05 4215297    /usr/lib/libdbus-glib-1.so.2.1.0
b56b9000-b56c0000 r-xp 00000000 08:05 671917     /lib/tls/i686/cmov/librt-2.5.so
b56c0000-b56c2000 rw-p 00006000 08:05 671917     /lib/tls/i686/cmov/librt-2.5.so
b56c2000-b56c6000 r-xp 00000000 08:05 4215201    /usr/lib/libgthread-2.0.so.0.1200.11
b56c6000-b56c7000 rw-p 00003000 08:05 4215201    /usr/lib/libgthread-2.0.so.0.1200.11
b56c7000-b56e0000 r-xp 00000000 08:05 4215206    /usr/lib/libatk-1.0.so.0.1809.1
b56e0000-b56e2000 rw-p 00018000 08:05 4215206    /usr/lib/libatk-1.0.so.0.1809.1
b56e2000-b5a33000 r-xp 00000000 08:05 4215278    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b5a33000-b5a39000 rw-p 00351000 08:05 4215278    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b5a39000-b5a3a000 rw-p b5a39000 00:00 0 
b5a3a000-b5a3f000 r--p 00000000 08:05 4264602    /usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk20-properties.mo
b5a3f000-b5a40000 r--p 00000000 08:05 4244606    /usr/lib/locale/en_AU.utf8/LC_NUMERIC
b5a40000-b5a41000 r--p 00000000 08:05 4244607    /usr/lib/locale/en_AU.utf8/LC_TIME
b5a41000-b5a42000 r--p 00000000 08:05 4244609    /usr/lib/locale/en_AU.utf8/LC_MONETARY
b5a42000-b5a43000 r--p 00000000 08:05 4259842    /usr/lib/locale/en_AU.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b5a43000-b5a44000 r--p 00000000 08:05 4244610    /usr/lib/locale/en_AU.utf8/LC_PAPER
b5a44000-b5a45000 r--p 00000000 08:05 4244611    /usr/lib/locale/en_AU.utf8/LC_NAME
b5a45000-b5a90000 r-xp 00000000 08:05 115650     /usr/lib/openoffice/program/libvclplug_gtk680li.so
b5a90000-b5a96000 rw-p 0004a000 08:05 115650     /usr/lib/openoffice/program/libvclplug_gtk680li.so
b5a96000-b5ad1000 r--p 00000000 08:05 4244605    /usr/lib/locale/en_AU.utf8/LC_CTYPE
b5ad1000-b5ad5000 rw-p b5ad1000 00:00 0 
b5ad5000-b5af7000 r-xp 00000000 08:05 4215015    /usr/lib/libpng12.so.0.15.0
b5af7000-b5af8000 rw-p 00021000 08:05 4215015    /usr/lib/libpng12.so.0.15.0
b5af8000-b5b22000 r-xp 00000000 08:05 4215248    /usr/lib/libpangoft2-1.0.so.0.1600.2
b5b22000-b5b23000 rw-p 0002a000 08:05 4215248    /usr/lib/libpangoft2-1.0.so.0.1600.2
b5b23000-b5b24000 rw-p b5b23000 00:00 0 
b5b24000-b5c3b000 r-xp 00000000 08:05 4215148    /usr/lib/libxml2.so.2.6.27
b5c3b000-b5c41000 rw-p 00116000 08:05 4215148    /usr/lib/libxml2.so.2.6.27
b5c41000-b5c5f000 r-xp 00000000 08:05 4214792    /usr/lib/libexpat.so.1.0.0
b5c5f000-b5c61000 rw-p 0001d000 08:05 4214792    /usr/lib/libexpat.so.1.0.0
b5c61000-b5cf5000 r-xp 00000000 08:05 4215198    /usr/lib/libglib-2.0.so.0.1200.11
b5cf5000-b5cf6000 rw-p 00093000 08:05 4215198    /usr/lib/libglib-2.0.so.0.1200.11
b5cf6000-b5cf8000 r-xp 00000000 08:05 4215200    /usr/lib/libgmodule-2.0.so.0.1200.11
b5cf8000-b5cf9000 rw-p 00002000 08:05 4215200    /usr/lib/libgmodule-2.0.so.0.1200.11
b5cf9000-b5d32000 r-xp 00000000 08:05 4215199    /usr/lib/libgobject-2.0.so.0.1200.11
b5d32000-b5d33000 rw-p 00039000 08:05 4215199    /usr/lib/libgobject-2.0.so.0.1200.11
b5d33000-b5d34000 rw-p b5d33000 00:00 0 
b5d34000-b5da2000 r-xp 00000000 08:05 4215229    /usr/lib/libcairo.so.2.11.1
b5da2000-b5da4000 rw-p 0006d000 08:05 4215229    /usr/lib/libcairo.so.2.11.1
b5da4000-b5de0000 r-xp 00000000 08:05 4215246    /usr/lib/libpango-1.0.so.0.1600.2
b5de0000-b5de2000 rw-p 0003b000 08:05 4215246    /usr/lib/libpango-1.0.so.0.1600.2
b5de2000-b5de6000 r-xp 00000000 08:05 4214790    /usr/lib/libXfixes.so.3.1.0
b5de6000-b5de7000 rw-p 00003000 08:05 4214790    /usr/lib/libXfixes.so.3.1.0
b5de7000-b5def000 r-xp 00000000 08:05 4215017    /usr/lib/libXcursor.so.1.0.2
b5def000-b5df0000 rw-p 00007000 08:05 4215017    /usr/lib/libXcursor.so.1.0.2
b5df0000-b5df5000 r-xp 00000000 08:05 4214939    /usr/lib/libXrandr.so.2.1.0
b5df5000-b5df6000 rw-p 00005000 08:05 4214939    /usr/lib/libXrandr.so.2.1.0
b5df6000-b5dfd000 r-xp 00000000 08:05 4214878    /usr/lib/libXi.so.6.0.0
b5dfd000-b5dfe000 rw-p 00006000 08:05 4214878    /usr/lib/libXi.so.6.0.0
b5dfe000-b5dff000 rw-p b5dfe000 00:00 0 
b5dff000-b5e01000 r-xp 00000000 08:05 4214891    /usr/lib/libXinerama.so.1.0.0
b5e01000-b5e02000 rw-p 00001000 08:05 4214891    /usr/lib/libXinerama.so.1.0.0
b5e02000-b5e09000 r-xp 00000000 08:05 4214842    /usr/lib/libXrender.so.1.3.0
b5e09000-b5e0a000 rw-p 00006000 08:05 4214842    /usr/lib/libXrender.so.1.3.0
b5e0a000-b5e11000 r-xp 00000000 08:05 4215247    /usr/lib/libpangocairo-1.0.so.0.1600.2
b5e11000-b5e12000 rw-p 00007000 08:05 4215247    /usr/lib/libpangocairo-1.0.so.0.1600.2
b5e12000-b5e28000 r-xp 00000000 08:05 4215276    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b5e28000-b5e29000 rw-p 00015000 08:05 4215276    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b5e29000-b5eac000 r-xp 00000000 08:05 4215277    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b5eac000-b5eaf000 rw-p 00083000 08:05 4215277    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b5eaf000-b5eb1000 r-xp 00000000 08:05 4215853    /usr/lib/libpaper.so.1.1.2
b5eb1000-b5eb2000 rw-p 00001000 08:05 4215853    /usr/lib/libpaper.so.1.1.2
b5eb2000-b5eb3000 rw-p b5eb2000 00:00 0 
b5eb3000-b6862000 r--p 00000000 08:05 4216111    /usr/lib/libicudata.so.36.0
b6862000-b6863000 rw-p 009ae000 08:05 4216111    /usr/lib/libicudata.so.36.0
b6863000-b6867000 r-xp 00000000 08:05 4214782    /usr/lib/libXdmcp.so.6.0.0
b6867000-b6868000 rw-p 00003000 08:05 4214782    /usr/lib/libXdmcp.so.6.0.0
b6868000-b686a000 r-xp 00000000 08:05 4214780    /usr/lib/libXau.so.6.0.0
b686a000-b686b000 rw-p 00001000 08:05 4214780    /usr/lib/libXau.so.6.0.0
b686b000-b6870000 r-xp 00000000 08:05 671898     /lib/tls/i686/cmov/libcrypt-2.5.so
b6870000-b6872000 rw-p 00004000 08:05 671898     /lib/tls/i686/cmov/libcrypt-2.5.so
b6872000-b689a000 rw-p b6872000 00:00 0 
b689a000-b68a1000 r-xp 00000000 08:05 671815     /lib/libpam.so.0.79
b68a1000-b68a2000 rw-p 00007000 08:05 671815     /lib/libpam.so.0.79
b68a2000-b68a6000 r-xp 00000000 08:05 115292     /usr/lib/openoffice/program/libuno_salhelpergcc3.so.3
b68a6000-b68a7000 rw-p 00003000 08:05 115292     /usr/lib/openoffice/program/libuno_salhelpergcc3.so.3
b68a7000-b68be000 r-xp 00000000 08:05 115325     /usr/lib/openoffice/program/libjvmfwk.so.3
b68be000-b68bf000 rw-p 00017000 08:05 115325     /usr/lib/openoffice/program/libjvmfwk.so.3
b68bf000-b68dd000 r-xp 00000000 08:05 4215270    /usr/lib/libjpeg.so.62.0.0
b68dd000-b68de000 rw-p 0001d000 08:05 4215270    /usr/lib/libjpeg.so.62.0.0
b68de000-b68df000 rw-p b68de000 00:00 0 
b68df000-b6902000 r-xp 00000000 08:05 4214840    /usr/lib/libfontconfig.so.1.2.0
b6902000-b690a000 rw-p 00023000 08:05 4214840    /usr/lib/libfontconfig.so.1.2.0
b690a000-b691d000 r-xp 00000000 08:05 4212746    /usr/lib/libz.so.1.2.3
b691d000-b691e000 rw-p 00012000 08:05 4212746    /usr/lib/libz.so.1.2.3
b691e000-b6986000 r-xp 00000000 08:05 4214795    /usr/lib/libfreetype.so.6.3.10
b6986000-b6989000 rw-p 00068000 08:05 4214795    /usr/lib/libfreetype.so.6.3.10
b6989000-b698d000 r-xp 00000000 08:05 115274     /usr/lib/openoffice/program/libjvmaccessgcc3.so.3
b698d000-b698e000 rw-p 00003000 08:05 115274     /usr/lib/openoffice/program/libjvmaccessgcc3.so.3
b698e000-b6a33000 r-xp 00000000 08:05 115183     /usr/lib/openoffice/program/libpsp680li.so
b6a33000-b6a7c000 rw-p 000a5000 08:05 115183     /usr/lib/openoffice/program/libpsp680li.so
b6a7c000-b6a7e000 rw-p b6a7c000 00:00 0 
b6a7e000-b6abd000 r-xp 00000000 08:05 4216114    /usr/lib/libicule.so.36.0
b6abd000-b6abf000 rw-p 0003f000 08:05 4216114    /usr/lib/libicule.so.36.0
b6abf000-b6ac0000 rw-p b6abf000 00:00 0 
b6ac0000-b6bd6000 r-xp 00000000 08:05 4216117    /usr/lib/libicuuc.so.36.0
b6bd6000-b6bdd000 rw-p 00116000 08:05 4216117    /usr/lib/libicuuc.so.36.0
b6bdd000-b6bdf000 rw-p b6bdd000 00:00 0 
b6bdf000-b6c55000 r-xp 00000000 08:05 115209     /usr/lib/openoffice/program/libbasegfx680li.so
b6c55000-b6c56000 rw-p 00076000 08:05 115209     /usr/lib/openoffice/program/libbasegfx680li.so
b6c56000-b6caf000 r-xp 00000000 08:05 115193     /usr/lib/openoffice/program/libsot680li.so
b6caf000-b6cb2000 rw-p 00059000 08:05 115193     /usr/lib/openoffice/program/libsot680li.so
b6cb2000-b6ded000 r-xp 00000000 08:05 671896     /lib/tls/i686/cmov/libc-2.5.so
b6ded000-b6dee000 r--p 0013b000 08:05 671896     /lib/tls/i686/cmov/libc-2.5.so
b6dee000-b6df0000 rw-p 0013c000 08:05 671896     /lib/tls/i686/cmov/libc-2.5.so
b6df0000-b6df3000 rw-p b6df0000 00:00 0 
b6df3000-b6dfe000 r-xp 00000000 08:05 671758     /lib/libgcc_s.so.1
b6dfe000-b6dff000 rw-p 0000a000 08:05 671758     /lib/libgcc_s.so.1
b6dff000-b6e00000 rw-p b6dff000 00:00 0 
b6e00000-b6e25000 r-xp 00000000 08:05 671901     /lib/tls/i686/cmov/libm-2.5.so
b6e25000-b6e27000 rw-p 00024000 08:05 671901     /lib/tls/i686/cmov/libm-2.5.so
b6e27000-b6f06000 r-xp 00000000 08:05 4213250    /usr/lib/libstdc++.so.6.0.8
b6f06000-b6f09000 r--p 000de000 08:05 4213250    /usr/lib/libstdc++.so.6.0.8
b6f09000-b6f0b000 rw-p 000e1000 08:05 4213250    /usr/lib/libstdc++.so.6.0.8
b6f0b000-b6f11000 rw-p b6f0b000 00:00 0 
b6f11000-b6fa3000 r-xp 00000000 08:05 4216131    /usr/lib/libstlport.so.5.1.0
b6fa3000-b6fa7000 rw-p 00091000 08:05 4216131    /usr/lib/libstlport.so.5.1.0
b6fa7000-b6fab000 rw-p b6fa7000 00:00 0 
b6fab000-b6fbe000 r-xp 00000000 08:05 671914     /lib/tls/i686/cmov/libpthread-2.5.so
b6fbe000-b6fc0000 rw-p 00013000 08:05 671914     /lib/tls/i686/cmov/libpthread-2.5.so
b6fc0000-b6fc2000 rw-p b6fc0000 00:00 0 
b6fc2000-b6fc4000 r-xp 00000000 08:05 671900     /lib/tls/i686/cmov/libdl-2.5.so
b6fc4000-b6fc6000 rw-p 00001000 08:05 671900     /lib/tls/i686/cmov/libdl-2.5.so
b6fc6000-b70b3000 r-xp 00000000 08:05 4214784    /usr/lib/libX11.so.6.2.0
b70b3000-b70b7000 rw-p 000ed000 08:05 4214784    /usr/lib/libX11.so.6.2.0
b70b7000-b70b8000 rw-p b70b7000 00:00 0 
b70b8000-b70cd000 r-xp 00000000 08:05 4214846    /usr/lib/libICE.so.6.3.0
b70cd000-b70cf000 rw-p 00014000 08:05 4214846    /usr/lib/libICE.so.6.3.0
b70cf000-b70d0000 rw-p b70cf000 00:00 0 
b70d0000-b70d8000 r-xp 00000000 08:05 4214848    /usr/lib/libSM.so.6.0.0
b70d8000-b70d9000 rw-p 00007000 08:05 4214848    /usr/lib/libSM.so.6.0.0
b70d9000-b70e6000 r-xp 00000000 08:05 4214786    /usr/lib/libXext.so.6.4.0
b70e6000-b70e7000 rw-p 0000d000 08:05 4214786    /usr/lib/libXext.so.6.4.0
b70e7000-b70e8000 r--p 00000000 08:05 4244612    /usr/lib/locale/en_AU.utf8/LC_ADDRESS
b70e8000-b70e9000 r--p 00000000 08:05 4244613    /usr/lib/locale/en_AU.utf8/LC_TELEPHONE
b70e9000-b70ea000 r--p 00000000 08:05 4244614    /usr/lib/locale/en_AU.utf8/LC_MEASUREMENT
b70ea000-b70eb000 r--p 00000000 08:05 4244615    /usr/lib/locale/en_AU.utf8/LC_IDENTIFICATION
b70eb000-b70f2000 r--s 00000000 08:05 4212750    /usr/lib/gconv/gconv-modules.cache
b70f2000-b7323000 r-xp 00000000 08:05 115203     /usr/lib/openoffice/program/libtk680li.so
b7323000-b734b000 rw-p 00231000 08:05 115203     /usr/lib/openoffice/program/libtk680li.so
b734b000-b734d000 rw-p b734b000 00:00 0 
b734d000-b739a000 r-xp 00000000 08:05 115291     /usr/lib/openoffice/program/libuno_sal.so.3
b739a000-b739d000 rw-p 0004c000 08:05 115291     /usr/lib/openoffice/program/libuno_sal.so.3
b739d000-b739f000 rw-p b739d000 00:00 0 
b739f000-b73cd000 r-xp 00000000 08:05 115237     /usr/lib/openoffice/program/libuno_cppu.so.3
b73cd000-b73ce000 rw-p 0002d000 08:05 115237     /usr/lib/openoffice/program/libuno_cppu.so.3
b73ce000-b73cf000 rw-p b73ce000 00:00 0 
b73cf000-b743b000 r-xp 00000000 08:05 115238     /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
b743b000-b743e000 rw-p 0006c000 08:05 115238     /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
b743e000-b7460000 r-xp 00000000 08:05 115322     /usr/lib/openoffice/program/libvos3gcc3.so
b7460000-b7462000 rw-p 00022000 08:05 115322     /usr/lib/openoffice/program/libvos3gcc3.so
b7462000-b74dd000 r-xp 00000000 08:05 115310     /usr/lib/openoffice/program/libucbhelper3gcc3.so
b74dd000-b74e1000 rw-p 0007b000 08:05 115310     /usr/lib/openoffice/program/libucbhelper3gcc3.so
b74e1000-b75dd000 r-xp 00000000 08:05 115233     /usr/lib/openoffice/program/libcomphelp4gcc3.so
b75dd000-b75e5000 rw-p 000fc000 08:05 115233     /usr/lib/openoffice/program/libcomphelp4gcc3.so
b75e5000-b75e6000 rw-p b75e5000 00:00 0 
b75e6000-b75ea000 r-xp 00000000 08:05 115261     /usr/lib/openoffice/program/libi18nisolang1gcc3.so
b75ea000-b75eb000 rw-p 00004000 08:05 115261     /usr/lib/openoffice/program/libi18nisolang1gcc3.so
b75eb000-b75ec000 rw-p b75eb000 00:00 0 
b75ec000-b768b000 r-xp 00000000 08:05 115204     /usr/lib/openoffice/program/libtl680li.so
b768b000-b768e000 rw-p 0009e000 08:05 115204     /usr/lib/openoffice/program/libtl680li.so
b768e000-b771b000 r-xp 00000000 08:05 115207     /usr/lib/openoffice/program/libutl680li.so
b771b000-b7720000 rw-p 0008c000 08:05 115207     /usr/lib/openoffice/program/libutl680li.so
b7720000-b7b02000 r-xp 00000000 08:05 115199     /usr/lib/openoffice/program/libsvt680li.so
b7b02000-b7b27000 rw-p 003e1000 08:05 115199     /usr/lib/openoffice/program/libsvt680li.so
b7b27000-b7b28000 rw-p b7b27000 00:00 0 
b7b28000-b7c3c000 r-xp 00000000 08:05 115198     /usr/lib/openoffice/program/libsvl680li.so
b7c3c000-b7c42000 rw-p 00114000 08:05 115198     /usr/lib/openoffice/program/libsvl680li.so
b7c42000-b7fb0000 r-xp 00000000 08:05 115210     /usr/lib/openoffice/program/libvcl680li.so
b7fb0000-b7fc4000 rw-p 0036e000 08:05 115210     /usr/lib/openoffice/program/libvcl680li.so
b7fc4000-b7fc8000 rw-p b7fc4000 00:00 0 
b7fc8000-b7fe1000 r-xp 00000000 08:05 671759     /lib/ld-2.5.so
b7fe1000-b7fe3000 rw-p 00019000 08:05 671759     /lib/ld-2.5.so
bfd96000-bfdda000 rwxp bfd96000 00:00 0          [stack]
bfdda000-bfddd000 rw-p bfdda000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
brodiepearce@ubuntu:~$ 

```

*edit*
OK seeing as vdso is the last thing that occured before it crashes, I tried searching that and came up with a few things:

[LIST=1]
[*][Google search "open office crashes vdso"](http://www.google.com.au/search?hl=en&q=open+office+crashes+vdso&btnG=Google+Search&meta=)
[*][Launchpad Post](https://answers.launchpad.net/ubuntu/+question/5743)
[*]["fglrx just recently went very wrong... broke Open Office?!"](http://ubuntuforums.org/showthread.php?t=185033)
[*][Launchpad Bug Report #110472](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/110472)
[/LIST]

So it seems there might be two ways of fixing it:
[LIST=1]
[*]Disabling 3D acceleration in the driver config (in link No. 2 above), or.. possibly:
[*]Overwriting your current LibGL.so.1.2 file with [This one](http://ubuntuforums.org/showpost.php?p=1071197&postcount=6) (In link No. 3 above)
[/LIST]

*edit*

OK I can confirm that enabling composite in etc/X11/xorg.conf and thus disabling 3D acceleration fixes this problem:

```

brodiepearce@ubuntu:~$ soffice
brodiepearce@ubuntu:~$ 

```

No errors! :D

This is still a very poor temporary fix though, having to disable 3D acceleration is unacceptable so I hope there's a better, more permanent fix for this.  Perhaps even rolling back the fglrx driver would help.

---

### Post by brodiepearce on 2007-06-12
Do you happen to use SCIM (like me) as well by any chance?  Apparently one of the causes of this bug is a combination of SCIM, OpenGL and fglrx, and has been a long running problem since Dapper. :O

[Launchpad bug report](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/80551) and workaround.

*edit*
OK the above workaround does not work for me.  I found out though from the bug report, that you can still use oOo with 3D acceleration enabled if you set it to start without OpenGL:

```

SAL_NOOPENGL=true ooffice

```

Enter that in terminal and it starts fine on my machine, add -writer etc. to the end for the particular app E.g.:

```

SAL_NOOPENGL=true ooffice -writer

```

I can't seem to get that command to work in an App. Launcher on a panel etc. however.  :(

*edit*
I decided to do it cheap and dirty and made a script that runs the "SAL_NOOPENGL=true ooffice -writer" command and set the shortcut pointing to it.  Works fine now, **and** with 3D acceleration enabled!

---

### Post by mcglnx on 2007-07-14
I got exactly the same issue since a couple of days (weeks?)

Using the following command as proposed works:
```
SAL_NOOPENGL=true ooffice

```

This is still a hacker trick - not for my gran'ma! :)

---

### Post by mcglnx on 2007-07-14
> **mcglnx said:**
> I got exactly the same issue since a couple of days (weeks?)

Using the following command as proposed works:
```
SAL_NOOPENGL=true ooffice

```

This is still a hacker trick - not for my gran'ma! :)

And this one works as well:
```

 sudo apt-get remove --purge scim-bridge scim

```

---

### Post by brodiepearce on 2007-10-09
> **mcglnx said:**
> And this one works as well:
```

 sudo apt-get remove --purge scim-bridge scim

```

That's a poor fix, considering if you already have SCIM installed, you probably need it.  :P

---

### Post by Rob Lindsay on 2007-10-31
I removed openoffice.org.gtk which also triggered the removal of openoffice.org.gnome, but fixed the problem.

Unfortunately OOo doesn't look quite as nice without the gtk.

---

### Post by Fruhwirth on 2007-11-20
> **Rob Lindsay said:**
> I removed openoffice.org.gtk which also triggered the removal of openoffice.org.gnome, but fixed the problem.

Unfortunately OOo doesn't look quite as nice without the gtk.

I had the same problem mentioned by the original poster except OOo would open. Only after selecting a menu item, such as "Format cells..." would it fail, lockup and give a similar terminal output.

In Synaptic I uninstalled openoffice.org-gtk, which prompted removal of openoffice.org-gnome and now it works fine. 

Annoying though.  This problem did not occur for me for several weeks of installed Gutsy and never happened in Dapper. I use OOo spreadsheets every week.  I believe a software update caused me to begin having the problem just this week or last because I have not changed anything else major that I can remember.

I guess this is another ATI-driver related problem?
by the by, I have ATI Radeon Xpress 200M using fglrx: OpenGL version string: 2.0.6473 (8.37.6).

---

