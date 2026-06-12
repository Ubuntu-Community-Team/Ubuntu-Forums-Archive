---
title: "kde4 desktop effects work until next login"
date: 2008-04-23
forum: General Help
---

### Post by attunezero on 2008-04-23
Turning on desktop effects in kde4 (gutsy or hardy, ubuntu or kubuntu) works great (just a little slow) on my inspiron 1420n with geforce 8400m... until i log out or reboot and try to log back in that is. There are no problems with desktop effects until i try to log in again, at which point i get the kde splash screen followed by a blank desktop with a cursor on it, nothing is being drawn. Startup sound and everything plays, and i can move the cursor around no problem. It seems that something is preventing kwin/plasma from drawing my desktop, or something is being drawn over it. Anybody have any knowledge of this problem? How can i turn the desktop effects off without deleting my whole .kde dir?

Edit: i once managed to get everything to display properly by pressing alt-f4 at the blank screen, apparently closing whatever window was causing the trouble, but i can not figure out what window that was.


Edit: running kwin from the failsafe console and doing a "ctl-c" after the blank screen comes up yeilds

X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xe00028
kwin(15220) KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/lib/kde4/kwin3_oxygen.so"  for  "kwin3_oxygen"
kwin(15220) KToolInvocation::klauncher: klauncher not running... launching kdeinit
kdeinit4: Shutting down running client.
kdeinit4: Killing kdeinit/klauncher.
kdeinit4: preparing to launch /usr/lib/kde4/lib/kde4/libexec/klauncher
kdeinit4: Launched KLauncher, pid = 15230 result = 0
kdeinit4: opened connection to :0.0
kdeinit4: preparing to launch /usr/lib/kde4/bin/kded4
kdeinit4: Launched KDED, pid = 15232 result = 0
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xe00028
kdeinit4: Got EXT_EXEC '/usr/lib/kde4/bin/kbuildsycoca4' from launcher.
kdeinit4: preparing to launch /usr/lib/kde4/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: PID 15236 terminated.
kdeinit4: Got EXEC_NEW 'kconf_update' from launcher.
kdeinit4: preparing to launch /usr/lib/kde4/lib/kde4/libexec/kconf_update
kdeinit4: PID 15238 terminated.
kdeinit4: PID 15232 terminated.
kdeinit4: Got EXT_EXEC '/usr/lib/kde4/bin/knotify4' from launcher.
kdeinit4: preparing to launch /usr/lib/kde4/bin/knotify4
kdeinit4: PID 15239 terminated.
kwin(15220): Couldn't start knotify from knotify4.desktop:  "KDEInit could not launch '/usr/lib/kde4/bin/knotify4'."

