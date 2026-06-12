---
title: "xfce4-terminal memory leak in xubuntu 14.04"
date: 2014-09-16
forum: General Help
---

### Post by WaltL on 2014-09-16
I'm running xubuntu on a 2005 MacPro 8 core, 32G RAM machine.  If I leave the terminal open for 3-4 days, almost all of my RAM will be used by terminal to the point that the OS will freeze if I don't reset.  Closing terminals resets it.  Not that big of a deal, but I would like to know why xfce4-terminal leaks like this and if anyone else has seen this.  I never had this issue with earlier ubuntu installs (first time using xubuntu).

Here's a top after ~ 24 hr with 2 terminals open (nothing else was running overnight):

 PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                                                                                                
18551 waltl   20   0  566516 188160  97836 S  17.3  0.6   2:25.16 chrome                                                                                                                                                                                                 
 1255 root      20   0  266804 103424  33660 S  11.0  0.3   2025:24 Xorg                                                                                                                                                                                                   
16740 waltl   20   0 4791460 3.830g  12740 S   6.3 12.2  57:52.77 xfce4-terminal                                                                                                                                                                                         
18740 waltl   20   0  805920 127072  46648 S   4.3  0.4   0:39.14 chrome                                                                                                                                                                                                 
18513 waltl   20   0  886088 143292  71996 S   1.3  0.4   0:25.88 chrome

---

### Post by matt_symes on 2014-09-16
Hi

I'm not seeing any memory leak at all.

```

matthew-laptop:/home/matthew:1 % ps aux | grep xfce4-terminal | grep -v grep && uptime
matthew   3142  0.0  0.3 620552 11756 ?        Sl   Sep15   1:10 /usr/bin/xfce4-terminal
 18:26:26 up 1 day,  1:57, 24 users,  load average: 1.85, 1.64, 1.92
matthew-laptop:/home/matthew:1 % 
```

In this case my uptime is only just after a day but i always have at least one terminal open and you can normally measure my uptime in weeks.

```

matthew-laptop:/home/matthew:1 % grep -i release /etc/lsb-release
DISTRIB_RELEASE=14.04
matthew-laptop:/home/matthew:1 %
```

Stock terminal.

```

matthew-laptop:/home/matthew:1 % xfce4-terminal --version
xfce4-terminal 0.6.3 (Xfce 4.10)

Copyright (c) 2003-2012
        The Xfce development team. All rights reserved.

Written by Benedikt Meurer <benny@xfce.org>
and Nick Schermer <nick@xfce.org>.

Please report bugs to <http://bugzilla.xfce.org/>.
matthew-laptop:/home/matthew:1 % 
```

Post back your memory usage again tomorrow.

Kind regards

---

### Post by matt_symes on 2014-09-16
Hi

Just a thought but have you used valgrind to try to track down the memory leak ?

Kind regards

---

### Post by WaltL on 2014-09-16
Matt,
I have not tried valgrind.  Note that in the top I submitted previously, terminal is using 12.2% of RAM

Here's the sys usage from that previous top:

top - 13:09:29 up 7 days, 22:26,  3 users,  load average: 0.56, 0.54, 0.42
Tasks: 234 total,   1 running, 233 sleeping,   0 stopped,   0 zombie
%Cpu(s):  4.4 us,  0.3 sy,  0.4 ni, 94.6 id,  0.2 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  **32943808 total,  6270764 used**, 26673044 free,   174460 buffers
KiB Swap:        0 total,        0 used,        0 free.   882976 cached Mem


Now, here's top (terminal now at 12.6% mem) and usage a mere 45 min. later:

1255 root      20   0  266804 103424  33660 R  10.0  0.3   2033:06 Xorg                                                                                                                                                                                                   
16740 waltl   20   0 4929644 3.962g  12740 S   6.6 **12.6**  61:07.09 xfce4-terminal                                                                                                                                                                                         
 2261 waltl   20   0  587976  17476   9272 S   0.3  0.1  22:02.79 xfwm4                                                                                                                                                                                                  
