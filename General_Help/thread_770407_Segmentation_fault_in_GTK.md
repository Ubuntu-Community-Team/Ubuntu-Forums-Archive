---
title: "Segmentation fault in GTK"
date: 2008-04-27
forum: General Help
---

### Post by alexfarran on 2008-04-27
I've just upgraded to 8.04 from 7.10.

A couple of programs immediately segfault when I start them: brasero and gthumb.  I've run a backtrace on both of them and the error seems to be due to gtk_file_system_path_to_uri().  Here's a backtrace for brasero:

#0  0xb7121bc7 in strchr () from /lib/tls/i686/cmov/libc.so.6
#1  0xb7985d3c in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#2  0x00000003 in ?? ()
#3  0x0000002f in ?? ()
#4  0xbfc4dec8 in ?? ()
#5  0xb79a40a5 in gtk_file_system_path_to_uri ()
   from /usr/lib/libgtk-x11-2.0.so.0
#6  0xb798843a in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#7  0x084984d8 in ?? ()
#8  0x084cda68 in ?? ()
#9  0x00000004 in ?? ()
#10 0xb72d2248 in ?? () from /usr/lib/libglib-2.0.so.0
#11 0x08498698 in ?? ()
#12 0x08244a90 in ?? ()
#13 0xbfc4df08 in ?? ()
#14 0xb72618b1 in g_free () from /usr/lib/libglib-2.0.so.0
#15 0xb798fe4f in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#16 0x00000000 in ?? ()

---

