---
title: "Banshee crashes when importing Music Library"
date: 2007-06-02
forum: General Help
---

### Post by alanorozco on 2007-06-02
I open Banshee, I select which folder to import music with, it starts scanning and it crashes.

Here's my console log:
```
alan@orozco:~$ banshee
Debug: [02/06/2007 09:24:08 a.m.] (Loading audio profiles) - /usr/share/banshee/audio-profiles
Debug: [02/06/2007 09:24:11 a.m.] (Motor de reproducción predeterminado) - GStreamer 0.10
Debug: [02/06/2007 09:24:11 a.m.] (Inicializado el core de CD de audio) - 
Debug: [02/06/2007 09:24:11 a.m.] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_uuid_49FE698CC18C6044
Debug: [02/06/2007 09:24:11 a.m.] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_uuid_49FE698CC18C6044
Debug: [02/06/2007 09:24:11 a.m.] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_uuid_127F9A621D1FCC71
Debug: [02/06/2007 09:24:11 a.m.] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_uuid_127F9A621D1FCC71
Debug: [02/06/2007 09:24:11 a.m.] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_uuid_8626_71DE
Debug: [02/06/2007 09:24:11 a.m.] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_uuid_8626_71DE
Debug: [02/06/2007 09:24:11 a.m.] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_uuid_2A648B39648B0733
Debug: [02/06/2007 09:24:12 a.m.] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_uuid_2A648B39648B0733
Setting IO Backend to Banshee.IO.Unix.IOConfig (unix)
*** stack smashing detected ***: banshee terminated
Stacktrace:

  at (wrapper managed-to-native) Mono.Unix.Native.Syscall.sys_readdir_r (intptr,Mono.Unix.Native.Syscall/_Dirent&,intptr&) <0x00004>
  at (wrapper managed-to-native) Mono.Unix.Native.Syscall.sys_readdir_r (intptr,Mono.Unix.Native.Syscall/_Dirent&,intptr&) <0xffffffff>
  at Mono.Unix.Native.Syscall.readdir_r (intptr,Mono.Unix.Native.Dirent,intptr&) <0x0005c>
  at Mono.Unix.UnixDirectoryInfo.GetEntries (intptr) <0x0007a>
  at Mono.Unix.UnixDirectoryInfo.GetEntries () <0x0004b>
  at Mono.Unix.UnixDirectoryInfo.GetFileSystemEntries () <0x0000d>
  at <>c__CompilerGenerated31.MoveNext () <0x0005f>
  at Banshee.Base.ImportManager.ScanForFiles (string) <0x00236>
  at Banshee.Base.ImportManager.ScanForFiles (string) <0x003a4>
  at Banshee.Base.ImportManager.ScanForFiles (string) <0x003a4>
  at <>c__CompilerGenerated60.<>c__AnonymousMethod181 () <0x0005e>
  at (wrapper delegate-invoke) System.MulticastDelegate.invoke_void () <0xffffffff>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

        banshee [0x818f7de]
        banshee [0x8171c4b]
        [0xffffe440]
        /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7d2e641]
        /lib/tls/i686/cmov/libc.so.6 [0xb7d629bb]
        /lib/tls/i686/cmov/libc.so.6(__stack_chk_fail+0x41) [0xb7de80e1]
        /usr/lib/libMonoPosixHelper.so [0xb6152be4]
        /usr/lib/libMonoPosixHelper.so(Mono_Posix_Syscall_readdir_r+0xa4) [0xb614dc11]
        [0xb2c436dc]
        [0xb2c4365d]
        [0xb2c434fb]
        [0xb2c432f4]
        [0xb2c4326e]
        [0xb2c42aa8]
        [0xb2c3fef7]
        [0xb2c40065]
        [0xb2c40065]
        [0xb2c3f6af]
        [0xb5059d78]
        [0xb73c2879]
        banshee [0x8171aaf]
        banshee(mono_runtime_invoke+0x27) [0x80b038f]
        banshee(mono_runtime_delegate_invoke+0x62) [0x80b0617]
        banshee [0x80e4f6e]
        banshee [0x812c50d]
        banshee [0x8145972]
        /lib/tls/i686/cmov/libpthread.so.0 [0xb7e7031b]
        /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7dd257e]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1211099424 (LWP 7259)]
[New Thread -1289983088 (LWP 7288)]
[New Thread -1294431344 (LWP 7278)]
[New Thread -1293378672 (LWP 7277)]
[New Thread -1291465840 (LWP 7276)]
[New Thread -1276277872 (LWP 7272)]
[New Thread -1277330544 (LWP 7267)]
[New Thread -1257960560 (LWP 7263)]
[New Thread -1220834416 (LWP 7261)]
[New Thread -1215079536 (LWP 7260)]
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
  10 Thread -1215079536 (LWP 7260)  0xffffe410 in __kernel_vsyscall ()
  9 Thread -1220834416 (LWP 7261)  0xffffe410 in __kernel_vsyscall ()
  8 Thread -1257960560 (LWP 7263)  0xffffe410 in __kernel_vsyscall ()
  7 Thread -1277330544 (LWP 7267)  0xffffe410 in __kernel_vsyscall ()
  6 Thread -1276277872 (LWP 7272)  0xffffe410 in __kernel_vsyscall ()
  5 Thread -1291465840 (LWP 7276)  0xffffe410 in __kernel_vsyscall ()
  4 Thread -1293378672 (LWP 7277)  0xffffe410 in __kernel_vsyscall ()
  3 Thread -1294431344 (LWP 7278)  0xffffe410 in __kernel_vsyscall ()
  2 Thread -1289983088 (LWP 7288)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1211099424 (LWP 7259)  0xffffe410 in __kernel_vsyscall ()

Thread 10 (Thread -1215079536 (LWP 7260)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e77986 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811700b in ?? ()
#3  0xb793539c in ?? ()
#4  0x00000000 in ?? ()

Thread 9 (Thread -1220834416 (LWP 7261)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e745c6 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811c14a in ?? ()
#3  0xb78a21dc in ?? ()
#4  0xb78a21c4 in ?? ()
#5  0xb73b8178 in ?? ()
#6  0x00000000 in ?? ()

Thread 8 (Thread -1257960560 (LWP 7263)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e7484c in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811c1c7 in ?? ()
#3  0xb78a31e4 in ?? ()
#4  0xb78a31cc in ?? ()
#5  0xb505005c in ?? ()
#6  0x00000000 in ?? ()

Thread 7 (Thread -1277330544 (LWP 7267)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7dc8893 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7eb6e03 in ?? () from /usr/lib/libglib-2.0.so.0
#3  0x08a1a2b0 in ?? ()
#4  0x00000005 in ?? ()
#5  0xffffffff in ?? ()
#6  0x08a1a2b0 in ?? ()
#7  0x00000005 in ?? ()
#8  0xb7f1a748 in ?? () from /usr/lib/libglib-2.0.so.0
#9  0x08a52fd0 in ?? ()
#10 0xb3dd7324 in ?? ()
#11 0x00000001 in ?? ()
#12 0x00000001 in ?? ()
#13 0x08a52fd0 in ?? ()
#14 0x08a1a2b0 in ?? ()
#15 0xb7dc8820 in ?? () from /lib/tls/i686/cmov/libc.so.6
#16 0xb7e73be0 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#17 0xb7e72440 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7ed1613 in g_thread_self () from /usr/lib/libglib-2.0.so.0
#19 0xb7eb7179 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#20 0xb6dea4a0 in ?? () from /usr/lib/libORBit-2.so.0
#21 0x08a71760 in ?? ()
#22 0xb7f1a748 in ?? () from /usr/lib/libglib-2.0.so.0
#23 0xb3dd73a8 in ?? ()
#24 0xb7ed1b7f in ?? () from /usr/lib/libglib-2.0.so.0
#25 0x00000000 in ?? ()

Thread 6 (Thread -1276277872 (LWP 7272)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e7484c in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811c1c7 in ?? ()
#3  0xb78a3178 in ?? ()
#4  0xb78a3160 in ?? ()
#5  0xb3ed804c in ?? ()
#6  0x00000000 in ?? ()

Thread 5 (Thread -1291465840 (LWP 7276)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e7484c in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811c1c7 in ?? ()
#3  0xb78a202c in ?? ()
#4  0xb78a2014 in ?? ()
#5  0xb305c198 in ?? ()
#6  0x081196a9 in ?? ()
#7  0x0811b001 in ?? ()
#8  0x00000004 in ?? ()
#9  0x46618ba9 in ?? ()
#10 0x2245cdc0 in ?? ()
#11 0x00000400 in ?? ()
#12 0x08229a48 in ?? ()
#13 0xb305c1d8 in ?? ()
#14 0x0811c457 in ?? ()
#15 0xb78a202c in ?? ()
#16 0xb78a2014 in ?? ()
#17 0xb305c248 in ?? ()
#18 0x00000001 in ?? ()
#19 0x00000000 in ?? ()

Thread 4 (Thread -1293378672 (LWP 7277)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7dd2be6 in epoll_wait () from /lib/tls/i686/cmov/libc.so.6
#2  0x080e663b in ?? ()
#3  0x00000041 in ?? ()
#4  0x0948b808 in ?? ()
#5  0x00000200 in ?? ()
#6  0xffffffff in ?? ()
#7  0xb7e737fc in __pthread_mutex_unlock_usercnt ()
   from /lib/tls/i686/cmov/libpthread.so.0
#8  0x080e4f16 in ?? ()
#9  0x0822af40 in ?? ()
#10 0xb2e892e8 in ?? ()
#11 0x080e65b2 in ?? ()
#12 0x00000001 in ?? ()
#13 0x00000000 in ?? ()

Thread 3 (Thread -1294431344 (LWP 7278)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e7484c in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811c1c7 in ?? ()
#3  0xb78a346c in ?? ()
#4  0xb78a3454 in ?? ()
#5  0xb2d88178 in ?? ()
#6  0x081196a9 in ?? ()
#7  0x0811b001 in ?? ()
#8  0x00000004 in ?? ()
#9  0x46618ba9 in ?? ()
#10 0x2245cdc0 in ?? ()
#11 0x00000430 in ?? ()
#12 0x08229a48 in ?? ()
#13 0xb2d881b8 in ?? ()
#14 0x0811c457 in ?? ()
#15 0xb78a346c in ?? ()
#16 0xb78a3454 in ?? ()
#17 0xb2d88228 in ?? ()
#18 0x00000001 in ?? ()
#19 0x00000000 in ?? ()

Thread 2 (Thread -1289983088 (LWP 7288)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7dcb3d1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7edf4a0 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7edf86c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0818f8bc in ?? ()
#5  0xb31c4db4 in ?? ()
#6  0xb31c4d9c in ?? ()
#7  0xb31c4d98 in ?? ()
#8  0xb31c4d94 in ?? ()
#9  0x00000000 in ?? ()

Thread 1 (Thread -1211099424 (LWP 7259)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e7484c in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f37133 in ?? () from /usr/lib/libgthread-2.0.so.0
#3  0x085a9920 in ?? ()
#4  0x085a9900 in ?? ()
#5  0xbf9388ac in ?? ()
#6  0xb7eb41e1 in g_get_current_time () from /usr/lib/libglib-2.0.so.0
#7  0xb6dcd512 in giop_recv_buffer_get () from /usr/lib/libORBit-2.so.0
#8  0xb6dd1fab in ORBit_small_invoke_stub () from /usr/lib/libORBit-2.so.0
#9  0xb6dd21ce in ORBit_small_invoke_stub_n () from /usr/lib/libORBit-2.so.0
#10 0xb6dde992 in ORBit_c_stub_invoke () from /usr/lib/libORBit-2.so.0
#11 0xb6e2a21a in ConfigDatabase_set () from /usr/lib/libgconf-2.so.4
#12 0xb6e20557 in gconf_engine_set () from /usr/lib/libgconf-2.so.4
#13 0xb6e23ba9 in gconf_client_set () from /usr/lib/libgconf-2.so.4
#14 0xb5059683 in ?? ()
#15 0x085b6e40 in ?? ()
#16 0x095712b8 in ?? ()
#17 0x09196bd0 in ?? ()
#18 0xbf938b28 in ?? ()
#19 0x003bdca9 in ?? ()
#20 0x095712b8 in ?? ()
#21 0xbf939398 in ?? ()
#22 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Cancelled (core dumped)

```