18642 waltl   20   0  807308 129112  29924 S   0.3  0.4   0:25.42 chrome                                                                                                                                                                                                 




Tasks: 235 total,   2 running, 233 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.0 us,  0.1 sy,  0.0 ni, 97.8 id,  0.1 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  **32943808 total,  6443224 used**, 26500584 free,   176188 buffers
KiB Swap:        0 total,        0 used,        0 free.   883720 cached Mem

Total went from 6.27G to 6.44G, and it's just sitting idle.


Now, I'll reset/close terminal, open, and top again:

1255 root      20   0  265396 102560  32796 S   8.6  0.3   2033:45 Xorg                                                                                              
18991 waltl   20   0  792524  16632  11404 S   4.7  **0.1**   0:00.51 xfce4-terminal                                                                                    
18551 waltl   20   0  582684 200880  97924 S   2.0  0.6   4:35.88 chrome                                                                                            

Voila!  Terminal memory goes from > 12% to  0.1%  and

Tasks: 233 total,   2 running, 231 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.8 us,  0.5 sy,  0.1 ni, 97.4 id,  0.2 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  **32943808 total,  2289884 used**, 30653924 free,   176472 buffers

Total drops from 6.4G to 2.2G.

This is consistent and always related to xfce-terminal.  If I let it go long enough w/o closing terminal it will literally suck up every bit of RAM available to it.

I'd be happy to diagnose/troubleshoot if you can give me some guidance.

Walt

---

### Post by Toz on 2014-09-16
Are you using a background image for your terminal window? If so, you may be suffering from [this bug]("https://bugzilla.xfce.org/show_bug.cgi?id=7871"). Or maybe some version of [this bug]("https://bugzilla.xfce.org/show_bug.cgi?id=8890").

What does the following return?
```
cat ~/.config/xfce4/terminal/terminalrc | grep BackgroundMode
```

---

### Post by matt_symes on 2014-09-17
Hi

That may be a really nice catch ToZ. I was not aware of that bug.

Kind regards

---

### Post by WaltL on 2014-09-17
Toz, I am running the default background, as far as I know... it's a gradient of blue (bottom) to greenish (top).

