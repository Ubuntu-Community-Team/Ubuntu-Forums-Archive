---
title: "evolution crashes"
date: 2004-11-02
forum: General Help
---

### Post by tanari on 2004-11-02
evolution crashes when starting :(

---

### Post by ubuntu-geek on 2004-11-02
[QUOTE=tanari]evolution crashes when starting :([/QUOTE]
 What errors do you get? Can you give us some more information.. :)

---

### Post by tanari on 2004-11-02
ubuntu start in calendar view and crashes
in error window I press 'inform developers', and than press 'debug info'
```

Backtrace was generated from '/usr/bin/evolution-2.0'

(no debugging symbols found)...Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...(no debugging symbols found)...[Thread debugging using libthread_db enabled]
[New Thread 1092421184 (LWP 6836)]
[New Thread 1108089776 (LWP 6840)]
[Thread debugging using libthread_db enabled]
[New Thread 1092421184 (LWP 6836)]
[New Thread 1108089776 (LWP 6840)]
[Thread debugging using libthread_db enabled]
[New Thread 1092421184 (LWP 6836)]
[New Thread 1108089776 (LWP 6840)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0x40dbf42b in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x4043a3dd in libgnomeui_segv_handle (signum=11) at gnome-ui-init.c:741
#3  0x080660c7 in e_sidebar_get_type ()
#4  <signal handler called>
#5  0x4100f818 in strcmp () from /lib/tls/i686/cmov/libc.so.6
#6  0x41208f63 in ?? () from /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so
#7  0x00000000 in ?? ()
#8  0x080fe648 in ?? ()
#9  0x00000125 in ?? ()
#10 0x4120e3c4 in ?? () from /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so
#11 0xbfffef10 in ?? ()
#12 0x083c2b18 in ?? ()
#13 0xbfffeed8 in ?? ()
#14 0x41208fcb in ?? () from /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so
#15 0x0838d748 in ?? ()
#16 0xbfffef10 in ?? ()
#17 0xbfffef28 in ?? ()
#18 0x40007b65 in _dl_lookup_symbol () from /lib/ld-linux.so.2


```

---

