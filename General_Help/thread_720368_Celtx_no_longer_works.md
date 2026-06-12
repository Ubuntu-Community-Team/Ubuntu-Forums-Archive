---
title: "Celtx no longer works"
date: 2008-03-10
forum: General Help
---

### Post by DrQuincy on 2008-03-10
I was running Celtx fine on two Gutsy machines. I have one at work and one at home that I've set up almost to be identical. Anyway, I was running it fine on both machines without issue. I went a period of a couple of weeks of not using it and in that time installed a few bits and piece on both machines. Now, Celtx just freezes or crashes when I run it. I get as far as the first screen where you can start a new project or choose an existing recent one. If you choose either it will either freeze or crash. If I run it from the terminal I get this (which means nothing to me I'm afraid):

```
tim@kubuntu:~/Desktop/DesktopStorage/celtx$ ./celtx
*** glibc detected *** ./celtx-bin: double free or corruption (out): 0x08c004b0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7317d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb731b800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7855961]
./celtx-bin[0x82125ea]
./celtx-bin[0x8212dfc]
./celtx-bin[0x8211765]
./celtx-bin[0x826c6c3]
./celtx-bin[0x826baf9]
./celtx-bin[0x829efa2]
./celtx-bin[0x835bbf7]
./celtx-bin[0x835bcc2]
./celtx-bin[0x835bd9e]
./celtx-bin[0x835bb76]
./celtx-bin[0x835bcc2]
./celtx-bin[0x835bd9e]
./celtx-bin[0x835bb76]
./celtx-bin[0x835bcc2]
./celtx-bin[0x835bd9e]
./celtx-bin[0x835bb76]
./celtx-bin[0x835bcc2]
./celtx-bin[0x835bd9e]
./celtx-bin[0x835bb76]
./celtx-bin[0x82871e1]
./celtx-bin[0x843c797]
./celtx-bin[0x843feb2]
./celtx-bin[0x843f8dd]
./celtx-bin[0x843e9a0]
./celtx-bin[0x84410b8]
./celtx-bin[0x843c224]
./celtx-bin[0x8250593]
./celtx-bin[0x8249eb4]
./celtx-bin[0x824df70]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7b7f1de]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb78ea772]
/usr/lib/libgobject-2.0.so.0[0xb78fb323]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb78fc60f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb78fca09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c9d498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x475)[0xb7b796f5]
/usr/lib/libgdk-x11-2.0.so.0[0xb79cf06f]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0xba)[0xb79cf73a]
/usr/lib/libgdk-x11-2.0.so.0[0xb79cf79b]
/usr/lib/libgdk-x11-2.0.so.0[0xb79b55e8]
/usr/lib/libglib-2.0.so.0[0xb784c551]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb784e11c]
/usr/lib/libglib-2.0.so.0[0xb785155f]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7851909]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7b799e4]
./celtx-bin[0x824f9fc]
./celtx-bin[0x865aff4]
./celtx-bin[0x807d97d]
./celtx-bin[0x8079bb7]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb72c4050]
./celtx-bin[0x8079b01]
======= Memory map: ========
08048000-08996000 r-xp 00000000 08:01 26772034   /home/tim/Desktop/DesktopStorage/celtx/celtx-bin
08996000-089b9000 rw-p 0094d000 08:01 26772034   /home/tim/Desktop/DesktopStorage/celtx/celtx-bin
089b9000-0957f000 rw-p 089b9000 00:00 0          [heap]
b1da0000-b1da7000 r-xp 00000000 08:01 31672098   /usr/lib/libfam.so.0.0.0
b1da7000-b1da8000 rw-p 00006000 08:01 31672098   /usr/lib/libfam.so.0.0.0
b1da8000-b1dae000 r-xp 00000000 08:01 13680673   /lib/libacl.so.1.1.0
b1dae000-b1daf000 rw-p 00005000 08:01 13680673   /lib/libacl.so.1.1.0
b1dc3000-b1dcf000 r-xp 00000000 08:01 31768619   /usr/lib/gnome-vfs-2.0/modules/libfile.so
b1dcf000-b1dd0000 rw-p 0000b000 08:01 31768619   /usr/lib/gnome-vfs-2.0/modules/libfile.so
b1dd0000-b1dd2000 r-xp 00000000 08:01 31817798   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b1dd2000-b1dd3000 rw-p 00001000 08:01 31817798   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b1dd3000-b1df2000 r--p 00000000 08:01 10944594   /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf
b1df2000-b1e0a000 r--p 00000000 08:01 31966011   /usr/share/fonts/type1/gsfonts/n019004l.pfb
b1e0a000-b1e24000 r--p 00000000 08:01 31966010   /usr/share/fonts/type1/gsfonts/n019003l.pfb
b1e24000-b1e56000 r-xp 00000000 08:01 31671379   /usr/lib/libcroco-0.6.so.3.0.1
b1e56000-b1e59000 rw-p 00031000 08:01 31671379   /usr/lib/libcroco-0.6.so.3.0.1
b1e59000-b1e89000 r-xp 00000000 08:01 31672221   /usr/lib/libgsf-1.so.114.0.7
b1e89000-b1e8c000 rw-p 0002f000 08:01 31672221   /usr/lib/libgsf-1.so.114.0.7
b1e8c000-b1e8d000 rw-p b1e8c000 00:00 0 
b1e8d000-b1ebd000 r-xp 00000000 08:01 31672015   /usr/lib/librsvg-2.so.2.18.2
b1ebd000-b1ebe000 rw-p 00030000 08:01 31672015   /usr/lib/librsvg-2.so.2.18.2
b1ebf000-b1ec2000 r-xp 00000000 08:01 13680771   /lib/libattr.so.1.1.0
b1ec2000-b1ec3000 rw-p 00002000 08:01 13680771   /lib/libattr.so.1.1.0
b1ec3000-b1ed1000 r-xp 00000000 08:01 34980736   /home/tim/Desktop/DesktopStorage/celtx/components/libspellchecker.so
b1ed1000-b1ed2000 rw-p 0000e000 08:01 34980736   /home/tim/Desktop/DesktopStorage/celtx/components/libspellchecker.so
b1ed2000-b1ed6000 r-xp 00000000 08:01 13713938   /lib/tls/i686/cmov/libnss_dns-2.6.1.so
b1ed6000-b1ed8000 rw-p 00003000 08:01 13713938   /lib/tls/i686/cmov/libnss_dns-2.6.1.so
b1ed8000-b1eda000 r-xp 00000000 08:01 13680944   /lib/libnss_mdns4_minimal.so.2
b1eda000-b1edb000 rw-p 00001000 08:01 13680944   /lib/libnss_mdns4_minimal.so.2
b1edc000-b1eeb000 r-xp 00000000 08:01 13680891   /lib/libbz2.so.1.0.4
b1eeb000-b1eec000 rw-p 0000f000 08:01 13680891   /lib/libbz2.so.1.0.4
b1eec000-b1eed000 r-xp 00000000 08:01 31735851   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b1eed000-b1eee000 rw-p 00000000 08:01 31735851   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b1eef000-b1ef0000 ---p b1eef000 00:00 0 
b1ef0000-b26f0000 rw-p b1ef0000 00:00 0 
b26f0000-b2729000 r-xp 00000000 08:01 26772039   /home/tim/Desktop/DesktopStorage/celtx/libnssckbi.so
b2729000-b2733000 rw-p 00038000 08:01 26772039   /home/tim/Desktop/DesktopStorage/celtx/libnssckbi.so
b2733000-b276f000 r-xp 00000000 08:01 26772045   /home/tim/Desktop/DesktopStorage/celtx/libfreebl3.so
b276f000-b2770000 rw-p 0003c000 08:01 26772045   /home/tim/Desktop/DesktopStorage/celtx/libfreebl3.so
b27700Killed
```

I've tried removing it totally and redownloading and installing to no avail. At first I thought the .celtx file I was working on was corrupt but I've loaded it on my Mac and it's fine. The fact I'm having the same problem on two machines and have installed things in between it must be one of those packages that is interfering.  I've changed that much though I have no idea what it might be. Any ideas?

---

### Post by DrQuincy on 2008-03-10
Update . . . 

Running it on the other machine it says:

```
Segmentation fault (core dumped)

```

Any ideas?

---

### Post by l4lucas on 2008-04-27
I am having the same problem. It just started recently... must have been some package update that caused it...

---

### Post by halfhaggis on 2008-05-03
Perhaps you'll have better luck asking [at the celtx forums:]("http://forums.celtx.com/")
Or else, submit a bug report there to help the developers help you.

---

