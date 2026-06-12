---
title: "Gnome-panel Error / Not Showing On Boot --help--"
date: 2008-07-08
forum: General Help
---

### Post by kaola_linux on 2008-07-08
kaola@desktop-linux:~$ gnome-panel
*** glibc detected *** gnome-panel: malloc(): memory corruption: 0x0000000000b3dc70 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f204b8d1a14]
/lib/libc.so.6(__libc_calloc+0x10f)[0x7f204b8d307f]
/usr/lib/libglib-2.0.so.0(g_malloc0+0x23)[0x7f204c31ec33]
/usr/lib/libgobject-2.0.so.0[0x7f204c5c4602]
/usr/lib/libgobject-2.0.so.0(g_type_register_static+0x2d1)[0x7f204c5c9dd1]
/usr/lib/libgobject-2.0.so.0(g_type_register_static_simple+0x58)[0x7f204c5c9fa8]
/usr/lib/libgio-2.0.so.0(g_themed_icon_get_type+0x67)[0x7f204f4bdcd7]
/usr/lib/libgio-2.0.so.0(g_themed_icon_new_from_names+0x59)[0x7f204f4bdf29]
/usr/lib/libgio-2.0.so.0(g_content_type_get_icon+0xb6)[0x7f204f49fba6]
/usr/lib/libgio-2.0.so.0[0x7f204f4cebae]
/usr/lib/libgio-2.0.so.0[0x7f204f4ca7d6]
gnome-panel(panel_util_get_icon_for_uri+0x281)[0x436921]
gnome-panel[0x44ed3c]
gnome-panel(panel_place_menu_item_new+0xc6)[0x44f5f6]
gnome-panel[0x44aed8]
/usr/lib/libgobject-2.0.so.0(g_type_create_instance+0x503)[0x7f204c5cc543]
/usr/lib/libgobject-2.0.so.0[0x7f204c5b1f4d]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0x230)[0x7f204c5b2540]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x2d2)[0x7f204c5b3032]
/usr/lib/libgobject-2.0.so.0(g_object_new+0xa1)[0x7f204c5b3171]
gnome-panel(panel_menu_bar_load_from_gconf+0x4d)[0x44a58d]
gnome-panel[0x4331b0]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f2)[0x7f204c317262]
/usr/lib/libglib-2.0.so.0[0x7f204c31a516]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1b7)[0x7f204c31a7d7]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa3)[0x7f204dda0f03]
gnome-panel(main+0x162)[0x4232d2]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7f204b87b1c4]
gnome-panel[0x4227a9]
======= Memory map: ========
00400000-00487000 r-xp 00000000 08:03 1107518                            /usr/bin/gnome-panel
00687000-0068b000 rw-p 00087000 08:03 1107518                            /usr/bin/gnome-panel
0068b000-00b71000 rw-p 0068b000 00:00 0                                  [heap]
7f203c000000-7f203c021000 rw-p 7f203c000000 00:00 0 
7f203c021000-7f2040000000 ---p 7f203c021000 00:00 0 
7f204262c000-7f204263b000 r-xp 00000000 08:03 1106308                    /usr/lib/libhal.so.1.0.0
7f204263b000-7f204283a000 ---p 0000f000 08:03 1106308                    /usr/lib/libhal.so.1.0.0
7f204283a000-7f204283b000 rw-p 0000e000 08:03 1106308                    /usr/lib/libhal.so.1.0.0
7f204283b000-7f204285d000 r-xp 00000000 08:03 1138697                    /usr/lib/gio/modules/libgiohal-volume-monitor.so
7f204285d000-7f2042a5c000 ---p 00022000 08:03 1138697                    /usr/lib/gio/modules/libgiohal-volume-monitor.so
7f2042a5c000-7f2042a5e000 rw-p 00021000 08:03 1138697                    /usr/lib/gio/modules/libgiohal-volume-monitor.so
7f2042a5e000-7f2042a83000 r-xp 00000000 08:03 1138698                    /usr/lib/gio/modules/libgvfsdbus.so
7f2042a83000-7f2042c82000 ---p 00025000 08:03 1138698                    /usr/lib/gio/modules/libgvfsdbus.so
7f2042c82000-7f2042c84000 rw-p 00024000 08:03 1138698                    /usr/lib/gio/modules/libgvfsdbus.so
7f2042c84000-7f2042c88000 r-xp 00000000 08:03 1139900                    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f2042c88000-7f2042e88000 ---p 00004000 08:03 1139900                    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f2042e88000-7f2042e89000 rw-p 00004000 08:03 1139900                    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f2042e89000-7f2042e8b000 r-xp 00000000 08:03 1107242                    /usr/lib/libXRes.so.1.0.0
7f2042e8b000-7f204308a000 ---p 00002000 08:03 1107242                    /usr/lib/libXRes.so.1.0.0
7f204308a000-7f204308b000 rw-p 00001000 08:03 1107242                    /usr/lib/libXRes.so.1.0.0
7f204308b000-7f20430c7000 r-xp 00000000 08:03 1108068                    /usr/lib/libwnck-1.so.22.3.7
7f20430c7000-7f20432c7000 ---p 0003c000 08:03 1108068                    /usr/lib/libwnck-1.so.22.3.7
7f20432c7000-7f20432c9000 rw-p 0003c000 08:03 1108068                    /usr/lib/libwnck-1.so.22.3.7
7f20432c9000-7f20432d8000 r-xp 00000000 08:03 1107446                    /usr/lib/libpanel-applet-2.so.0.2.34
7f20432d8000-7f20434d7000 ---p 0000f000 08:03 1107446                    /usr/lib/libpanel-applet-2.so.0.2.34
7f20434d7000-7f20434d9000 rw-p 0000e000 08:03 1107446                    /usr/lib/libpanel-applet-2.so.0.2.34
7f20434d9000-7f20434e6000 r-xp 00000000 08:03 376841                     /usr/lib/gnome-panel/libwnck-applet.so
7f20434e6000-7f20436e6000 ---p 0000d000 08:03 376841                     /usr/lib/gnome-panel/libwnck-applet.so
7f20436e6000-7f20436e7000 rw-p 0000d000 08:03 376841                     /usr/lib/gnome-panel/libwnck-applet.so
7f20436e7000-7f2043747000 rw-s 00000000 00:09 819208                     /SYSV00000000 (deleted)
7f2043747000-7f2043a0d000 r--p 00000000 08:03 1338250                    /usr/share/icons/hicolor/icon-theme.cache
7f2043a0d000-7f2043ab8000 r--p 00000000 08:03 1337741                    /usr/share/icons/Tangerine/icon-theme.cache
7f2043ab8000-7f2043b7b000 rw-p 7f2043ab8000 00:00 0 
7f2043b7b000-7f2043b7d000 r-xp 00000000 08:03 1131639                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f2043b7d000-7f2043d7c000 ---p 00002000 08:03 1131639                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f2043d7c000-7f2043d7d000 rw-p 00001000 08:03 1131639                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f2043d7d000-7f2043e0e000 r--p 00000000 08:03 1253510                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
7f2043e0e000-7f2043e20000 r-xp 00000000 08:03 1139086                    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
7f2043e20000-7f2044020000 ---p 00012000 08:03 1139086                    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
7f2044020000-7f2044021000 rw-p 00012000 08:03 1139086                    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
7f2044021000-7f204402b000 r-xp 00000000 08:03 1163352                    /lib/libnss_files-2.7.so
7f204402b000-7f204422b000 ---p 0000a000 08:03 1163352                    /lib/libnss_files-2.7.so
7f204422b000-7f204422d000 rw-p 0000a000 08:03 1163352                    /lib/libnss_files-2.7.so
7f204422d000-7f2044237000 r-xp 00000000 08:03 1163362                    /lib/libnss_nis-2.7.so
7f2044237000-7f2044436000 ---p 0000a000 08:03 1163362                    /lib/libnss_nis-2.7.so
7f2044436000-7f2044438000 rw-p 00009000 08:03 1163362                    /lib/libnss_nis-2.7.so
7f2044438000-7f2044440000 r-xp 00000000 08:03 1163348                    /lib/libnss_compat-2.7.so
7f2044440000-7f204463f000 ---p 00008000 08:03 1163348                    /lib/libnss_compat-2.7.so
7f204463f000-7f2044641000 rw-p 00007000 08:03 1163348                    /lib/libnss_compat-2.7.so
7f2044641000-7f2044644000 r-xp 00000000 08:03 1163331                    /lib/libgpg-error.so.0.3.0
7f2044644000-7f2044843000 ---p 00003000 08:03 1163331                    /lib/libgpg-error.so.0.3.0
7f2044843000-7f2044844000 rw-p 00002000 08:03 1163331                    /lib/libgpg-error.so.0.3.0
7f2044844000-7f2044890000 r-xp 00000000 08:03 1163329                    /lib/libgcrypt.so.11.2.3
7f2044890000-7f2044a8f000 ---p 0004c000 08:03 1163329                    /lib/libgcrypt.so.11.2.3
7f2044a8f000-7f2044a92000 rw-p 0004b000 08:03 1163329                    /lib/libgcrypt.so.11.2.3
7f2044a92000-7f2044aa2000 r-xp 00000000 08:03 1108026                    /usr/lib/libtasn1.so.3.0.12
7f2044aa2000-7f2044ca1000 ---p 00010000 08:03 1108026                    /usr/lib/libtasn1.so.3.0.12
7f2044ca1000-7f2044ca2000 rw-p 0000f000 08:03 1108026                    /usr/lib/libtasn1.so.3.0.12
7f2044ca2000-7f2044ca7000 r-xp 00000000 08:03 1107257                    /usr/lib/libXdmcp.so.6.0.0
7f2044ca7000-7f2044ea6000 ---p 00005000 08:03 1107257                    /usr/lib/libXdmcp.so.6.0.0
7f2044ea6000-7f2044ea7000 rw-p 00004000 08:03 1107257                    /usr/lib/libXdmcp.so.6.0.0
7f2044ea7000-7f2044ec9000 r-xp 00000000 08:03 1107483                    /usr/lib/libexpat.so.1.5.2
7f2044ec9000-7f20450c9000 ---p 00022000 08:03 1107483                    /usr/lib/libexpat.so.1.5.2
7f20450c9000-7f20450cb000 rw-p 00022000 08:03 1107483                    /usr/lib/libexpat.so.1.5.2
7f20450cb000-7f20451a2000 r-xp 00000000 08:03 1107318                    /usr/lib/libasound.so.2.0.0
7f20451a2000-7f20453a2000 ---p 000d7000 08:03 1107318                    /usr/lib/libasound.so.2.0.0
7f20453a2000-7f20453a9000 rw-p 000d7000 08:03 1107318                    /usr/lib/libasound.so.2.0.0
7f20453a9000-7f20453ab000 r-xp 00000000 08:03 1163407                    /lib/libutil-2.7.so
7f20453ab000-7f20455aa000 ---p 00002000 08:03 1163407                    /lib/libutil-2.7.so
7f20455aa000Aborted


--------------------------------------------------------------------------
   I just installed Glib, just compiled it though because I want to install XMMS but to no luck hence I had a faulty machine now... :(

   Please help me with this because if I can't handle this I might as well reinstall Ubuntu but I can't afford to lose my apps and installed updates it's too time consuming to do things whole over again...I'm typing this message using Firefox runned from Terminal...NO GNOME-PANEL AVAILABLE!!!

   Thanks in advance...

---

### Post by adityakavoor on 2008-07-08
Hit Alt+F2 and type in gnome-terminal
now type in the following to the terminal

```


gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

```

---

### Post by kaola_linux on 2008-07-08
Thanks for your reply
The code you showed does not function, it just loads...It doesn't do anything..can u help me plz? If I can't then I just might as well reinstall

---

### Post by adityakavoor on 2008-07-08
```

sudo dpkg-reconfigure gnome-panel

```

---