knotify(15240) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
*** glibc detected *** kwin: corrupted double-linked list: 0x08153158 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7de0d0d]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7de44f0]
/usr/lib/libGL.so.1[0xb6e88c51]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:03 2843531    /usr/lib/kde4/bin/kwin
08049000-0804a000 rw-p 00000000 08:03 2843531    /usr/lib/kde4/bin/kwin
0804a000-08555000 rw-p 0804a000 00:00 0          [heap]
b2eb2000-b2f43000 r--p 00000000 08:03 3039356    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b2f4a000-b314a000 rw-s 326ab000 00:0e 13562      /dev/nvidia0
b4020000-b406c000 r-xp 00000000 08:03 2965674    /usr/lib/qt4/plugins/imageformats/libqtiff.so
b406c000-b406e000 rw-p 0004c000 08:03 2965674    /usr/lib/qt4/plugins/imageformats/libqtiff.so
b406e000-b409b000 r-xp 00000000 08:03 2819833    /usr/lib/liblcms.so.1.0.16
b409b000-b409d000 rw-p 0002c000 08:03 2819833    /usr/lib/liblcms.so.1.0.16
b409d000-b409f000 rw-p b409d000 00:00 0
b409f000-b410a000 r-xp 00000000 08:03 2819860    /usr/lib/libmng.so.1.1.0.9
b410a000-b410d000 rw-p 0006a000 08:03 2819860    /usr/lib/libmng.so.1.1.0.9
b4118000-b411b000 r-xp 00000000 08:03 2965673    /usr/lib/qt4/plugins/imageformats/libqsvg.so
b411b000-b411c000 rw-p 00002000 08:03 2965673    /usr/lib/qt4/plugins/imageformats/libqsvg.so
b411c000-b4120000 r-xp 00000000 08:03 2965672    /usr/lib/qt4/plugins/imageformats/libqmng.so
b4120000-b4121000 rw-p 00004000 08:03 2965672    /usr/lib/qt4/plugins/imageformats/libqmng.so
b4121000-b4129000 r-xp 00000000 08:03 2965671    /usr/lib/qt4/plugins/imageformats/libqjpeg.so
b4129000-b412a000 rw-p 00007000 08:03 2965671    /usr/lib/qt4/plugins/imageformats/libqjpeg.so
b412a000-b412f000 r-xp 00000000 08:03 2965670    /usr/lib/qt4/plugins/imageformats/libqgif.so
b412f000-b4130000 rw-p 00004000 08:03 2965670    /usr/lib/qt4/plugins/imageformats/libqgif.so
b4130000-b413e000 r-xp 00000000 08:03 2851038    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_xcf.so
b413e000-b413f000 rw-p 0000d000 08:03 2851038    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_xcf.so
b413f000-b4143000 rw-p b413f000 00:00 0
b4143000-b414d000 r-xp 00000000 08:03 2851036    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_rgb.so
b414d000-b414e000 rw-p 0000a000 08:03 2851036    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_rgb.so
b414e000-b416d000 r-xp 00000000 08:03 2819629    /usr/lib/libjpeg.so.62.0.0
b416d000-b416e000 rw-p 0001e000 08:03 2819629    /usr/lib/libjpeg.so.62.0.0
b416e000-b41b2000 r-xp 00000000 08:03 2819627    /usr/lib/libjasper.so.1.0.0
b41b2000-b41b5000 rw-p 00044000 08:03 2819627    /usr/lib/libjasper.so.1.0.0
b41b5000-b41bb000 rw-p b41b5000 00:00 0
b41bd000-b41c3000 r-xp 00000000 08:03 2851037    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_tga.so
b41c3000-b41c4000 rw-p 00005000 08:03 2851037    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_tga.so
b41c4000-b41c9000 r-xp 00000000 08:03 2851035    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_psd.so
b41c9000-b41ca000 rw-p 00004000 08:03 2851035    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_psd.so
b41ca000-b420c000 r-xp 00000000 08:03 2819168    /usr/lib/libHalf.so.2.0.2
b420c000-b420d000 rw-p 00041000 08:03 2819168    /usr/lib/libHalf.so.2.0.2
b420d000-b4221000 r-xp 00000000 08:03 2819175    /usr/lib/libIex.so.2.0.2
b4221000-b4223000 rw-p 00013000 08:03 2819175    /usr/lib/libIex.so.2.0.2
b4223000-b4298000 r-xp 00000000 08:03 2819177    /usr/lib/libIlmImf.so.2.0.2
b4298000-b429a000 rw-p 00074000 08:03 2819177    /usr/lib/libIlmImf.so.2.0.2
b429a000-b42cf000 r-xp 00000000 08:03 2844042    /usr/lib/kde4/lib/kde4/kwin4_effect_builtins.so
b42cf000-b42d1000 rw-p 00034000 08:03 2844042    /usr/lib/kde4/lib/kde4/kwin4_effect_builtins.so
b438e000-b458e000 rw-s 324cd000 00:0e 13562      /dev/nvidia0
b4699000-b469a000 rw-s fdc08000 00:0e 13562      /dev/nvidia0
b46fb000-b46fc000 rw-s 1fb23000 00:0e 13562      /dev/nvidia0
b4723000-b4727000 r-xp 00000000 08:03 2851039    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_xview.so
b4727000-b4728000 rw-p 00004000 08:03 2851039    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_xview.so
b4728000-b4730000 r-xp 00000000 08:03 2851034    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_pcx.so
b4730000-b4731000 rw-p 00008000 08:03 2851034    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_pcx.so
b4731000-b4736000 r-xp 00000000 08:03 2851033    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_jp2.so
b4736000-b4737000 rw-p 00005000 08:03 2851033    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_jp2.so
b4737000-b473d000 r-xp 00000000 08:03 2851032    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_ico.so
b473d000-b473e000 rw-p 00005000 08:03 2851032    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_ico.so
b473e000-b4744000 r-xp 00000000 08:03 2851031    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_exr.so
b4744000-b4745000 rw-p 00005000 08:03 2851031    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_exr.so
b4745000-b474c000 r-xp 00000000 08:03 2851030    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_eps.so
b474c000-b474d000 rw-p 00007000 08:03 2851030    /usr/lib/kde4/lib/kde4/plugins/imageformats/kimg_eps.so
b474d000-b4754000 r-xp Application::crashHandler() called with signal 6; recent crashes: 1
sh: kwin: not found
KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = kwin path = <unknown> pid = 15220
Fatal Error: Accessed global static 'KGlobalPrivate *globalData()' after destruction. Defined at /build/buildd/kde4libs-4.0.3/kdecore/kernel/kglobal.cpp:86
Unable to start Dr. Konqi



Where i assume the problem is probably

X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xe00028

and the rest is likely a backtrace from my killing kwin, but i do not know what this means or what could be causing it since the effects work fine until a login.

---

### Post by umberleigh on 2008-05-08
I was having similar problems. It seems to be caused by Compiz Fusion desktop effects. check [here]("http://ubuntuforums.org/showthread.php?p=4903202") for a fix.

---