Running the cmd. [COLOR=#000000][FONT=Ubuntu Mono]cat ~/.config/xfce4/terminal/terminalrc | grep BackgroundMode[/FONT][/COLOR]

BackgroundMode=TERMINAL_BACKGROUND_IMAGE

As an aside, there is one thing about this install that is a bit quirky.  I originally installed Ubuntu (ultimately on 3 different drives) and unlike all previous version installs, with every install I had all kinds of problems with the OS locking up as described here [http://ubuntuforums.org/showthread.php?t=2238374&p=13092704#post13092704](http://ubuntuforums.org/showthread.php?t=2238374&p=13092704#post13092704).  This is unrelated to the mem issue I'm seeing now.  Anyway, I thought the locking up problem might have something to do with the desktop environment, so I "changed" from Ubuntu to Xubuntu per this example (including the cleanup after I was sure I was happy with the install) [https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative)  
This solved all the lock up issues I was seeing with Ubuntu (I was rebooting 2-3X day with the original Ubuntu 14.04 install) and, other than the mem issue I have now, Xubuntu is as stable as a rock.

So here is the mem usage since I reset the terminal yesterday afternoon:

top - 10:40:26 up 8 days, 19:57,  5 users,  load average: 0.16, 0.30, 0.37
Tasks: 248 total,   2 running, 246 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.3 us,  0.0 sy,  0.0 ni, 96.6 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  32943808 total, **17783380 used**, 15160428 free,   241628 buffers


1255 root      20   0  275160 109852  40088 S  17.3  0.3   2184:26 Xorg                                                                                                                                                                                       
18991 waltl   20   0 5377500 4.389g  12996 S   8.6 **14.0**  68:06.16 xfce4-terminal                                                                                                                                                                             


And here is some diagnosis data per Matt's suggestion, i.e. Valgrind output... not sure how to diagnose from this, but it does appear to be detecting a leak; although, no error summary is shown.  Running with --leak-check=full is quite an extensive output:

waltl@waltl-MacPro:~$ valgrind -v --tool=memcheck xfce4-terminal
==3829== Memcheck, a memory error detector
==3829== Copyright (C) 2002-2013, and GNU GPL'd, by Julian Seward et al.
==3829== Using Valgrind-3.10.0 and LibVEX; rerun with -h for copyright info
==3829== Command: xfce4-terminal
==3829== 
--3829-- Valgrind options:
--3829--    -v
--3829--    --tool=memcheck
--3829-- Contents of /proc/version:
--3829--   Linux version 3.13.0-35-generic (buildd@panlong) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014
--3829-- Arch and hwcaps: AMD64, LittleEndian, amd64-cx16-sse3
--3829-- Page sizes: currently 4096, max supported 4096
--3829-- Valgrind library directory: /usr/local/lib/valgrind
--3829-- Reading syms from /usr/bin/xfce4-terminal
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /lib/x86_64-linux-gnu/ld-2.19.so
--3829--   Considering /lib/x86_64-linux-gnu/ld-2.19.so ..
--3829--   .. CRC mismatch (computed 4cbae35e wanted 8d683c31)
--3829--   Considering /usr/lib/debug/lib/x86_64-linux-gnu/ld-2.19.so ..
--3829--   .. CRC is valid
--3829-- Reading syms from /usr/local/lib/valgrind/memcheck-amd64-linux
--3829--    object doesn't have a dynamic symbol table
--3829-- Scheduler: using generic scheduler lock implementation.
--3829-- Reading suppressions file: /usr/local/lib/valgrind/default.supp
==3829== embedded gdbserver: reading from /tmp/vgdb-pipe-from-vgdb-to-3829-by-wlorenz-on-???
==3829== embedded gdbserver: writing to   /tmp/vgdb-pipe-to-vgdb-from-3829-by-wlorenz-on-???
==3829== embedded gdbserver: shared mem   /tmp/vgdb-pipe-shared-mem-vgdb-3829-by-wlorenz-on-???
==3829== 
==3829== TO CONTROL THIS PROCESS USING vgdb (which you probably
==3829== don't want to do, unless you know exactly what you're doing,
==3829== or are doing some strange experiment):
==3829==   /usr/local/lib/valgrind/../../bin/vgdb --pid=3829 ...command...
==3829== 
==3829== TO DEBUG THIS PROCESS USING GDB: start GDB like this
==3829==   /path/to/gdb xfce4-terminal
==3829== and then give GDB the following command
==3829==   target remote | /usr/local/lib/valgrind/../../bin/vgdb --pid=3829
==3829== --pid is optional if only one valgrind process is running
==3829== 
--3829-- REDIR: 0x4019ca0 (ld-linux-x86-64.so.2:strlen) redirected to 0x3806bd01 (vgPlain_amd64_linux_REDIR_FOR_strlen)
--3829-- Reading syms from /usr/local/lib/valgrind/vgpreload_core-amd64-linux.so
--3829-- Reading syms from /usr/local/lib/valgrind/vgpreload_memcheck-amd64-linux.so
==3829== WARNING: new redirection conflicts with existing -- ignoring it
--3829--     old: 0x04019ca0 (strlen              ) R-> (0000.0) 0x3806bd01 vgPlain_amd64_linux_REDIR_FOR_strlen
--3829--     new: 0x04019ca0 (strlen              ) R-> (2007.0) 0x04c2dc20 strlen
--3829-- REDIR: 0x4019a50 (ld-linux-x86-64.so.2:index) redirected to 0x4c2d7d0 (index)
--3829-- REDIR: 0x4019c70 (ld-linux-x86-64.so.2:strcmp) redirected to 0x4c2ed70 (strcmp)
--3829-- REDIR: 0x401a9c0 (ld-linux-x86-64.so.2:mempcpy) redirected to 0x4c31820 (mempcpy)
--3829-- Reading syms from /usr/lib/libvte.so.9.2800.2
--3829--   Considering /usr/lib/libvte.so.9.2800.2 ..
--3829--   .. CRC mismatch (computed 73f5b2e5 wanted f98ee7c1)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0 ..
--3829--   .. CRC mismatch (computed c168660b wanted 161bd255)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libxfce4ui-1.so.0.0.0
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0.2400.23
--3829--   Considering /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0.2400.23 ..
--3829--   .. CRC mismatch (computed 8c0d12da wanted 1fba93ef)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libxfce4util.so.6.0.0
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0.2400.23
--3829--   Considering /usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0.2400.23 ..
--3829--   .. CRC mismatch (computed 14cd00c8 wanted 18d7b54e)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libatk-1.0.so.0.21009.1
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.4000.0
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0.3000.7
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0.3600.3
--3829--   Considering /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0.3600.3 ..
--3829--   .. CRC mismatch (computed 75ba8bff wanted 46def4ba)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4000.0
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /lib/x86_64-linux-gnu/libglib-2.0.so.0.4000.0
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /lib/x86_64-linux-gnu/libpthread-2.19.so
--3829--   Considering /lib/x86_64-linux-gnu/libpthread-2.19.so ..
--3829--   .. CRC mismatch (computed d7f7b713 wanted 28afece6)
--3829--   Considering /usr/lib/debug/lib/x86_64-linux-gnu/libpthread-2.19.so ..
--3829--   .. CRC is valid
--3829-- Reading syms from /lib/x86_64-linux-gnu/libc-2.19.so
--3829--   Considering /lib/x86_64-linux-gnu/libc-2.19.so ..
--3829--   .. CRC mismatch (computed e7228afa wanted 93ff6981)
--3829--   Considering /usr/lib/debug/lib/x86_64-linux-gnu/libc-2.19.so ..
--3829--   .. CRC is valid
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0.3600.3
--3829--   Considering /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0.3600.3 ..
--3829--   .. CRC mismatch (computed 5d962888 wanted 38e86a7c)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libcairo.so.2.11301.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libcairo.so.2.11301.0 ..
--3829--   .. CRC mismatch (computed 839f59a9 wanted 3b96e381)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /lib/x86_64-linux-gnu/libtinfo.so.5.9
--3829--   Considering /lib/x86_64-linux-gnu/libtinfo.so.5.9 ..
--3829--   .. CRC mismatch (computed a766b3f6 wanted 5ffaddcc)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /lib/x86_64-linux-gnu/libm-2.19.so
--3829--   Considering /lib/x86_64-linux-gnu/libm-2.19.so ..
--3829--   .. CRC mismatch (computed 0ebccb69 wanted 44d41128)
--3829--   Considering /usr/lib/debug/lib/x86_64-linux-gnu/libm-2.19.so ..
--3829--   .. CRC is valid
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /lib/x86_64-linux-gnu/libdl-2.19.so
--3829--   Considering /lib/x86_64-linux-gnu/libdl-2.19.so ..
--3829--   .. CRC mismatch (computed c1315e8c wanted 37097b60)
--3829--   Considering /usr/lib/debug/lib/x86_64-linux-gnu/libdl-2.19.so ..
--3829--   .. CRC is valid
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libSM.so.6.0.1
--3829--   Considering /usr/lib/x86_64-linux-gnu/libSM.so.6.0.1 ..
--3829--   .. CRC mismatch (computed 61ae06da wanted 846458ce)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libICE.so.6.3.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libICE.so.6.3.0 ..
--3829--   .. CRC mismatch (computed af330d05 wanted 8506ebab)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libstartup-notification-1.so.0.0.0
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.4000.0
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0.3600.3
--3829--   Considering /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0.3600.3 ..
--3829--   .. CRC mismatch (computed 158534d4 wanted 9191af40)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libfontconfig.so.1.8.0
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0 ..
--3829--   .. CRC mismatch (computed 96d07840 wanted d3cfc2cf)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0 ..
--3829--   .. CRC mismatch (computed 7bb99cdf wanted 61ad4d32)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0 ..
--3829--   .. CRC mismatch (computed ea0c9213 wanted 8b39c27e)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0 ..
--3829--   .. CRC mismatch (computed 0be820e9 wanted c977080b)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
--3829--   Considering /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2 ..
--3829--   .. CRC mismatch (computed 63e27661 wanted 89d60ca9)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libXcomposite.so.1.0.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libXcomposite.so.1.0.0 ..
--3829--   .. CRC mismatch (computed 95e939a0 wanted a74069c4)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0 ..
--3829--   .. CRC mismatch (computed fe4e32c0 wanted 2a5b3a13)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0 ..
--3829--   .. CRC mismatch (computed 02fd320d wanted 0899221f)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /lib/x86_64-linux-gnu/libz.so.1.2.8
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /lib/x86_64-linux-gnu/libselinux.so.1
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /lib/x86_64-linux-gnu/libresolv-2.19.so
--3829--   Considering /lib/x86_64-linux-gnu/libresolv-2.19.so ..
--3829--   .. CRC mismatch (computed 5c733db8 wanted 30cd2eee)
--3829--   Considering /usr/lib/debug/lib/x86_64-linux-gnu/libresolv-2.19.so ..
--3829--   .. CRC is valid
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libthai.so.0.2.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libthai.so.0.2.0 ..
--3829--   .. CRC mismatch (computed ae138e5a wanted 3573c45a)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libffi.so.6.0.1
--3829--   Considering /usr/lib/x86_64-linux-gnu/libffi.so.6.0.1 ..
--3829--   .. CRC mismatch (computed cbfcaa4a wanted 2012f49a)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /lib/x86_64-linux-gnu/libpcre.so.3.13.1
--3829--   Considering /lib/x86_64-linux-gnu/libpcre.so.3.13.1 ..
--3829--   .. CRC mismatch (computed 3fb98dc8 wanted 29d03fa3)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libfreetype.so.6.11.1
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.30.2
--3829--   Considering /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.30.2 ..
--3829--   .. CRC mismatch (computed 0ca62200 wanted 0a138481)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /lib/x86_64-linux-gnu/libpng12.so.0.50.0
--3829--   Considering /lib/x86_64-linux-gnu/libpng12.so.0.50.0 ..
--3829--   .. CRC mismatch (computed bcf7bdd8 wanted dafabe67)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0.0.0
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libxcb-render.so.0.0.0
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /lib/x86_64-linux-gnu/librt-2.19.so
--3829--   Considering /lib/x86_64-linux-gnu/librt-2.19.so ..
--3829--   .. CRC mismatch (computed aa86d720 wanted d04e3800)
--3829--   Considering /usr/lib/debug/lib/x86_64-linux-gnu/librt-2.19.so ..
--3829--   .. CRC is valid
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0 ..
--3829--   .. CRC mismatch (computed 256f5df8 wanted 5d40ac88)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0 ..
--3829--   .. CRC mismatch (computed 15fc4130 wanted a06cb5c7)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /lib/x86_64-linux-gnu/libuuid.so.1.3.0
--3829--   Considering /lib/x86_64-linux-gnu/libuuid.so.1.3.0 ..
--3829--   .. CRC mismatch (computed ebc66fde wanted 8052c978)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libxcb-util.so.0.0.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libxcb-util.so.0.0.0 ..
--3829--   .. CRC mismatch (computed d6abf049 wanted 50280efe)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1.0.0
--3829--   Considering /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1.0.0 ..
--3829--   .. CRC mismatch (computed e2f4c069 wanted 2164c257)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libharfbuzz.so.0.927.0
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /lib/x86_64-linux-gnu/libexpat.so.1.6.0
--3829--   Considering /lib/x86_64-linux-gnu/libexpat.so.1.6.0 ..
--3829--   .. CRC mismatch (computed 8f384202 wanted da130668)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libdatrie.so.1.3.1
--3829--   Considering /usr/lib/x86_64-linux-gnu/libdatrie.so.1.3.1 ..
--3829--   .. CRC mismatch (computed 857b05e2 wanted 26b22fc0)
--3829--    object doesn't have a symbol table
--3829-- Reading syms from /usr/lib/x86_64-linux-gnu/libgraphite2.so.3.0.1
--3829--    object doesn't have a symbol table
--3829-- REDIR: 0x73237e0 (libc.so.6:strcasecmp) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x7325ad0 (libc.so.6:strncasecmp) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x7322fb0 (libc.so.6:memcpy@GLIBC_2.2.5) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x73281b0 (libc.so.6:memcpy@@GLIBC_2.14) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x731f960 (libc.so.6:strncmp) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x731ef80 (libc.so.6:strcpy) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x7339780 (libc.so.6:wcscpy) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x739f5a0 (libc.so.6:__memcpy_chk) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x731daf0 (libc.so.6:strcmp) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x7321200 (libc.so.6:strncpy) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x731d8a0 (libc.so.6:index) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x7322450 (libc.so.6:strstr) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x7321240 (libc.so.6:rindex) redirected to 0x4c2d4b0 (rindex)
--3829-- REDIR: 0x731f540 (libc.so.6:strlen) redirected to 0x4c2db60 (strlen)
--3829-- REDIR: 0x73191d0 (libc.so.6:malloc) redirected to 0x4c2ab36 (malloc)
--3829-- REDIR: 0x7321e90 (libc.so.6:__GI_strstr) redirected to 0x4c31ab0 (__strstr_sse2)
--3829-- REDIR: 0x7322690 (libc.so.6:memchr) redirected to 0x4c2ee10 (memchr)
--3829-- REDIR: 0x7328200 (libc.so.6:__GI_memcpy) redirected to 0x4c2f710 (__GI_memcpy)
--3829-- REDIR: 0x7337cb0 (libc.so.6:__strstr_sse2_unaligned) redirected to 0x4c31a20 (strstr)
--3829-- REDIR: 0x7319870 (libc.so.6:free) redirected to 0x4c2bc50 (free)
--3829-- REDIR: 0x7323040 (libc.so.6:memset) redirected to 0x4c30dd0 (memset)
--3829-- REDIR: 0xffffffffff600000 (???:???) redirected to 0x3806bce3 (vgPlain_amd64_linux_REDIR_FOR_vgettimeofday)
--3829-- REDIR: 0x7319ca0 (libc.so.6:calloc) redirected to 0x4c2c89e (calloc)
--3829-- REDIR: 0x732ea50 (libc.so.6:__memcpy_sse2_unaligned) redirected to 0x4c2f130 (memcpy@@GLIBC_2.14)
--3829-- REDIR: 0x732e7a0 (libc.so.6:__strcmp_sse2_unaligned) redirected to 0x4c2ec30 (strcmp)
--3829-- REDIR: 0x7319970 (libc.so.6:realloc) redirected to 0x4c2ca40 (realloc)
--3829-- REDIR: 0x73e6bd0 (libc.so.6:__memmove_ssse3_back) redirected to 0x4c2eed0 (memcpy@GLIBC_2.2.5)
--3829-- REDIR: 0x731d8d0 (libc.so.6:__GI_strchr) redirected to 0x4c2d610 (__GI_strchr)
--3829-- REDIR: 0x731d6a0 (libc.so.6:strcat) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x7336430 (libc.so.6:__strcat_sse2_unaligned) redirected to 0x4c2d810 (strcat)
--3829-- REDIR: 0x731db30 (libc.so.6:__GI_strcmp) redirected to 0x4c2ec80 (__GI_strcmp)
--3829-- REDIR: 0x731f9b0 (libc.so.6:__GI_strncmp) redirected to 0x4c2e3b0 (__GI_strncmp)
--3829-- REDIR: 0x732a540 (libc.so.6:strchrnul) redirected to 0x4c31430 (strchrnul)
--3829-- REDIR: 0x7323670 (libc.so.6:__GI_stpcpy) redirected to 0x4c30820 (__GI_stpcpy)
--3829-- REDIR: 0x731f700 (libc.so.6:strnlen) redirected to 0x4c2db00 (strnlen)
--3829-- REDIR: 0x731efc0 (libc.so.6:__GI_strcpy) redirected to 0x4c2dd20 (__GI_strcpy)
--3829-- REDIR: 0x7323850 (libc.so.6:__GI___strcasecmp_l) redirected to 0x4c2e8a0 (__GI___strcasecmp_l)
--3829-- REDIR: 0x732a330 (libc.so.6:rawmemchr) redirected to 0x4c31470 (rawmemchr)
--3829-- REDIR: 0x73d7fa0 (libc.so.6:__strncmp_ssse3) redirected to 0x4c2e340 (strncmp)
--3829-- REDIR: 0x73229e0 (libc.so.6:bcmp) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x73f6ba0 (libc.so.6:__memcmp_sse4_1) redirected to 0x4c30680 (__memcmp_sse4_1)
--3829-- REDIR: 0x7333c40 (libc.so.6:__strncpy_sse2_unaligned) redirected to 0x4c2e1f0 (__strncpy_sse2_unaligned)
--3829-- REDIR: 0x73218c0 (libc.so.6:strspn) redirected to 0x4a25713 (_vgnU_ifunc_wrapper)
--3829-- REDIR: 0x73d3c00 (libc.so.6:__strspn_sse42) redirected to 0x4c31ca0 (strspn)
==3829== 
==3829== HEAP SUMMARY:
==3829==     in use at exit: 109,807 bytes in 1,053 blocks
==3829==   total heap usage: 2,445 allocs, 1,392 frees, 180,648 bytes allocated
==3829== 
==3829== Searching for pointers to 991 not-freed blocks
==3829== Checked 9,001,456 bytes
==3829== 
==3829== LEAK SUMMARY:
==3829==    definitely lost: 48 bytes in 1 blocks
==3829==    indirectly lost: 80 bytes in 4 blocks
==3829==      possibly lost: 7,164 bytes in 134 blocks
==3829==    still reachable: 93,803 bytes in 852 blocks
==3829==         suppressed: 0 bytes in 0 blocks
==3829== Rerun with --leak-check=full to see details of leaked memory
==3829== 
==3829== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)
==3829== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)

