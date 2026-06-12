---
title: "AWN Beryl and Firefox crashes, Ubuntu Feisty Fawn"
date: 2008-03-11
forum: General Help
---

### Post by Captaingracekidd on 2008-03-11
Yesterday I got a little over excited an installed a bunch of cool programs on my old laptop. I am on feisty and wanted a nicer look so I installed AWN+dependencies (though I gave up on the installation of awn-extra) Beryl+dependencies and also the DarkIce theme from gnome-look.org. 
She is beautiful now but I have a huge issue. 
Firefox crashes or freezes when I try to access the preferences!! :confused:  

I have tried shuting down both awn and beryl but can still not get it to work. I ahve no idea whats doing this, although I have seen other people having issues with dark themes and firefox? But I dont understand how a theme could do this. 

This is the terminal output:
```

-laptop:~$ firefox
*** glibc detected *** /usr/lib/firefox/firefox-bin: double free or corruption (out): 0x084c8f80 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb770fd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7713800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7523961]
/usr/lib/firefox/components/libgfx_gtk.so[0xb56e3a7d]
/usr/lib/firefox/components/libgfx_gtk.so[0xb5703169]
/usr/lib/firefox/components/libgklayout.so[0xb58264dd]
/usr/lib/firefox/components/libgklayout.so[0xb5827267]
/usr/lib/firefox/components/libgklayout.so[0xb586d22b]
/usr/lib/firefox/components/libgklayout.so[0xb597e321]
/usr/lib/firefox/components/libgklayout.so[0xb597e190]
/usr/lib/firefox/components/libgklayout.so[0xb597efdb]
/usr/lib/firefox/components/libgklayout.so[0xb597e285]
/usr/lib/firefox/components/libgklayout.so[0xb597e190]
/usr/lib/firefox/components/libgklayout.so[0xb597efdb]
/usr/lib/firefox/components/libgklayout.so[0xb597e285]
/usr/lib/firefox/components/libgklayout.so[0xb597e190]
/usr/lib/firefox/components/libgklayout.so[0xb597efdb]
/usr/lib/firefox/components/libgklayout.so[0xb597e285]
/usr/lib/firefox/components/libgklayout.so[0xb597e190]
/usr/lib/firefox/components/libgklayout.so[0xb597efdb]
/usr/lib/firefox/components/libgklayout.so[0xb59948e5]
/usr/lib/firefox/components/libgklayout.so[0xb597e190]
/usr/lib/firefox/components/libgklayout.so[0xb597efdb]
/usr/lib/firefox/components/libgklayout.so[0xb597e285]
/usr/lib/firefox/components/libgklayout.so[0xb583f815]
/usr/lib/firefox/components/libgklayout.so[0xb5b1d535]
/usr/lib/firefox/components/libgklayout.so[0xb5b200d9]
/usr/lib/firefox/components/libgklayout.so[0xb5b25f80]
/usr/lib/firefox/components/libgklayout.so[0xb5b282d9]
/usr/lib/firefox/components/libgklayout.so[0xb5b290dd]
/usr/lib/firefox/components/libgklayout.so[0xb5b1d236]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb676b22e]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb6762eb2]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb6762f3b]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7bb61de]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb75b8772]
/usr/lib/libgobject-2.0.so.0[0xb75c9323]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb75ca60f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb75caa09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7cd4498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x475)[0xb7bb06f5]
/usr/lib/libgdk-x11-2.0.so.0[0xb7a0606f]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0xba)[0xb7a0673a]
/usr/lib/libgdk-x11-2.0.so.0[0xb7a0679b]
/usr/lib/libgdk-x11-2.0.so.0[0xb79ec5e8]
/usr/lib/libglib-2.0.so.0[0xb751a551]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb751c11c]
/usr/lib/libglib-2.0.so.0[0xb751f55f]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb751f909]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7bb09e4]
/usr/lib/firefox/components/libwidget_gtk2.so[0xb6769b12]
/usr/lib/firefox/components/libtoolkitcomps.so[0xb6684be2]
/usr/lib/firefox/firefox-bin[0x804f8d1]
/usr/lib/firefox/firefox-bin[0x804ab8f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb76bc050]
/usr/lib/firefox/firefox-bin[0x804aac1]
======= Memory map: ========
08048000-0805a000 r-xp 00000000 08:01 863274     /usr/lib/firefox/firefox-bin
0805a000-0805b000 rw-p 00012000 08:01 863274     /usr/lib/firefox/firefox-bin
0805b000-08ebc000 rw-p 0805b000 00:00 0          [heap]
aed00000-aed21000 rw-p aed00000 00:00 0 
aed21000-aee00000 ---p aed21000 00:00 0 
aeed1000-aeed3000 r-xp 00000000 08:01 201734     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
aeed3000-aeed4000 rw-p 00001000 08:01 201734     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
aeed4000-aef51000 r--p 00000000 08:01 262636     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
aef51000-aef88000 r-xp 00000000 08:01 863283     /usr/lib/firefox/libnssckbi.so
aef88000-aef91000 rw-p 00037000 08:01 863283     /usr/lib/firefox/libnssckbi.so
aef91000-aefd0000 r-xp 00000000 08:01 50351      /usr/lib/libfreebl3.so
aefd000Killed

```
Please Help! 

(Also, Im not an expert at ubuntu, I can work the terminal but please be very specific with instructions, thanks!)

---

### Post by emshains on 2008-03-15
I also have no idea how to fix this, but i can suggest upgrading to gutsy, it will have compiz-fusionso you it will be easier to customize your desktop. Also gutsy (without compiz) wont take more resources than feisty would.

---

