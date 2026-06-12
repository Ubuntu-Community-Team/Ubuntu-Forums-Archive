---
title: "Downloader for X 2.5.5 start error"
date: 2005-09-18
forum: General Help
---

### Post by zerooo on 2005-09-18
When starting Download manager for x (d4x) i get this:
```
ubuntu@User:~$ d4x

(d4x:10299): Gdk-CRITICAL **: gdk_gc_set_clip_rectangle: assertion `GDK_IS_GC (gc)' failed

(d4x:10299): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:10299): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:10299): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:10299): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:10299): Gdk-CRITICAL **: gdk_gc_set_clip_rectangle: assertion `GDK_IS_GC (gc)' failed
Segmentation fault
```
I think i know where's the problem. I need to downgrade GTK+ 2.8.3 to 2.4.X, but how to do that? Or how to install 2.4.X without removing 2.8.3? (In synaptic i didn't managed to find 2.4.X package)

---

### Post by zerooo on 2005-09-18
If nobody's know how to help me, maybe you can offer me a good multi thread (prefered gui) download manager?

---

