---
title: "CS: Source server- Help?"
date: 2008-06-25
forum: General Help
---

### Post by trillobite on 2008-06-25
yup, im trying to start a CS: Source server, and i came to a couple problems (i read all the posts about CS: Source server problems and helps and none of them so far have been able to help me, probably mostly because of my little knowledge in linux). 

Here is everything the terminal said:

jesse@jesse-desktop:~$ ./srcds_run -console -game cstrike +map de_dust -maxplayers 16 -autoupdate -norestart
Auto detecting CPU
Using SSE2 Optimised binary.
Updating server using Steam.
Checking bootstrapper version ...
Updating Installation
Cannot open output file './InstallRecord.blob'
Wed Jun 25 10:21:42 PDT 2008: Steam Update failed, ignoring.

Console initialized.
Game.dll loaded for "Counter-Strike: Source"
maxplayers set to 16
*** glibc detected *** ./srcds_i686: free(): invalid pointer: 0xb7d73000 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e4ad65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e4e800]
bin/dedicated_i686.so(_ZN15CBaseFileSystem12FastFindFileEPKNS_11CSearchPathEPKc+0x213)[0xb7d16713]
======= Memory map: ========
08048000-08054000 r-xp 00000000 03:01 5439949    /home/jesse/srcds_i686
08054000-08056000 rwxp 0000c000 03:01 5439949    /home/jesse/srcds_i686
08056000-081ec000 rwxp 08056000 00:00 0          [heap]
b1e00000-b1e21000 rwxp b1e00000 00:00 0 
b1e21000-b1f00000 ---p b1e21000 00:00 0 
b1f88000-b5f89000 rwxp b1f88000 00:00 0 
b5f89000-b6af2000 r-xp 00000000 03:01 5457227    /home/jesse/cstrike/bin/server_i486.so
b6af2000-b6bd9000 rwxp 00b68000 03:01 5457227    /home/jesse/cstrike/bin/server_i486.so
b6bd9000-b6dd7000 rwxp b6bd9000 00:00 0 
b6e13000-b6e1d000 r-xp 00000000 03:01 3047491    /lib/libgcc_s.so.1
b6e1d000-b6e1e000 rwxp 0000a000 03:01 3047491    /lib/libgcc_s.so.1
b6e29000-b6e38000 r-xp 00000000 03:01 2195467    /home/jesse/bin/shaderapiempty_i486.so
b6e38000-b6e39000 rwxp 0000f000 03:01 2195467    /home/jesse/bin/shaderapiempty_i486.so
b6e39000-b6e4b000 r-xp 00000000 03:01 2195470    /home/jesse/bin/steam_api_i486.so
b6e4b000-b6e4d000 rwxp 00011000 03:01 2195470    /home/jesse/bin/steam_api_i486.so
b6e4d000-b6e51000 rwxp b6e4d000 00:00 0 
b6e51000-b6fd3000 r-xp 00000000 03:01 2195464    /home/jesse/bin/libsteamvalidateuseridtickets_i486.so
b6fd3000-b6ffa000 rwxp 00182000 03:01 2195464    /home/jesse/bin/libsteamvalidateuseridtickets_i486.so
b6ffa000-b6fff000 rwxp b6ffa000 00:00 0 
b6fff000-b73ce000 r-xp 00000000 03:01 2195463    /home/jesse/bin/engine_i686.so
b73ce000-b7420000 rwxp 003ce000 03:01 2195463    /home/jesse/bin/engine_i686.so
b7420000-b7497000 rwxp b7420000 00:00 0 
b7497000-b74f0000 r-xp 00000000 03:01 2195457    /home/jesse/bin/datacache_i486.so
b74f0000-b74f6000 rwxp 00058000 03:01 2195457    /home/jesse/bin/datacache_i486.so
b74f6000-b74f8000 rwxp b74f6000 00:00 0 
b74f8000-b7752000 r-xp 00000000 03:01 2195476    /home/jesse/bin/vphysics_i486.so
b7752000-b7771000 rwxp 00259000 03:01 2195476    /home/jesse/bin/vphysics_i486.so
b7771000-b7787000 rwxp b7771000 00:00 0 
b7787000-b77ff000 r-xp 00000000 03:01 2195472    /home/jesse/bin/studiorender_i486.so
b77ff000-b7803000 rwxp 00078000 03:01 2195472    /home/jesse/bin/studiorender_i486.so
b7803000-b7b80000 rwxp b7803000 00:00 0 
b7b80000-b7c6c000 r-xp 00000000 03:01 2195465    /home/jesse/bin/materialsystem_i486.so
b7c6c000-b7c77000 rwxp 000ec000 03:01 2195465    /home/jesse/bin/materialsystem_i486.so
b7c77000-b7c8e000 rwxp b7c77000 00:00 0 
b7c8e000-b7cc6000 r-xp 00000000 03:01 2195469    /home/jesse/bin/soundemittersystem_i486.so
b7cc6000-b7cca000 rwxp 00038000 03:01 2195469    /home/jesse/bin/soundemittersystem_i486.so
b7cca000-b7ccc000 rwxp b7cca000 00:00 0 
b7ccc000-b7d66000 r-xp 00000000 03:01 2195460    /home/jesse/bin/dedicated_i686.so
b7d66000-b7d70000 rwxp 00099000 03:01 2195460    /home/jesse/bin/dedicated_i686.so
b7d70000-b7d7e000 rwxp b7d70000 00:00 0 
b7d7e000-b7d90000 r-xp 00000000 03:01 2195477    /home/jesse/bin/vstdlib_i486.so
b7d90000-b7d92000 rwxp 00011000 03:01 2195477    /home/jesse/bin/vstdlib_i486.so
b7d92000-b7da6000 r-xp 00000000 03:01 3081177    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7da6000-b7da8000 rwxp 00013000 03:01 3081177    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7da8000-b7daa000 rwxp b7da8000 00:00 0 
b7daa000-b7dd6000 r-xp 00000000 03:01 2195473    /home/jesse/bin/tier0_i486.so
b7dd6000-b7dd9000 rwxp 0002b000 03:01 2195473    /home/jesse/bin/tier0_i486.so
b7dd9000-b7de1000 rwxp b7dd9000 00:00 0 
b7de1000-b7f25000 r-xp 00000000 03:01 3081163    /lib/tls/i686/cmov/libc-2.6.1.so
b7f25000-b7f26000 r-xp 00143000 03:01 3081163    /lib/tls/i686/cmov/libc-2.6.1.so
b7f26000-b7f28000 rwxp 00144000 03:01 3081163    /lib/tls/i686/cmov/libc-2.6.1.so
b7f28000-b7f2c000 rwxp b7f28000 00:00 0 
b7f2c000-b7f2e000 r-xp 00000000 03:01 3081166    /lib/tls/i686/cmov/libdl-2.6.1.so
b7f2e000-b7f30000 rwxp 00001000 03:01 3081166    /lib/tls/i686/cmov/libdl-2.6.1.so
b7f30000-b7f53000 r-xp 00000000 03:01 3081167    /lib/tls/i686/cmov/libm-2.6.1.so
b7f53000-b7f55000 rwxp 00023000 03:01 3081167    /lib/tls/i686/cmov/libm-2.6.1.so
b7f57000-b7f5e000 r-xp 00000000 03:01 2195466    /home/jesse/bin/scenefilecache_i486.so
b7f5e000-b7f5f000 rwxp 00007000 03:01 2195466    /home/jesse/bin/scenefilecache_i486.so
b7f5f000-b7f62000 rwxp b7f5f000 00:00 0 
b7f62000-b7f7c000 r-xp 00000000 03:01 3047492    /lib/ld-2.6.1.so
b7f7c000-b7f7e000 rwxp 00019000 03:01 3047492    /lib/ld-2.6.1.so
bfe8f000-bfea4000 rwxp bfe8f000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
jesse@jesse-desktop:~$ 

i use Ubuntu 7.10, on a P4 2.8GHz Northwood, 512MB DDR

Hopefully i get this thing up, i need to use this spare computer for something! :)

EDIT: Accidently made 2 threads on this same subject, i want to delete this one...

---

