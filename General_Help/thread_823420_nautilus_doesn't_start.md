---
title: "nautilus doesn't start"
date: 2008-06-09
forum: General Help
---

### Post by grzegorz_maj on 2008-06-09
Hi,
after one of last Ubuntu updates (about 2 weeks ago) nautilus has stoped working. When I'm trying to run it, there comes such an error:

(nautilus:6772): GLib-GObject-CRITICAL **: g_value_dup_boxed: assertion `G_VALUE_HOLDS_BOXED (value)' failed

(nautilus:6772): GLib-GIO-CRITICAL **: g_themed_icon_constructed: assertion `themed->names != NULL && themed->names[0] != NULL' failed
*** glibc detected *** nautilus: free(): invalid next size (fast): 0x081f2b70 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb72c2a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb72c64f0]
/usr/local/lib/libglib-2.0.so.0(g_free+0x31)[0xb7604941]
/usr/local/lib/libgio-2.0.so.0(g_themed_icon_new_from_names+0x8b)[0xb7704afb]
/usr/local/lib/libgio-2.0.so.0(g_content_type_get_icon+0xdf)[0xb76e49ef]
/usr/local/lib/libgio-2.0.so.0[0xb7718328]
/usr/local/lib/libgio-2.0.so.0[0xb77134a5]
/usr/local/lib/libgio-2.0.so.0(g_file_query_info+0x90)[0xb76edc90]
/usr/local/lib/libgio-2.0.so.0[0xb76ef1f4]
/usr/local/lib/libgio-2.0.so.0[0xb7703d49]
/usr/local/lib/libgio-2.0.so.0[0xb76fd884]
/usr/local/lib/libglib-2.0.so.0[0xb762672b]
/usr/local/lib/libglib-2.0.so.0[0xb7624a9f]
/lib/tls/i686/cmov/libpthread.so.0[0xb73ab4fb]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb732de5e]

I've got Ubuntu 8.04. I've reinstalled nautilus and gnome, but nothing has changed.

---

