---
title: "F-Spot crashes right after startup!"
date: 2008-03-08
forum: General Help
---

### Post by KernelPanic14 on 2008-03-08
Yesterday, I imported some photos from a SD Card reader, and when it finished, I unmounted it. Right when the icon changed, i took it off, and then F-Spot crashed. Now, when I open F-Spot, it loads fine, it loads the thumbnails of the photos, and then crashes!
This is what I get:
```
Initializing Mono.Addins
Starting new FSpot server
Query: SELECT photos.id, photos.time, photos.uri, photos.description, photos.roll_id, photos.default_version_id, photos.rating FROM photos  WHERE photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY photos.time
Query: SELECT photos.id, photos.time, photos.uri, photos.description, photos.roll_id, photos.default_version_id, photos.rating FROM photos  WHERE photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY photos.time
Query: SELECT photos.id, photos.time, photos.uri, photos.description, photos.roll_id, photos.default_version_id, photos.rating FROM photos  WHERE photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY photos.time
Query: SELECT photos.id, photos.time, photos.uri, photos.description, photos.roll_id, photos.default_version_id, photos.rating FROM photos  WHERE photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY photos.time
Reloading
Query: SELECT photos.id, photos.time, photos.uri, photos.description, photos.roll_id, photos.default_version_id, photos.rating FROM photos  WHERE photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY photos.time
item changed
open uri = file:///home/mikel/Photos/2008/03/06/201_0622.JPG
open uri = file:///home/mikel/Photos/2008/03/06/201_0622.JPG
Syncing metadata to file...
open uri = file:///home/mikel/Photos/2006/09/26/WELL_SLIDE_SHOW_06___080.JPG
old = "" new = "" heading = "ASCII"
value = 2006:09:26 16:01:05 len = 19
<http://fakebase.f-spot.org/internal/> <http://ns.adobe.com/xap/1.0/Rating> "0" .
value = f-spot version 0.4.2 len = 20
value = 2008:03:08 13:42:42 len = 19
value = f-spot version 0.4.2 len = 20
value = 2008:03:08 13:42:43 len = 19
open uri = file:///home/mikel/Photos/2008/03/06/201_0621.JPG
open uri = file:///home/mikel/Photos/2008/03/06/201_0621.JPG
(f-spot:13989): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
Stacktrace:


Native stacktrace:

        f-spot [0x8194ca6]
        f-spot [0x81770ed]
        [0xffffe440]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1210648880 (LWP 13989)]
[New Thread -1281999984 (LWP 14051)]
[New Thread -1280881776 (LWP 14050)]
[New Thread -1277211760 (LWP 14028)]
[New Thread -1257739376 (LWP 14019)]
[New Thread -1221424240 (LWP 13991)]
[New Thread -1208161392 (LWP 13990)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
  7 Thread -1208161392 (LWP 13990)  0xffffe410 in __kernel_vsyscall ()
  6 Thread -1221424240 (LWP 13991)  0xffffe410 in __kernel_vsyscall ()
  5 Thread -1257739376 (LWP 14019)  0xffffe410 in __kernel_vsyscall ()
  4 Thread -1277211760 (LWP 14028)  0xffffe410 in __kernel_vsyscall ()
  3 Thread -1280881776 (LWP 14050)  0xb6cad790 in deflateInit2_ ()
   from /usr/lib/libz.so.1
  2 Thread -1281999984 (LWP 14051)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1210648880 (LWP 13989)  0xffffe410 in __kernel_vsyscall ()

Thread 7 (Thread -1208161392 (LWP 13990)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7eec9f6 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811bc9f in ?? ()
#3  0xb7fce3ac in ?? ()
#4  0x00000000 in ?? ()

Thread 6 (Thread -1221424240 (LWP 13991)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ee9676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120dde in ?? ()
#3  0xb78021dc in ?? ()
#4  0xb78021c4 in ?? ()
#5  0xb7ee7541 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6  0x081210eb in ?? ()
#7  0xb78021dc in ?? ()
#8  0xb78021c4 in ?? ()
#9  0x00000000 in ?? ()

Thread 5 (Thread -1257739376 (LWP 14019)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ee98fc in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120e5b in ?? ()
#3  0xb7802464 in ?? ()
#4  0xb780244c in ?? ()
#5  0xb5086054 in ?? ()
#6  0x00000000 in ?? ()

Thread 4 (Thread -1277211760 (LWP 14028)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e3d2a1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f5c780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f5cb4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xb4f75844 in ?? ()
#6  0xb4f7582c in ?? ()
#7  0xb4f75828 in ?? ()
#8  0xb4f75824 in ?? ()
#9  0x00000000 in ?? ()

Thread 3 (Thread -1280881776 (LWP 14050)):
#0  0xb6cad790 in deflateInit2_ () from /usr/lib/libz.so.1
#1  0xb61a52ad in ?? () from /usr/lib/libpng12.so.0
#2  0x08f1b998 in ?? ()
#3  0xffffffff in ?? ()
#4  0x00000008 in ?? ()
#5  0x0000000f in ?? ()
#6  0x00000008 in ?? ()
#7  0x00000001 in ?? ()
#8  0xb61b5789 in ?? () from /usr/lib/libpng12.so.0
#9  0x00000038 in ?? ()
#10 0xb7eb6ff4 in ?? () from /lib/tls/i686/cmov/libc.so.6
#11 0xb61b7b58 in ?? () from /usr/lib/libpng12.so.0
#12 0x00000208 in ?? ()
#13 0xb61a2043 in ?? () from /usr/lib/libpng12.so.0
#14 0x08f1b8c8 in ?? ()
#15 0xb3a73d68 in ?? ()
#16 0x00000008 in ?? ()
#17 0x00000100 in ?? ()
#18 0x08c00000 in ?? ()
#19 0x00000002 in ?? ()
#20 0xff0a0000 in ?? ()
#21 0xb61b7b58 in ?? () from /usr/lib/libpng12.so.0
#22 0xb3a73ecb in ?? ()
#23 0x08f1bb90 in ?? ()
#24 0xb3a73ddc in ?? ()
#25 0xb61a93de in png_write_info_before_PLTE () from /usr/lib/libpng12.so.0
Backtrace stopped: frame did not save the PC

Thread 2 (Thread -1281999984 (LWP 14051)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ee98fc in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120e5b in ?? ()
#3  0xb7802b90 in ?? ()
#4  0xb7802b78 in ?? ()
#5  0xb3963058 in ?? ()
#6  0x00000000 in ?? ()

Thread 1 (Thread -1210648880 (LWP 13989)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7eebe1e in __lll_mutex_lock_wait ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ee7b74 in _L_mutex_lock_218 () from /lib/tls/i686/cmov/libpthread.so.0
#3  0xb7ee7609 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x0810dab8 in ?? ()
#5  0x082303c4 in ?? ()
#6  0xb2800010 in ?? ()
#7  0xbf9f4858 in ?? ()
#8  0x085ddc50 in ?? ()
#9  0x08efe420 in ?? ()
#10 0xb28cb678 in ?? ()
#11 0xbf9f4888 in ?? ()
#12 0x0811975b in mono_bounded_array_class_get ()
Backtrace stopped: frame did not save the PC
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)

```
Any help?

