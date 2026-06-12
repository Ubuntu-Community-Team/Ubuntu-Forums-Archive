---
title: "Strange 10 Seconds Login Error"
date: 2007-05-24
forum: General Help
---

### Post by Ziox on 2007-05-24
Here's the background information.

I'm running Ubuntu Feisty on HP Pavillion Laptop with a nVidia graphics card.  Aside from the standard packages, I've also installed Beryl, which is run with nVidia's own implementation of composite desktop.  It worked perfectly for about 1 month.

Here's the problem:

About 3 days ago, I was working in the desktop environment, then I had to edit several files from virtual terminal (ctrl + alt + f1).  After which, I switched back to the GUI environment (ctrl + alt + f7) with beryl running, the screen remained black, with the cursor still showing.  After a few minutes, no I/O registration.  Therefore, I was forced to hard reboot the computer.  When I log in, I receive a 10 seconds login error and the output of xsession-errors, which I've posted below:

```
Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "xavier"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Toybox:/tmp/.ICE-unix/6427
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Initializing gnome-mount extension

** (gsynaptics-init:6524): WARNING **: Using synclient
*** glibc detected *** x-session-manager: malloc(): memory corruption (fast): 0x082a4fc8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75c16fc]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb75c260e]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb76d82c6]
/usr/lib/libgdk-x11-2.0.so.0[0xb7a6ddb0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_intersect+0x99)[0xb7a6f1e9]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_maybe_recurse+0x10d)[0xb7a72f2d]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_region+0x40)[0xb7a731c0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_rect+0xaf)[0xb7a7327f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_queue_draw_area+0x150)[0xb7d28440]
x-session-manager[0x805ce05]
/usr/lib/libglib-2.0.so.0[0xb76d13c6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb76d0df2]
/usr/lib/libglib-2.0.so.0[0xb76d3dcf]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x65)[0xb76d4335]
x-session-manager[0x8055789]
/usr/lib/libglib-2.0.so.0[0xb76fa40d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb76d0df2]
/usr/lib/libglib-2.0.so.0[0xb76d3dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb76d4179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c08044]
x-session-manager(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb756eebc]
x-session-manager[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:03 186285     /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 08:03 186285     /usr/bin/gnome-session
08069000-082ef000 rw-p 08069000 00:00 0          [heap]
b4700000-b4721000 rw-p b4700000 00:00 0 
b4721000-b4800000 ---p b4721000 00:00 0 
b489e000-b48a9000 r-xp 00000000 08:03 163214     /lib/libgcc_s.so.1
b48a9000-b48aa000 rw-p 0000a000 08:03 163214     /lib/libgcc_s.so.1
b48b9000-b48bc000 r-xp 00000000 08:03 281545     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-ico.so
b48bc000-b48bd000 rw-p 00002000 08:03 281545     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-ico.so
b48bd000-b48be000 ---p b48bd000 00:00 0 
b48be000-b50be000 rw-p b48be000 00:00 0 
b50be000-b513b000 r--p 00000000 08:03 261881     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b513b000-b513d000 r-xp 00000000 08:03 281357     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b513d000-b513e000 rw-p 00001000 08:03 281357     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b513e000-b5141000 r--s 00000000 08:03 655493     /var/cache/fontconfig/5e10083637a12ecd1bff191eb66bfa2f-x86.cache-2
b5141000-b5144000 r--s 00000000 08:03 655492     /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86.cache-2
b5144000-b514a000 r--s 00000000 08:03 655434     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b514a000-b514d000 r--s 00000000 08:03 655432     /var/cache/fontconfig/a46337af8a0b4c9b317ad981ec3bdf87-x86.cache-2
b514d000-b514e000 r--s 00000000 08:03 655489     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b514e000-b5151000 r--s 00000000 08:03 655488     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b5151000-b5152000 r--s 00000000 08:03 655487     /var/cache/fontconfig/6edd069ccec3ba28096b368c434fa861-x86.cache-2
b5152000-b5153000 r--s 00000000 08:03 655486     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b5153000-b5154000 r--s 00000000 08:03 655485     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b5154000-b5158000 r--s 00000000 08:03 655426     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b5158000-b5173000 r--s 00000000 08:03 655483     /var/cache/fontconfig/4ca92cf76c0cf3dfa7f011127eff595d-x86.cache-2
b5173000-b518f000 r--s 00000000 08:03 655482     /var/cache/fontconfig/6abf76b0b4cc7192703d8431ac929b75-x86.cache-2
b518f000-b51ad000 r--s 00000000 08:03 655481     /var/cache/fontconfig/f408d08d2fce062ab660f628db78bf96-x86.cache-2
b51ad000-b51ae000 r--s 00000000 08:03 655480     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b51ae000-b51b0000 r--s 00000000 08:03 655479     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b51b0000-b51b2000 r--s 00000000 08:03 655478     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b51b2000-b51b3000 r--s 00000000 08:03 655477     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
```

I've seen this error reported before, however, I want to offer something interesting.  After the initial login (which gives me the 10 seconds login error), I started metacity, which was shut down when the login crashed, and I enter "x-session-manager" in terminal.  Now there are two sessions layered on top of one another.  The interesting point is that when I start session from terminal, there was no error. In other words, beryl started correctly, without crashing.  Hopefully someone is able to fix this error.  If more information is needed, I'll gladly post them.

---

