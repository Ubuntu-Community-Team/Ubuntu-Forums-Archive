---
title: "Building Thunderbird 2.0.0.6 from sources"
date: 2007-09-07
forum: General Help
---

### Post by panayk on 2007-09-07
Has anyone succeeded in building Thunderbird 2.0.0.6 from sources on Feisty? I am trying to build a .deb but I get:

```
make[3]: Entering directory `/home/panayk/Desktop/projects/mozilla-thunderbird-2.0.0.6/widget/src/gtkxtbin'
rm -f libgtkxtbin.so
c++  -fno-rtti -fno-exceptions -Wall -Wconversion -Wpointer-arith -Wcast-align -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wno-long-long -pedantic -fshort-wchar -pthread -pipe  -DNDEBUG -DTRIMMED -O -fPIC -shared -Wl,-z,defs -Wl,-h,libgtkxtbin.so -o libgtkxtbin.so  gtk2xtbin.o       -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0      -ldl -lm    
gtk2xtbin.o: In function `xt_event_dispatch':
gtk2xtbin.c:(.text+0xdf): undefined reference to `XtDisplayToApplicationContext'
gtk2xtbin.c:(.text+0x106): undefined reference to `XtAppProcessEvent'
gtk2xtbin.o: In function `xt_event_polling_timer_callback':
gtk2xtbin.c:(.text+0x21b): undefined reference to `XtDisplayToApplicationContext'
gtk2xtbin.c:(.text+0x234): undefined reference to `XtAppProcessEvent'
gtk2xtbin.c:(.text+0x244): undefined reference to `XtAppPending'
gtk2xtbin.o: In function `gtk_xtbin_resize':
gtk2xtbin.c:(.text+0x2d2): undefined reference to `XtStrings'
gtk2xtbin.c:(.text+0x30a): undefined reference to `XtSetValues'
gtk2xtbin.o: In function `gtk_xtbin_new':
gtk2xtbin.c:(.text+0x404): undefined reference to `XtToolkitInitialize'
gtk2xtbin.c:(.text+0x409): undefined reference to `XtCreateApplicationContext'
gtk2xtbin.c:(.text+0x425): undefined reference to `XtAppSetFallbackResources'
gtk2xtbin.c:(.text+0x469): undefined reference to `XtOpenDisplay'
gtk2xtbin.o: In function `gtk_xtbin_destroy':
gtk2xtbin.c:(.text+0x767): undefined reference to `XtRemoveEventHandler'
gtk2xtbin.c:(.text+0x772): undefined reference to `XtDestroyWidget'
gtk2xtbin.o: In function `xt_client_set_info':
gtk2xtbin.c:(.text+0x81e): undefined reference to `XtDisplay'
gtk2xtbin.c:(.text+0x84e): undefined reference to `XtWindow'
gtk2xtbin.c:(.text+0x859): undefined reference to `XtDisplay'
gtk2xtbin.o: In function `xt_remove_focus_listener':
gtk2xtbin.c:(.text+0x947): undefined reference to `XtRemoveEventHandler'
gtk2xtbin.o: In function `send_xembed_message':
gtk2xtbin.c:(.text+0x991): undefined reference to `XtWindow'
gtk2xtbin.o: In function `xt_client_event_handler':
gtk2xtbin.c:(.text+0xad8): undefined reference to `XtDisplay'
gtk2xtbin.c:(.text+0xb40): undefined reference to `XtWindow'
gtk2xtbin.c:(.text+0xb4e): undefined reference to `XtDisplay'
gtk2xtbin.c:(.text+0xb5f): undefined reference to `XtDisplay'
gtk2xtbin.c:(.text+0xb8d): undefined reference to `XtDisplay'
gtk2xtbin.o: In function `gtk_xtbin_unrealize':
gtk2xtbin.c:(.text+0xc8f): undefined reference to `XtUnregisterDrawable'
gtk2xtbin.c:(.text+0xcb9): undefined reference to `XtUnrealizeWidget'
gtk2xtbin.o: In function `gtk_xtbin_realize':
gtk2xtbin.c:(.text+0xe7a): undefined reference to `applicationShellWidgetClass'
gtk2xtbin.c:(.text+0xe98): undefined reference to `XtAppCreateShell'
gtk2xtbin.c:(.text+0xea6): undefined reference to `XtStrings'
gtk2xtbin.c:(.text+0xec1): undefined reference to `XtStrings'
gtk2xtbin.c:(.text+0xef3): undefined reference to `XtSetValues'
gtk2xtbin.c:(.text+0xf05): undefined reference to `compositeWidgetClass'
gtk2xtbin.c:(.text+0xf19): undefined reference to `XtVaCreateWidget'
gtk2xtbin.c:(.text+0xf3f): undefined reference to `XtShellStrings'
gtk2xtbin.c:(.text+0xf54): undefined reference to `XtStrings'
gtk2xtbin.c:(.text+0xf99): undefined reference to `XtSetValues'
gtk2xtbin.c:(.text+0xfda): undefined reference to `XtRegisterDrawable'
gtk2xtbin.c:(.text+0xfe2): undefined reference to `XtRealizeWidget'
gtk2xtbin.c:(.text+0xfea): undefined reference to `XtWindow'
gtk2xtbin.c:(.text+0x101b): undefined reference to `XtManageChild'
gtk2xtbin.c:(.text+0x1047): undefined reference to `XtAddEventHandler'
gtk2xtbin.c:(.text+0x1070): undefined reference to `XtAddEventHandler'
gtk2xtbin.c:(.text+0x109d): undefined reference to `XtWindow'
gtk2xtbin.o: In function `xt_add_focus_listener_tree':
gtk2xtbin.c:(.text+0x1107): undefined reference to `XtWindow'
gtk2xtbin.c:(.text+0x1115): undefined reference to `XtDisplay'
gtk2xtbin.c:(.text+0x1135): undefined reference to `XtWindow'
gtk2xtbin.c:(.text+0x113f): undefined reference to `XtDisplay'
gtk2xtbin.c:(.text+0x1165): undefined reference to `XtWindow'
gtk2xtbin.c:(.text+0x116f): undefined reference to `XtDisplay'
gtk2xtbin.c:(.text+0x11ae): undefined reference to `XtAddEventHandler'
gtk2xtbin.c:(.text+0x122b): undefined reference to `XtWindowToWidget'
gtk2xtbin.o: In function `xt_client_focus_listener':
gtk2xtbin.c:(.text+0x1280): undefined reference to `XtDisplay'
gtk2xtbin.c:(.text+0x128b): undefined reference to `XtWindow'
gtk2xtbin.c:(.text+0x12d5): undefined reference to `XtWindowToWidget'
gtk2xtbin.c:(.text+0x1306): undefined reference to `XtWindowToWidget'
collect2: ld returned 1 exit status
make[3]: *** [libgtkxtbin.so] Error 1
make[3]: Leaving directory `/home/panayk/Desktop/projects/mozilla-thunderbird-2.0.0.6/widget/src/gtkxtbin'
make[2]: *** [tier_9] Error 2
make[2]: Leaving directory `/home/panayk/Desktop/projects/mozilla-thunderbird-2.0.0.6'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/panayk/Desktop/projects/mozilla-thunderbird-2.0.0.6'
make: *** [build-stamp] Error 2
```

I think I am missing a library. Any ideas?

---

### Post by panayk on 2007-09-07
Never mind. I had to switch '--enable-default-toolkit' from 'cairo-gtk2' to 'gtk2'

---