---

### Post by gobbles414 on 2008-03-08
KernelPanic14,

I can't help you to get F-Spot working correctly. But I can recommend a substitute program called gThumb. It's installed by default in Ubuntu.

---

### Post by Arthur Archnix on 2008-03-08
Yeah... F-Spot is a horrible application. Shouldn't even be installed. Second vote for gThumb.

If you must, you can try deleting your thumbnail cache.
```
cd ~/.thumbnails
rm -R fail
rm -R normal
ls
```
If something shows up after ls, delete that too.

---

### Post by KernelPanic14 on 2008-03-10
Thank you for the replies,
but I prefer F-Spot over gThumb. I use gThumb for opening pictures & photos, but not for managing. I like both, but I use gThumb for previews, not for managing.
I already fixed the issue, it was some weirdo photos with weird tags.
Plus, I can't use the IcedTea Java plugin, I don't know why, so I have to use F-Spot Facebook plugin (which I prefer over the normal Java thing.)
Thanks anyway :D

---

### Post by gobbles414 on 2008-03-11
KernelPanic14,

Well, I'm glad that your problem is fixed. I still prefer gThumb. But everyone's entitled to his/her own opinion. :lolflag:

---

### Post by neighborlee on 2008-03-11
> **Arthur Archnix said:**
> Yeah... F-Spot is a horrible application. Shouldn't even be installed. Second vote for gThumb.

If you must, you can try deleting your thumbnail cache.
```
cd ~/.thumbnails
rm -R fail
rm -R normal
ls
```
If something shows up after ls, delete that too.

 3rd vote..get rid of fspot and err...nvm ;)

[https://bugs.launchpad.net/f-spot/+bug/34074](https://bugs.launchpad.net/f-spot/+bug/34074)



cheers
nl

---

### Post by neighborlee on 2008-03-12
> **KernelPanic14 said:**
> Thank you for the replies,
but I prefer F-Spot over gThumb. I use gThumb for opening pictures & photos, but not for managing. I like both, but I use gThumb for previews, not for managing.
I already fixed the issue, it was some weirdo photos with weird tags.
Plus, I can't use the IcedTea Java plugin, I don't know why, so I have to use F-Spot Facebook plugin (which I prefer over the normal Java thing.)
Thanks anyway :D

 I dont know if  this is any less crashy, but you might consider trying blue marine: [http://bluemarine.tidalwave.it/](http://bluemarine.tidalwave.it/)

It looks amazing and has  really nice feature set imo.

cheers
nl

---

