---
title: "HLDS ERROR! im a noob"
date: 2008-06-30
forum: General Help
---

### Post by trillobite on 2008-06-30
I am trying to setup a Counterstrike Source dedicated server except the problem is i keep on getting errors! This is my system specs:
2.8GHz P4-Northwood
1GB DDR ram
60GB HDD
GeForce 6200 128MB


THIS IS WHAT HAPPENS IN THE TERMINAL:

I type in: ./srcds_run -console -game cstrike +map de_dust -maxplayers 16

Console initialized.
Game.dll loaded for "Counter-Strike: Source"
maxplayers set to 16
*** glibc detected *** ./srcds_i686: free(): invalid pointer: 0xb7d88000 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e5fd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e63800]
bin/dedicated_i686.so(_ZN15CBaseFileSystem12FastFindFileEPKNS_11CSearchPathEPKc+0x213)[0xb7d2b713]
======= Memory map: ========
08048000-08054000 r-xp 00000000 03:01 5439949    /home/jesse/srcds_i686
08054000-08056000 rwxp 0000c000 03:01 5439949    /home/jesse/srcds_i686
08056000-081ec000 rwxp 08056000 00:00 0          [heap]
b1e00000-b1e21000 rwxp b1e00000 00:00 0 
b1e21000-b1f00000 ---p b1e21000 00:00 0 
b1f9d000-b5f9e000 rwxp b1f9d000 00:00 0 
b5f9e000-b6b07000 r-xp 00000000 03:01 5457227    /home/jesse/cstrike/bin/server_i486.so
b6b07000-b6bee000 rwxp 00b68000 03:01 5457227    /home/jesse/cstrike/bin/server_i486.so
b6bee000-b6dec000 rwxp b6bee000 00:00 0 
b6e28000-b6e32000 r-xp 00000000 03:01 3047491    /lib/libgcc_s.so.1
b6e32000-b6e33000 rwxp 0000a000 03:01 3047491    /lib/libgcc_s.so.1
b6e3e000-b6e4d000 r-xp 00000000 03:01 2195467    /home/jesse/bin/shaderapiempty_i486.so
b6e4d000-b6e4e000 rwxp 0000f000 03:01 2195467    /home/jesse/bin/shaderapiempty_i486.so
b6e4e000-b6e60000 r-xp 00000000 03:01 2195470    /home/jesse/bin/steam_api_i486.so
b6e60000-b6e62000 rwxp 00011000 03:01 2195470    /home/jesse/bin/steam_api_i486.so
b6e62000-b6e66000 rwxp b6e62000 00:00 0 
b6e66000-b6fe8000 r-xp 00000000 03:01 2195464    /home/jesse/bin/libsteamvalidateuseridtickets_i486.so
b6fe8000-b700f000 rwxp 00182000 03:01 2195464    /home/jesse/bin/libsteamvalidateuseridtickets_i486.so
b700f000-b7014000 rwxp b700f000 00:00 0 
b7014000-b73e3000 r-xp 00000000 03:01 2195463    /home/jesse/bin/engine_i686.so
b73e3000-b7435000 rwxp 003ce000 03:01 2195463    /home/jesse/bin/engine_i686.so
b7435000-b74ac000 rwxp b7435000 00:00 0 
b74ac000-b7505000 r-xp 00000000 03:01 2195457    /home/jesse/bin/datacache_i486.so
b7505000-b750b000 rwxp 00058000 03:01 2195457    /home/jesse/bin/datacache_i486.so
b750b000-b750d000 rwxp b750b000 00:00 0 
b750d000-b7767000 r-xp 00000000 03:01 2195476    /home/jesse/bin/vphysics_i486.so
b7767000-b7786000 rwxp 00259000 03:01 2195476    /home/jesse/bin/vphysics_i486.so
b7786000-b779c000 rwxp b7786000 00:00 0 
b779c000-b7814000 r-xp 00000000 03:01 2195472    /home/jesse/bin/studiorender_i486.so
b7814000-b7818000 rwxp 00078000 03:01 2195472    /home/jesse/bin/studiorender_i486.so
b7818000-b7b95000 rwxp b7818000 00:00 0 
b7b95000-b7c81000 r-xp 00000000 03:01 2195465    /home/jesse/bin/materialsystem_i486.so
b7c81000-b7c8c000 rwxp 000ec000 03:01 2195465    /home/jesse/bin/materialsystem_i486.so
b7c8c000-b7ca3000 rwxp b7c8c000 00:00 0 
b7ca3000-b7cdb000 r-xp 00000000 03:01 2195469    /home/jesse/bin/soundemittersystem_i486.so
b7cdb000-b7cdf000 rwxp 00038000 03:01 2195469    /home/jesse/bin/soundemittersystem_i486.so
b7cdf000-b7ce1000 rwxp b7cdf000 00:00 0 
b7ce1000-b7d7b000 r-xp 00000000 03:01 2195460    /home/jesse/bin/dedicated_i686.so
b7d7b000-b7d85000 rwxp 00099000 03:01 2195460    /home/jesse/bin/dedicated_i686.so
b7d85000-b7d93000 rwxp b7d85000 00:00 0 
b7d93000-b7da5000 r-xp 00000000 03:01 2195477    /home/jesse/bin/vstdlib_i486.so
b7da5000-b7da7000 rwxp 00011000 03:01 2195477    /home/jesse/bin/vstdlib_i486.so
b7da7000-b7dbb000 r-xp 00000000 03:01 3081177    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7dbb000-b7dbd000 rwxp 00013000 03:01 3081177    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7dbd000-b7dbf000 rwxp b7dbd000 00:00 0 
b7dbf000-b7deb000 r-xp 00000000 03:01 2195473    /home/jesse/bin/tier0_i486.so
b7deb000-b7dee000 rwxp 0002b000 03:01 2195473    /home/jesse/bin/tier0_i486.so
b7dee000-b7df6000 rwxp b7dee000 00:00 0 
b7df6000-b7f3a000 r-xp 00000000 03:01 3081163    /lib/tls/i686/cmov/libc-2.6.1.so
b7f3a000-b7f3b000 r-xp 00143000 03:01 3081163    /lib/tls/i686/cmov/libc-2.6.1.so
b7f3b000-b7f3d000 rwxp 00144000 03:01 3081163    /lib/tls/i686/cmov/libc-2.6.1.so
b7f3d000-b7f41000 rwxp b7f3d000 00:00 0 
b7f41000-b7f43000 r-xp 00000000 03:01 3081166    /lib/tls/i686/cmov/libdl-2.6.1.so
b7f43000-b7f45000 rwxp 00001000 03:01 3081166    /lib/tls/i686/cmov/libdl-2.6.1.so
b7f45000-b7f68000 r-xp 00000000 03:01 3081167    /lib/tls/i686/cmov/libm-2.6.1.so
b7f68000-b7f6a000 rwxp 00023000 03:01 3081167    /lib/tls/i686/cmov/libm-2.6.1.so
b7f6c000-b7f73000 r-xp 00000000 03:01 2195466    /home/jesse/bin/scenefilecache_i486.so
b7f73000-b7f74000 rwxp 00007000 03:01 2195466    /home/jesse/bin/scenefilecache_i486.so
b7f74000-b7f77000 rwxp b7f74000 00:00 0 
b7f77000-b7f91000 r-xp 00000000 03:01 3047492    /lib/ld-2.6.1.so
b7f91000-b7f93000 rwxp 00019000 03:01 3047492    /lib/ld-2.6.1.so
bf8c8000-bf8de000 rwxp bf8c8000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

