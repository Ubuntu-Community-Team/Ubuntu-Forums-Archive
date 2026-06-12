---
title: "ifolder client on gutsy"
date: 2007-10-24
forum: General Help
---

### Post by _DjScrew_ on 2007-10-24
well, I got the server going in gutsy, now I'm having some problems with the client. I followed this guide [http://ubuntuforums.org/showthread.php?t=470907](http://ubuntuforums.org/showthread.php?t=470907) (i know it's not meant for gutsy, but figured it would be the same for the most part) anyways, when trying to execute ifolder i get:

```

        mono [0x8194ca6]
        mono [0x81770ed]
        [0xffffe440]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        mono [0x810f9a7]
        mono [0x811a390]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        mono [0x810f9a7]
        mono [0x811a390]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_type_load+0x62) [0x80f0cfa]
        mono [0x811a36e]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono [0x8176f1a]
        mono(mono_runtime_invoke+0x27) [0x80b0b2f]
        mono(mono_runtime_exec_main+0x142) [0x80b5383]
        mono(mono_runtime_run_main+0x27e) [0x80b5631]
        mono(mono_jit_exec+0xbd) [0x805a4cb]
        mono [0x805a5a8]
        mono(mono_main+0x1683) [0x805bdc9]
        mono [0x8059636]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d5f050]
        mono [0x80595b1]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1210812720 (LWP 4696)]
[New Thread -1220031600 (LWP 4698)]
[New Thread -1214268528 (LWP 4697)]
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
  3 Thread -1214268528 (LWP 4697)  0xffffe410 in __kernel_vsyscall ()
  2 Thread -1220031600 (LWP 4698)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1210812720 (LWP 4696)  0xffffe410 in __kernel_vsyscall ()

Thread 3 (Thread -1214268528 (LWP 4697)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ec49f6 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811bc9f in ?? ()
#3  0xb79fb3ac in ?? ()
#4  0x00000000 in ?? ()

Thread 2 (Thread -1220031600 (LWP 4698)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ec1676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120dde in ?? ()
#3  0xb79661dc in ?? ()
#4  0xb79661c4 in ?? ()
#5  0xb7ebf541 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6  0x081210eb in ?? ()
#7  0xb79661dc in ?? ()
#8  0xb79661c4 in ?? ()
#9  0x00000000 in ?? ()

Thread 1 (Thread -1210812720 (LWP 4696)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e15301 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f34780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f34b4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xb7c04844 in ?? ()
#6  0xb7c0482c in ?? ()
#7  0xb7c04828 in ?? ()
#8  0xb7c04824 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)
root@GUTSY:/opt/ifolder/bin# sudo apt-get install mono-mcs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mono-mcs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@GUTSY:/opt/ifolder/bin# sudo apt-get install mono
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mono
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1332B of archives.
After unpacking 28.7kB of additional disk space will be used.
Get:1 http://hive.gds.unomaha.edu gutsy/main mono 1.2.4-6ubuntu6 [1332B]
Fetched 1332B in 0s (1348B/s)          
Selecting previously deselected package mono.
(Reading database ... 107699 files and directories currently installed.)
Unpacking mono (from .../mono_1.2.4-6ubuntu6_i386.deb) ...
Setting up mono (1.2.4-6ubuntu6) ...

root@GUTSY:/opt/ifolder/bin# ./ifolder

** (iFolderClient.exe:4736): WARNING **: The following assembly referenced from /opt/ifolder/bin/iFolderClient.exe could not be loaded:
     Assembly:   SimiasClient    (assemblyref_index=6)
     Version:    1.4.7296.1
     Public Key: (none)
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/opt/ifolder/bin/).


** (iFolderClient.exe:4736): WARNING **: Could not load file or assembly 'SimiasClient, Version=1.4.7296.1, Culture=neutral' or one of its dependencies.
Stacktrace:


Native stacktrace:

        mono [0x8194ca6]
        mono [0x81770ed]
        [0xffffe440]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        mono [0x810f9a7]
        mono [0x811a390]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        mono [0x810f9a7]
        mono [0x811a390]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_type_load+0x62) [0x80f0cfa]
        mono [0x811a36e]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono [0x8176f1a]
        mono(mono_runtime_invoke+0x27) [0x80b0b2f]
        mono(mono_runtime_exec_main+0x142) [0x80b5383]
        mono(mono_runtime_run_main+0x27e) [0x80b5631]
        mono(mono_jit_exec+0xbd) [0x805a4cb]
        mono [0x805a5a8]
        mono(mono_main+0x1683) [0x805bdc9]
        mono [0x8059636]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d68050]
        mono [0x80595b1]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1210775856 (LWP 4736)]
[New Thread -1219994736 (LWP 4738)]
[New Thread -1214231664 (LWP 4737)]
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
  3 Thread -1214231664 (LWP 4737)  0xffffe410 in __kernel_vsyscall ()
  2 Thread -1219994736 (LWP 4738)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1210775856 (LWP 4736)  0xffffe410 in __kernel_vsyscall ()

Thread 3 (Thread -1214231664 (LWP 4737)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ecd9f6 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811bc9f in ?? ()
#3  0xb7a043ac in ?? ()
#4  0x00000000 in ?? ()

Thread 2 (Thread -1219994736 (LWP 4738)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7eca676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120dde in ?? ()
#3  0xb796f1dc in ?? ()
#4  0xb796f1c4 in ?? ()
#5  0xb7ec8541 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6  0x081210eb in ?? ()
#7  0xb796f1dc in ?? ()
#8  0xb796f1c4 in ?? ()
#9  0x00000000 in ?? ()

Thread 1 (Thread -1210775856 (LWP 4736)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e1e301 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f3d780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f3db4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xb7c0d844 in ?? ()
#6  0xb7c0d82c in ?? ()
#7  0xb7c0d828 in ?? ()
#8  0xb7c0d824 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)
root@GUTSY:/opt/ifolder/bin# clear

root@GUTSY:/opt/ifolder/bin# ./ifolder

** (iFolderClient.exe:4746): WARNING **: The following assembly referenced from /opt/ifolder/bin/iFolderClient.exe could not be loaded:
     Assembly:   SimiasClient    (assemblyref_index=6)
     Version:    1.4.7296.1
     Public Key: (none)
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/opt/ifolder/bin/).


** (iFolderClient.exe:4746): WARNING **: Could not load file or assembly 'SimiasClient, Version=1.4.7296.1, Culture=neutral' or one of its dependencies.
Stacktrace:


Native stacktrace:

        mono [0x8194ca6]
        mono [0x81770ed]
        [0xffffe440]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        mono [0x810f9a7]
        mono [0x811a390]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        mono [0x810f9a7]
        mono [0x811a390]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_type_load+0x62) [0x80f0cfa]
        mono [0x811a36e]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono [0x8176f1a]
        mono(mono_runtime_invoke+0x27) [0x80b0b2f]
        mono(mono_runtime_exec_main+0x142) [0x80b5383]
        mono(mono_runtime_run_main+0x27e) [0x80b5631]
        mono(mono_jit_exec+0xbd) [0x805a4cb]
        mono [0x805a5a8]
        mono(mono_main+0x1683) [0x805bdc9]
        mono [0x8059636]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d4d050]
        mono [0x80595b1]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1210886448 (LWP 4746)]
[New Thread -1220105328 (LWP 4748)]
[New Thread -1214342256 (LWP 4747)]
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
  3 Thread -1214342256 (LWP 4747)  0xffffe410 in __kernel_vsyscall ()
  2 Thread -1220105328 (LWP 4748)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1210886448 (LWP 4746)  0xffffe410 in __kernel_vsyscall ()

Thread 3 (Thread -1214342256 (LWP 4747)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7eb29f6 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811bc9f in ?? ()
#3  0xb79e93ac in ?? ()
#4  0x00000000 in ?? ()

Thread 2 (Thread -1220105328 (LWP 4748)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7eaf676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120dde in ?? ()
#3  0xb79541dc in ?? ()
#4  0xb79541c4 in ?? ()
#5  0xb7ead541 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6  0x081210eb in ?? ()
#7  0xb79541dc in ?? ()
#8  0xb79541c4 in ?? ()
#9  0x00000000 in ?? ()

Thread 1 (Thread -1210886448 (LWP 4746)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e03301 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f22780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f22b4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xb7bf2844 in ?? ()
#6  0xb7bf282c in ?? ()
#7  0xb7bf2828 in ?? ()
#8  0xb7bf2824 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)
root@GUTSY:/opt/ifolder/bin# sudo apt-get install libmono-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmono-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@GUTSY:/opt/ifolder/bin# sudo apt-get install libmono-dev   mono-xsp  mono-gmcs libflaim-dev libflaim4.1  liblog4net1.2-cil build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmono-dev is already the newest version.
mono-xsp is already the newest version.
mono-gmcs is already the newest version.
libflaim-dev is already the newest version.
libflaim4.1 is already the newest version.
liblog4net1.2-cil is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@GUTSY:/opt/ifolder/bin# clear

root@GUTSY:/opt/ifolder/bin# ./ifolder

** (iFolderClient.exe:4761): WARNING **: The following assembly referenced from /opt/ifolder/bin/iFolderClient.exe could not be loaded:
     Assembly:   SimiasClient    (assemblyref_index=6)
     Version:    1.4.7296.1
     Public Key: (none)
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/opt/ifolder/bin/).


** (iFolderClient.exe:4761): WARNING **: Could not load file or assembly 'SimiasClient, Version=1.4.7296.1, Culture=neutral' or one of its dependencies.
Stacktrace:


Native stacktrace:

        mono [0x8194ca6]
        mono [0x81770ed]
        [0xffffe440]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        mono [0x810f9a7]
        mono [0x811a390]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        mono [0x810f9a7]
        mono [0x811a390]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_type_load+0x62) [0x80f0cfa]
        mono [0x811a36e]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono [0x8176f1a]
        mono(mono_runtime_invoke+0x27) [0x80b0b2f]
        mono(mono_runtime_exec_main+0x142) [0x80b5383]
        mono(mono_runtime_run_main+0x27e) [0x80b5631]
        mono(mono_jit_exec+0xbd) [0x805a4cb]
        mono [0x805a5a8]
        mono(mono_main+0x1683) [0x805bdc9]
        mono [0x8059636]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d35050]
        mono [0x80595b1]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1210984752 (LWP 4761)]
[New Thread -1220203632 (LWP 4763)]
[New Thread -1214440560 (LWP 4762)]
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
  3 Thread -1214440560 (LWP 4762)  0xffffe410 in __kernel_vsyscall ()
  2 Thread -1220203632 (LWP 4763)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1210984752 (LWP 4761)  0xffffe410 in __kernel_vsyscall ()

Thread 3 (Thread -1214440560 (LWP 4762)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e9a9f6 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811bc9f in ?? ()
#3  0xb79d13ac in ?? ()
#4  0x00000000 in ?? ()

Thread 2 (Thread -1220203632 (LWP 4763)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e97676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120dde in ?? ()
#3  0xb793c1dc in ?? ()
#4  0xb793c1c4 in ?? ()
#5  0xb7e95541 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6  0x081210eb in ?? ()
#7  0xb793c1dc in ?? ()
#8  0xb793c1c4 in ?? ()
#9  0x00000000 in ?? ()

Thread 1 (Thread -1210984752 (LWP 4761)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7deb301 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f0a780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f0ab4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xb7bda844 in ?? ()
#6  0xb7bda82c in ?? ()
#7  0xb7bda828 in ?? ()
#8  0xb7bda824 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)

```

Thanks

---

### Post by ikus060 on 2007-10-29
I can't help you with your problem installing iFolder Client on gusty, because I experience my self some problem to install it. But, I'm really interesting to know how you manage to install iFolder Server on Gusty. If you can point on the documentation you use, it's could be a good start for me.

---

### Post by ikus060 on 2007-10-30
I get a very similar error if I execute iFolder by not using the ifolder.sh script, but calling mono iFolderClient.exe. Also, is it possible that you don't install Simias ??

---

### Post by _DjScrew_ on 2007-11-05
simias must be installed before ifolder. Simias does your syncing and all of that stuff, ifolder is just a module that sits on top of simias.

---

### Post by ikus060 on 2007-11-08
So it's working on gusty or not ??

---

### Post by KillerKiwi on 2008-03-16
see [http://alt-j.com/200712/ifolder-on-kubuntu-gutsy-710](http://alt-j.com/200712/ifolder-on-kubuntu-gutsy-710)

---

### Post by ikus060 on 2008-03-16
Thank for the reply, but I finnaly got it and I write the procedure on the Ubuntu wiki : [https://help.ubuntu.com/community/iFolderClient](https://help.ubuntu.com/community/iFolderClient)

I install the server and the client version on Ubuntu.

---

