---
title: "Want to convert but"
date: 2008-01-18
forum: General Help
---

### Post by chrissimpson156 on 2008-01-18
The last time I tried Ubuntu I had a few problems:

* The max resolution I could select was 1024x768. Which was rather low, the native resolution for my LCD is 1280x1024. So everything looked a bit blocky. I have a second LCD with a 16:10 aspect ratio with similar problems.

* I have a 42" Plasma connected to the DVI output on my graphics card that I used again for watching movies, it is completely blank. The only resolution this supports is 1024x768. On Windows I have this as an extended rather than a clone of my primary desktop. The card is an ATI Radeon X1050

* The graphics seemed very slow, moving windows and scrolling web pages leaves a very noticeable and annoying delay as it redraws the entire window.

* Creating play lists in VLC via drag and drop does not work for some reason. Adding stuff with the built in dialogs is very slow and cumbersome.

* The only sound being output was analog stereo. Nothing over SPDIF, which is what I need for a lot of the movies I watch.

I am considering trying Ubuntu again as I have a free weekend. Is there anything in the above wish list that is not possible to fix? Also does anybody else have any advice or quick tips that might help?

Thanks a lot!

Chris

---

### Post by bodhi.zazen on 2008-01-18
Sounds like you should try the ATI drivers.

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

### Post by zero-9376 on 2008-01-18
the first 3 of those issues are indeed likely to be resolved by installing the binary drivers from ati (using restricted driver manager). 

drag and drop in vlc works on my system so it may have improved since you last used ubuntu.

ive never used spdif so i cant offer advice the only thing i can say is you may want to search these forums and providing the model of your soundcard may help, as always google can also help.

---

### Post by chrissimpson156 on 2008-01-18
Well I attempted to run the ati config utility, the following error occured:

sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-2
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfbc49ef ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d3392b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cdc050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:01 432844     /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:01 432844     /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7ca2000-b7cac000 r-xp 00000000 08:01 318787     /lib/libgcc_s.so.1
b7cac000-b7cad000 rw-p 0000a000 08:01 318787     /lib/libgcc_s.so.1
b7cb8000-b7cb9000 rw-p b7cb8000 00:00 0 
b7cb9000-b7cbb000 r-xp 00000000 08:01 351283     /lib/tls/i686/cmov/libdl-2.6.1.so
b7cbb000-b7cbd000 rw-p 00001000 08:01 351283     /lib/tls/i686/cmov/libdl-2.6.1.so
b7cbd000-b7cbe000 rw-p b7cbd000 00:00 0 
b7cbe000-b7cc2000 r-xp 00000000 08:01 431603     /usr/lib/libXdmcp.so.6.0.0
b7cc2000-b7cc3000 rw-p 00003000 08:01 431603     /usr/lib/libXdmcp.so.6.0.0
b7cc3000-b7cc5000 r-xp 00000000 08:01 431592     /usr/lib/libXau.so.6.0.0
b7cc5000-b7cc6000 rw-p 00001000 08:01 431592     /usr/lib/libXau.so.6.0.0
b7cc6000-b7e0a000 r-xp 00000000 08:01 351280     /lib/tls/i686/cmov/libc-2.6.1.so
b7e0a000-b7e0b000 r--p 00143000 08:01 351280     /lib/tls/i686/cmov/libc-2.6.1.so
b7e0b000-b7e0d000 rw-p 00144000 08:01 351280     /lib/tls/i686/cmov/libc-2.6.1.so
b7e0d000-b7e10000 rw-p b7e0d000 00:00 0 
b7e10000-b7e33000 r-xp 00000000 08:01 351284     /lib/tls/i686/cmov/libm-2.6.1.so
b7e33000-b7e35000 rw-p 00023000 08:01 351284     /lib/tls/i686/cmov/libm-2.6.1.so
b7e35000-b7f22000 r-xp 00000000 08:01 431586     /usr/lib/libX11.so.6.2.0
b7f22000-b7f26000 rw-p 000ed000 08:01 431586     /usr/lib/libX11.so.6.2.0
b7f26000-b7f33000 r-xp 00000000 08:01 431607     /usr/lib/libXext.so.6.4.0
b7f33000-b7f34000 rw-p 0000d000 08:01 431607     /usr/lib/libXext.so.6.4.0
b7f34000-b7f35000 rw-p b7f34000 00:00 0 
b7f35000-b7f3c000 r-xp 00000000 08:01 431629     /usr/lib/libXrender.so.1.3.0
b7f3c000-b7f3d000 rw-p 00006000 08:01 431629     /usr/lib/libXrender.so.1.3.0
b7f3d000-b7f42000 r-xp 00000000 08:01 431627     /usr/lib/libXrandr.so.2.1.0
b7f42000-b7f43000 rw-p 00005000 08:01 431627     /usr/lib/libXrandr.so.2.1.0
b7f4d000-b7f50000 rw-p b7f4d000 00:00 0 
b7f50000-b7f6a000 r-xp 00000000 08:01 318733     /lib/ld-2.6.1.so
b7f6a000-b7f6c000 rw-p 00019000 08:01 318733     /lib/ld-2.6.1.so
bfbb0000-bfbc5000 rw-p bfbb0000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)


I replaced the backup file and ran sudo aticonfig --initial --force instread. That worked, but then I got another core dump error when running sudo aticonfig --overlay-type=Xv

Any ideas?

---