---

### Post by angryhomer17 on 2007-06-10
Not sure how to fix the crashing, but you might just want to reinstall Banshee (*I have no idea what's wrong*)
Otherwise I'd suggest ditching Banshee and using Rhythmbox. My library loads much faster, rhythmbox is pretty stable and provides a nice simple interface while still being more useful than xmms or bmp.

---

### Post by mattismyname on 2007-12-23
Hey!  I have the same problem.  Somehow the stack smashing protection is kicking in when you try to import a directory with more than X contents.  I don't know what X is.]

Anybody have a soution?  I've tried compiling banshee from latest source but no luck.

---

### Post by tgalati4 on 2007-12-23
What version of Ubuntu are you running Banshee under?

Try running in debug mode:

>banshee --debug

Try importing a small music library first, then adding to it later, perhaps directory-by-directory.

Make sure you have the latest mono updates, there have been quite a few lately.

I've never seen it crash in the few months that I have been running it under SLED10 and Linux Mint 4, but my library is only a few thousand songs.

---

### Post by mattismyname on 2007-12-25
Confirmed in Hardy Alpha 2.  Also tried compiling Banshee from latest source -- no luck.

It somehow depends on the size or contents of the library being imported.  If I do one directory, no problem.  But if I do all 1800 dirs & 15400 files it happens.

---

