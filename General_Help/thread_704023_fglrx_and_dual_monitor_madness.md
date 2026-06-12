---
title: "fglrx and dual monitor madness"
date: 2008-02-21
forum: General Help
---

### Post by approaching on 2008-02-21
So i have lived with either compiz and my monitors not maximizing right because i use two, or i have gotten them to maximize right, and not had compiz. This is mainly due to my fglrx driver not being set up correctly. After some time, i figured it was worth not having all the glitz to have my desktop work correctly so i have been using that. but just today, i figured i would delve into this frustrating mess again to see if i could get everything working.

so now i can technically get the fglrx running, but when i try to do the aticonfig --initial command to see if i can get the dual monitor working (it has in the past without compiz, and that is how i normally have run) i get some madness that looks like this:

sudo aticonfig --dtop=horizontal --overlay-on=1
[sudo] password for vgrato:
Warning: Failed to set hardware overlay to head 1 immediately.
Warning: Option 'DesktopSetup' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-6
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfd079d2 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d1d92b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cc6050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 fe:00 24707635   /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 fe:00 24707635   /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7ca2000-b7ca3000 rw-p b7ca2000 00:00 0 
b7ca3000-b7ca5000 r-xp 00000000 fe:00 21331992   /lib/tls/i686/cmov/libdl-2.6.1.so
b7ca5000-b7ca7000 rw-p 00001000 fe:00 21331992   /lib/tls/i686/cmov/libdl-2.6.1.so
b7ca7000-b7ca8000 rw-p b7ca7000 00:00 0 
b7ca8000-b7cac000 r-xp 00000000 fe:00 24707970   /usr/lib/libXdmcp.so.6.0.0
b7cac000-b7cad000 rw-p 00003000 fe:00 24707970   /usr/lib/libXdmcp.so.6.0.0
b7cad000-b7caf000 r-xp 00000000 fe:00 24707968   /usr/lib/libXau.so.6.0.0
b7caf000-b7cb0000 rw-p 00001000 fe:00 24707968   /usr/lib/libXau.so.6.0.0
b7cb0000-b7df4000 r-xp 00000000 fe:00 21331989   /lib/tls/i686/cmov/libc-2.6.1.so
b7df4000-b7df5000 r--p 00143000 fe:00 21331989   /lib/tls/i686/cmov/libc-2.6.1.so
b7df5000-b7df7000 rw-p 00144000 fe:00 21331989   /lib/tls/i686/cmov/libc-2.6.1.so
b7df7000-b7dfa000 rw-p b7df7000 00:00 0 
b7dfa000-b7e1d000 r-xp 00000000 fe:00 21331993   /lib/tls/i686/cmov/libm-2.6.1.so
b7e1d000-b7e1f000 rw-p 00023000 fe:00 21331993   /lib/tls/i686/cmov/libm-2.6.1.so
b7e1f000-b7f0c000 r-xp 00000000 fe:00 24707973   /usr/lib/libX11.so.6.2.0
b7f0c000-b7f10000 rw-p 000ed000 fe:00 24707973   /usr/lib/libX11.so.6.2.0
b7f10000-b7f1d000 r-xp 00000000 fe:00 24708351   /usr/lib/libXext.so.6.4.0
b7f1d000-b7f1e000 rw-p 0000d000 fe:00 24708351   /usr/lib/libXext.so.6.4.0
b7f1e000-b7f1f000 rw-p b7f1e000 00:00 0 
b7f1f000-b7f26000 r-xp 00000000 fe:00 24707978   /usr/lib/libXrender.so.1.3.0
b7f26000-b7f27000 rw-p 00006000 fe:00 24707978   /usr/lib/libXrender.so.1.3.0
b7f27000-b7f2c000 r-xp 00000000 fe:00 24708604   /usr/lib/libXrandr.so.2.1.0
b7f2c000-b7f2d000 rw-p 00005000 fe:00 24708604   /usr/lib/libXrandr.so.2.1.0
b7f2d000-b7f37000 r-xp 00000000 fe:00 21332030   /lib/libgcc_s.so.1
b7f37000-b7f38000 rw-p 0000a000 fe:00 21332030   /lib/libgcc_s.so.1
b7f38000-b7f3b000 rw-p b7f38000 00:00 0 
b7f3b000-b7f55000 r-xp 00000000 fe:00 21331978   /lib/ld-2.6.1.so
b7f55000-b7f57000 rw-p 00019000 fe:00 21331978   /lib/ld-2.6.1.so
bfcf3000-bfd09000 rw-p bfcf3000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

sorry for the huge code dump, but this has been getting me rather upset, and now i can't get it to get off of the mode where it maximizes across both monitors i have poked around and used some of these tutorials to  get the dual monitor working, but they didn't do anything for me, so i reverted the xorg.conf to a backup that i had made.

Please let me know any ideas!

---

### Post by kokiri on 2008-02-21
Well, what you have there is aticonfig throwing a huge fit and seg faulting on you.
Meaning that for some reason, old driver, old aticonfig, too new of a kernel, something - is causing aticonfig to crash so badly that it can't recover and is just bailing on you. Hence the core dump.

You'll need to sort that out before anything else can get fixed.

---

### Post by approaching on 2008-02-21
now i know this is lame of me, but i have actualy reinstalled the os a few times because of this. The first time, if i don't mess with compiz, and just get the fglrx, then the aticonfig, it works. but after that, if you try to switch off the fglrx or delve into getting compiz working it would do this. This isn't the first time this has showed up while using the same versions that work the first time, but not after. I would only admit that if i thought it meant something, but i am always way to cautious to report a bug of some type because i am never sure if it is me that is at fault.

---

### Post by approaching on 2008-02-22
so, compiz is working right now, but the dual monitor functionality is still broken, and if i try and do the aticonfig, i still get the same output.

...

is this an issue with aticonfig?

---

### Post by kokiri on 2008-02-24
if you can get your monitor card to do the 3d natively ( not software emulated ) then there are ways of coaxing your xorg.conf to kick the other head in your card on
if you can open a terminal and type:
glxinfo
and see a bunch of output spewed out, then your card is working for 3d natively and we can configure xorg.conf by hand to get it working and forget about that fluffy aticonfig trash

btw - if you're seriously going to run linux for the long term, never, never, never buy another ati card again...they suck on the driver end big time and lead to way more headaches than they're worth. Just my 2 cents.

---

### Post by Yellow Pasque on 2008-02-24
You need to be using Compiz 0.7 or greater for multi-monitor support.

---

