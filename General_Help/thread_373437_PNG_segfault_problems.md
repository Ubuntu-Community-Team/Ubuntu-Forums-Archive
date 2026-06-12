---
title: "PNG segfault problems"
date: 2007-03-01
forum: General Help
---

### Post by EReckase on 2007-03-01
I'm at my wit's end here, and I don't know how to solve this problem.

I recently built a new machine, an AMD X2 4600+ processor on an Asus M2N-SLI Deluxe motherboard, with 2 GB RAM.  I initially had Corsair memory, but when I started having these problems, I RMA'd it and got some Kingston RAM that was on the Asus 'Qualified Vendor List' - at a lower speed - but the problems remain. 

My problems relate to writing out PNG images.  There are three applications that I use that write out PNG files: GIMP, gnome-screenshot, and the flam3 IFS rendering engine.  The first two are fairly common, but the last is something I work on as a developer.

When I first got the machine, I went to benchmark the render speed of an image using the flam3 code, and while the first render went fine, the second one died with a Segmentation Fault.  Knowing of course that this is usually a programmer error, I spent two weeks trying to find the bug in my code, and was unable to find it.  

I know now, however, that it's not a problem with my code.  Intermittently, say, once every 5-10 snaps, gnome-screenshot fails, ALSO with a segmentation fault - the same segfault I get with my own code:

```
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb74d134b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f8e1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb73ff37c in memcpy () from /lib/tls/i686/cmov/libc.so.6
#5  0xb72c4e8d in deflateCopy () from /usr/lib/libz.so.1
#6  0xb72c5a44 in deflateInit_ () from /usr/lib/libz.so.1
#7  0xb72c5f10 in deflate () from /usr/lib/libz.so.1
#8  0xb7180101 in png_write_chunk () from /usr/lib/libpng12.so.0
#9  0xb718064b in png_write_chunk () from /usr/lib/libpng12.so.0
#10 0xb7184774 in png_write_row () from /usr/lib/libpng12.so.0
#11 0xb7184937 in png_write_rows () from /usr/lib/libpng12.so.0
#12 0xb6e94a79 in fill_info ()
   from /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
#13 0x08257ac0 in ?? ()
#14 0xbffee120 in ?? ()
#15 0x00000001 in ?? ()
#16 0x00000400 in ?? ()
#17 0x00000008 in ?? ()
#18 0x00000006 in ?? ()
#19 0x00000000 in ?? ()

Thread 1 (Thread -1224767824 (LWP 5590)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb74d134b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f8e1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb73ff37c in memcpy () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0xb72c4e8d in deflateCopy () from /usr/lib/libz.so.1
No symbol table info available.
#6  0xb72c5a44 in deflateInit_ () from /usr/lib/libz.so.1
No symbol table info available.
#7  0xb72c5f10 in deflate () from /usr/lib/libz.so.1
No symbol table info available.
#8  0xb7180101 in png_write_chunk () from /usr/lib/libpng12.so.0
No symbol table info available.
#9  0xb718064b in png_write_chunk () from /usr/lib/libpng12.so.0
No symbol table info available.
#10 0xb7184774 in png_write_row () from /usr/lib/libpng12.so.0
No symbol table info available.
#11 0xb7184937 in png_write_rows () from /usr/lib/libpng12.so.0
No symbol table info available.
#12 0xb6e94a79 in fill_info ()
   from /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
No symbol table info available.
#13 0x08257ac0 in ?? ()
No symbol table info available.
#14 0xbffee120 in ?? ()
No symbol table info available.
#15 0x00000001 in ?? ()
No symbol table info available.
#16 0x00000400 in ?? ()
No symbol table info available.
#17 0x00000008 in ?? ()
No symbol table info available.
#18 0x00000006 in ?? ()
No symbol table info available.
#19 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
```

To make sure it was the system and not my code, I attempted to save a PNG file from the Gimp - and I also have intermittent failures there as well.  It simply says 'failed: Plug-In could not save image', and leaves a partially saved image.

I've tried recompiling libpng and zlib, and linked both of those to the flam3 engine, and I still get the segmentation fault on an intermittent basis.

What else can I try?  Is it possible that I have a corrupt kernel and that's causing these problems?  If so, how would I reinstall the kernel?  Should I reinstall Edgy completely?  ANY recommendations at all would save me more headaches.  I'll be happy to provide any information requested to get to the bottom of this.  I am running kernel version 2.6.17.1-11.35, if that helps.

Erik

---

