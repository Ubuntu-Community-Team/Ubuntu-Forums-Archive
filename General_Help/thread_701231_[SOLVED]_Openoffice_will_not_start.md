---
title: "[SOLVED] Openoffice will not start"
date: 2008-02-19
forum: General Help
---

### Post by Chokkan on 2008-02-19
Hi guys, I'm having a problem with OO. Starting from the desktop, the splash screen appears and then stops.

I've a feeling it's something to do with SCIM, as I recently adjusted my settings so I could actually type in Japanese in OO.

When I start from the command line using
```
soffice -writer
```

I get this!
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(process:17812): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:17812): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:17812): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:17812): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:17812): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:17812): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed
*** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x080ec1e8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6ca67cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6ca9e30]
/usr/lib/openoffice/program/libuno_sal.so.3(rtl_freeMemory+0x1d)[0xb73000bd]
/usr/lib/openoffice/program/soffice.bin[0x809192e]
/usr/lib/openoffice/program/soffice.bin(_ZdlPv+0x26)[0x8091966]
/usr/lib/libscim-1.0.so.8[0x9d54a156]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0x9d54af77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0x9d545f05]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal10initializeEv+0x257)[0x9d5eccf7]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x31e)[0x9d5eeace]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6createERK7QString+0x7e)[0x9d5e7cae]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x25)[0xb5200ecb]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x94)[0xb5200a98]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17changeInputMethodE7QString+0xc3)[0x9d633c9b]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slaveEv+0x43)[0x9d633e4f]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15setHolderWidgetEP7QWidget+0x26)[0x9d6340be]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xb8)[0xb5200abc]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x8f)[0xb4f53965]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x1d)[0xb4f53c6b]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x1d)[0xb50d40e5]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setLineEditEP9QLineEdit+0x82)[0xb509b3e6]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox13setUpLineEditEv+0x60)[0xb5095cb0]
/usr/lib/libqt-mt.so.3(_ZN9QComboBoxC1EbP7QWidgetPKc+0x217)[0xb509af53]
/usr/lib/openoffice/program/libvclplug_kde680li.so[0xb5a1c784]
/usr/lib/openoffice/program/libvclplug_kde680li.so[0xb5a1eaf4]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11SalGraphics22GetNativeControlRegionEmmRK6RegionmRK16ImplControlValueR16SalControlHandleRKN3rtl8OUStringERS0_SC_PK12OutputDevice+0x17b)[0xb7dad56b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN6Window22GetNativeControlRegionEmmRK6RegionmRK16ImplControlValueN3rtl8OUStringERS0_S8_+0x103)[0xb7e6fc93]
/usr/lib/openoffice/program/libvcl680li.so(_ZN8ComboBox6ResizeEv+0x198)[0xb7e840b8]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e56754]
/usr/lib/openoffice/program/libvcl680li.so(_ZN6Window4ShowEht+0xca)[0xb7e58dda]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e3cf15]
/usr/lib/openoffice/program/libvcl680li.so(_ZN7ToolBox12StateChangedEt+0x110)[0xb7e3eb30]
/usr/lib/openoffice/program/libfwk680li.so[0xa0a12dc0]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e49085]
/usr/lib/openoffice/program/libvcl680li.so(_ZN6Window4ShowEht+0x378)[0xb7e59088]
/usr/lib/openoffice/program/libfwk680li.so[0xa090afb9]
/usr/lib/openoffice/program/libfwk680li.so[0xa090bdd7]
/usr/lib/openoffice/program/libtk680li.so[0xb7254cab]
/usr/lib/openoffice/program/libtk680li.so(_ZN10VCLXWindow18ProcessWindowEventERK14VclWindowEvent+0x2ff)[0xb7162adf]
/usr/lib/openoffice/program/libtk680li.so(_ZN10VCLXWindow19WindowEventListenerEP14VclSimpleEvent+0x63)[0xb715fb13]
/usr/lib/openoffice/program/libtk680li.so(_ZN10VCLXWindow27LinkStubWindowEventListenerEPvS0_+0x24)[0xb715fb44]
/usr/lib/openoffice/program/libvcl680li.so(_ZNK17VclEventListeners4CallEP14VclSimpleEvent+0x9a)[0xb7c6e7da]
/usr/lib/openoffice/program/libvcl680li.so(_ZN6Window18CallEventListenersEmPv+0xff)[0xb7e54d5f]
/usr/lib/openoffice/program/libvcl680li.so(_ZN6Window22ImplCallEventListenersEmPv+0x2b)[0xb7e54dbb]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e55a2f]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e559de]
/usr/lib/openoffice/program/libvcl680li.so(_ZN6Window4ShowEht+0x3ba)[0xb7e590ca]
/usr/lib/openoffice/program/libvcl680li.so(_ZN6Window4ShowEht+0x138)[0xb7e58e48]
/usr/lib/openoffice/program/libtk680li.so(_ZN10VCLXWindow10setVisibleEh+0x4e)[0xb716534e]
/usr/lib/openoffice/program/libfwk680li.so[0xa09aa3e2]
/usr/lib/openoffice/program/libfwk680li.so[0xa09aed47]
/usr/lib/openoffice/program/libfwk680li.so[0xa09aefb2]
/usr/lib/openoffice/program/libfwk680li.so[0xa09b576f]
/usr/lib/openoffice/program/libfwk680li.so[0xa09b7493]
/usr/lib/openoffice/program/libfwk680li.so[0xa09b76e5]
/usr/lib/openoffice/program/libfwk680li.so[0xa0853ba3]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop15DispatchWatcher23executeDispatchRequestsERKN8stlp_std6vectorINS0_15DispatchRequestENS1_9allocatorIS3_EEEE+0x23c0)[0x80851a0]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop15OfficeIPCThread22ExecuteCmdLineRequestsERNS_23ProcessDocumentsRequestE+0x133)[0x80776d3]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop11OpenDefaultEv+0x11e)[0x8062c0e]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop11OpenClientsEv+0x1f09)[0x8072fd9]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop16OpenClients_ImplEPv+0x3d)[0x80739cd]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e6a576]
/usr/lib/openoffice/program/libvclplug_gen680li.so(_ZN10SalDisplay21DispatchInternalEventEv+0xc4)[0xb4c8b784]
======= Memory map: ========
08048000-0809c000 r-xp 00000000 08:15 3452677    /usr/lib/openoffice/program/soffice.bin
0809c000-0809e000 rw-p 00053000 08:15 3452677    /usr/lib/openoffice/program/soffice.bin
0809e000-0878d000 rw-p 0809e000 00:00 0          [heap]
9d300000-9d321000 rw-p 9d300000 00:00 0 
9d321000-9d400000 ---p 9d321000 00:00 0 
9d4e2000-9d5b6000 r-xp 00000000 08:15 3370434    /usr/lib/libscim-1.0.so.8.1.0
9d5b6000-9d5c4000 rw-p 000d4000 08:15 3370434    /usr/lib/libscim-1.0.so.8.1.0
9d5c4000-9d5c6000 r-xp 00000000 08:15 3370438    /usr/lib/libscim-x11utils-1.0.so.8.1.0
9d5c6000-9d5c7000 rw-p 00001000 08:15 3370438    /usr/lib/libscim-x11utils-1.0.so.8.1.0
9d5d9000-9d5f7000 r-xp 00000000 08:15 3468688    /usr/lib/qt3/plugins/inputmethods/libqscim.so
9d5f7000-9d5f8000 rw-p 0001e000 08:15 3468688    /usr/lib/qt3/plugins/inputmethods/libqscim.so
9d5f8000-9d603000 r-xp 00000000 08:15 2338355    /usr/lib/qt3/plugins/inputmethods/libqxim.so
9d603000-9d604000 rw-p 0000a000 08:15 2338355    /usr/lib/qt3/plugins/inputmethods/libqxim.so
9d604000-9d628000 r-xp 00000000 08:15 2338354    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
9d628000-9d629000 rw-p 00024000 08:15 2338354    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
9d629000-9d62d000 r-xp 00000000 08:15 2338353    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
9d62d000-9d62e000 rw-p 00003000 08:15 2338353    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
9d62e000-9d637000 r-xp 00000000 08:15 2338351    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
9d637000-9d638000 rw-p 00009000 08:15 2338351    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
9d638000-9d65b000 r--s 00000000 08:15 3581154    /usr/share/fonts/type1/gsfonts/n021003l.pfb
9d65b000-9d6d5000 r-xp 00000000 08:15 3453891    /usr/lib/openoffice/program/libxstor.so
9d6d5000-9d6d8000 rw-p 00079000 08:15 3453891    /usr/lib/openoffice/program/libxstor.so
9d6d8000-9d6f7000 r-xp 00000000 08:15 3453823    /usr/lib/openoffice/program/fsstorage.uno.so
9d6f7000-9d6f9000 rw-p 0001e000 08:15 3453823    /usr/lib/openoffice/program/fsstorage.uno.so
9d6f9000-9d713000 r-xp 00000000 08:15 3453843    /usr/lib/openoffice/program/liblocaledata_en.so
9d713000-9d718000 rw-p 00019000 08:15 3453843    /usr/lib/openoffice/program/liblocaledata_en.so
9d718000-9d856000 r-xp 00000000 08:15 3370237    /usr/lib/libicui18n.so.36.0
9d856000-9d85c000 rw-p 0013e000 08:15 3370237    /usr/lib/libicui18n.so.36.0
9d85e000-9d86e000 rw-p 9d85e000 00:00 0 
9d86e000-9d9bd000 r-xp 00000000 08:15 3453826    /usr/lib/openoffice/program/i18npool.uno.so
9d9bd000-9d9cd000 rw-p 0014e000 08:15 3453826    /usr/lib/openoffice/program/i18npool.uno.so
9d9cd000-9d9df000 rw-p 9d9cd000 00:00 0 
9d9df000-9d9e0000 ---p 9d9df000 00:00 0 
9d9e0000-9e1e0000 rwxp 9d9e0000 00:00 0 
9e1e0000-9e268000 r-xp 00000000 08:15 3453744    /usr/lib/openoffic


```

Any pointers would be much appreciated.

---

### Post by pip_134 on 2008-02-19
It doesn't seem to like one of your plugins (your probably right about SCIM if it was working before). To check can you undo the changes you made and see if open office works then?

---

### Post by Chokkan on 2008-02-19
Yeah, that's probably the best place to start. There are one or two other threads on this problem with SCIM. I did look at those in an effort to solve this but nothing worked. I'll remove SCIM and start from scratch.

---

### Post by Chokkan on 2008-02-20
OK, so I decided to just remove scim using apt, and then I removed openoffice.org, also with apt. Reinstalled openoffice, added the japanese language supprt, and everything seems to be working fine both for me in my en_GB and for my wife in her Japanese environment. I hope it's still working after I reboot the machine.

---

### Post by goggle5 on 2008-03-26
Sorry for the Newbie question ... I am having the same problem with OO not starting up.    What i s SCIM ??

---

### Post by tom-ubuntu on 2008-03-26
Having the same problem since yesterday.

** (process:6785): WARNING **: Unknown error forking main binary / abnormal early exit ...

Any tips? Thank you!

---