NOW THE DEBUG.LOG

CRASH: Mon Jun 30 17:21:14 PDT 2008
Start Line: ./srcds_i686 -console -game cstrike +map de_dust -maxplayers 16 -debug
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Core was generated by `./srcds_i686 -debug -game cstrike'.
Program terminated with signal 6, Aborted.
#0  0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e82875 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e84201 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7eb9e5c in ?? () from /lib/tls/i686/cmov/libc.so.6
#4  0x00000005 in ?? ()
#5  0xbfb1b594 in ?? ()
#6  0x00000400 in ?? ()
#7  0xb7f840c8 in ?? () from /lib/tls/i686/cmov/libc.so.6
#8  0x00000017 in ?? ()
#9  0xbfb2491c in ?? ()
#10 0x0000000c in ?? ()
#11 0xb7f840e1 in ?? () from /lib/tls/i686/cmov/libc.so.6
#12 0x00000002 in ?? ()
#13 0xb7f810c4 in ?? () from /lib/tls/i686/cmov/libc.so.6
#14 0x00000017 in ?? ()
#15 0xb7f840e5 in ?? () from /lib/tls/i686/cmov/libc.so.6
#16 0x00000004 in ?? ()
#17 0xbfb1bb0b in ?? ()
#18 0x00000008 in ?? ()
#19 0xb7f840eb in ?? () from /lib/tls/i686/cmov/libc.so.6
#20 0x00000005 in ?? ()
#21 0xbfb1b994 in ?? ()
#22 0x00000001 in ?? ()
#23 0x00000002 in ?? ()
#24 0x00000000 in ?? ()
No symbol table info available.
From        To          Syms Read   Shared Object Library
0xb7faa460  0xb7fc43f4  Yes         /lib/tls/i686/cmov/libm.so.6
0xb7fa3a70  0xb7fa4a74  Yes         /lib/tls/i686/cmov/libdl.so.2
0xb7e6de30  0xb7f6ab24  Yes         /lib/tls/i686/cmov/libc.so.6
0xb7fd97f0  0xb7fee1af  Yes         /lib/ld-linux.so.2
0xb7e2f190  0xb7e4a7c0  Yes         bin/tier0_i486.so
0xb7e0d250  0xb7e18224  Yes         /lib/tls/i686/cmov/libpthread.so.0
0xb7dfc910  0xb7e05ff0  Yes         bin/vstdlib_i486.so
0xb7d7dfb0  0xb7dd8060  Yes         bin/dedicated_i686.so
0xb7d19610  0xb7d3b190  Yes         bin/soundemittersystem_i486.so
0xb7c4a7e0  0xb7cdb210  Yes         bin/materialsystem_i486.so
0xb78222c0  0xb7874820  Yes         bin/studiorender_i486.so
0xb76266a0  0xb77b12b0  Yes         bin/vphysics_i486.so
0xb752c580  0xb7565180  Yes         bin/datacache_i486.so
0xb71e1af0  0xb74013f0  Yes         bin/engine_i686.so
0xb6f6b410  0xb7031040  Yes         bin/libsteamvalidateuseridtickets_i486.so
0xb6eb4b20  0xb6ec0500  Yes         bin/steam_api_i486.so
0xb6eab440  0xb6eadaa0  Yes         bin/shaderapiempty_i486.so
0xb6476990  0xb6aa2fd0  Yes         /home/jesse/cstrike/bin/server_i486.so
0xb7fd1530  0xb7fd4920  Yes         /home/jesse/bin/scenefilecache_i486.so
0xb6e8b970  0xb6e92e64  Yes         /lib/libgcc_s.so.1
Stack level 0, frame at 0xbfb1b324:
 eip = 0xffffe410 in __kernel_vsyscall; saved eip 0xb7e82875
 called by frame at 0xbfb1b338
 Arglist at 0xbfb1b31c, args: 
 Locals at 0xbfb1b31c, Previous frame's sp is 0xbfb1b324
 Saved registers:
  ebp at 0xbfb1b314, eip at 0xbfb1b320
End of Source crash report


lol, what is going on? i read so many other posts but no help at all, i went all over the internet!

---

### Post by ar0n on 2008-07-02
Hi!

Try unloading any custom mods installed like metamod etc... .
But I think this looks like you have memory problems.

Aron

---