---

### Post by WaltL on 2014-09-17
Just noticed your link to the bug post. In desktop settings I changed background to "none," and now it's basically black, but I still get
cat ~/.config/xfce4/terminal/terminalrc | grep BackgroundMode
BackgroundMode=TERMINAL_BACKGROUND_IMAGE

So I'll reset the terminal and see what happens as the day goes on...

---

### Post by matt_symes on 2014-09-17
Hi

How long did you leave valgrind running ?

If i start it and then close the terminal terminal right after i get this as memory leakage.
```

==11713== LEAK SUMMARY:
==11713==    definitely lost: 48 bytes in 1 blocks
==11713==    indirectly lost: 115 bytes in 4 blocks
==11713==      possibly lost: 7,012 bytes in 131 blocks
==11713==    still reachable: 93,334 bytes in 840 blocks
==11713==         suppressed: 0 bytes in 0 blocks
```

Similar to yours and this may be memory not released at terminal shutdown. It would be cleaned up by the kernel after the terminal is closed anyway.

Run this command overnight and see what valgrind makes of it as your output seems to show no more leakage than mine.

```
valgrind --show-reachable=yes --trace-children=yes --log-file="$HOME"/terminal.log  xfce4-terminal
```

Incidently i have the transparent background with the opacity set at .98.

xfce4-terminal-> Edit Menu-> Preferences-> Background Dropdown->Transparent Background.

If you switch to this, do you still get the memory leak ?

Kind regards

---

