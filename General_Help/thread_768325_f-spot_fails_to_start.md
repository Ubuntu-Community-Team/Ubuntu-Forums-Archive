---
title: "f-spot fails to start"
date: 2008-04-26
forum: General Help
---

### Post by SergeTheSeal on 2008-04-26
I am new to Ubuntu and fairly new to linux.

Having just installed Hardy I have tried to run the f-spot application
the the following results.

jason@DEMANTOID:~$ f-spot
Stacktrace:

  at FSpot.Global..cctor () <0xffffffff>
  at FSpot.Global..cctor () <0x0000d>
  at (wrapper runtime-invoke) FSpot.Defines.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at FSpot.Driver.Main (string[]) <0xffffffff>
  at FSpot.Driver.Main (string[]) <0x00144>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	f-spot [0x51bb67]
	f-spot [0x43dacd]
	/lib/libpthread.so.0 [0x7fc2e2d6a7d0]
	/lib/libc.so.6(memcpy+0x60) [0x7fc2e27f5d50]
	f-spot(mono_breakpoint_clean_code+0x1b) [0x42725b]
	f-spot [0x43f78d]
	f-spot [0x44005e]
	[0x400b115b]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7fc2e3a4d7a0 (LWP 6565)]
[New Thread 0x40bb2950 (LWP 6567)]
[New Thread 0x40e7f950 (LWP 6566)]
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
0x00007fc2e2d695cb in read () from /lib/libpthread.so.0
  3 Thread 0x40e7f950 (LWP 6566)  0x00007fc2e2d69e81 in nanosleep ()
   from /lib/libpthread.so.0
  2 Thread 0x40bb2950 (LWP 6567)  0x00007fc2e2d66b99 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  1 Thread 0x7fc2e3a4d7a0 (LWP 6565)  0x00007fc2e2d695cb in read ()
   from /lib/libpthread.so.0

Thread 3 (Thread 0x40e7f950 (LWP 6566)):
#0  0x00007fc2e2d69e81 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000004b8f4f in ?? ()
#2  0x00007fc2e2d623f7 in start_thread () from /lib/libpthread.so.0
#3  0x00007fc2e2850b2d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x40bb2950 (LWP 6567)):
#0  0x00007fc2e2d66b99 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb585 in ?? ()
#2  0x00000000004bdb37 in ?? ()
#3  0x00000000004cbc03 in ?? ()
#4  0x000000000046b3c1 in ?? ()
#5  0x00000000004855c3 in ?? ()
#6  0x00000000004cb287 in ?? ()
#7  0x00000000004e07d2 in ?? ()
#8  0x00007fc2e2d623f7 in start_thread () from /lib/libpthread.so.0
#9  0x00007fc2e2850b2d in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7fc2e3a4d7a0 (LWP 6565)):
#0  0x00007fc2e2d695cb in read () from /lib/libpthread.so.0
#1  0x00007fc2e31e5a90 in ?? () from /usr/lib/libglib-2.0.so.0
#2  0x00007fc2e31e5f7e in ?? () from /usr/lib/libglib-2.0.so.0
#3  0x00007fc2e31e68df in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#4  0x00007fc2e31e6d98 in g_spawn_command_line_sync ()
   from /usr/lib/libglib-2.0.so.0
#5  0x000000000051bbf9 in ?? ()
#6  0x000000000043dacd in ?? ()
#7  <signal handler called>
#8  0x00007fc2e27f5d50 in memcpy () from /lib/libc.so.6
#9  0x000000000042725b in mono_breakpoint_clean_code ()
#10 0x000000000043f78d in ?? ()
#11 0x000000000044005e in ?? ()
#12 0x00000000400b115b in ?? ()
#13 0x0000000000000000 in ?? ()
#0  0x00007fc2e2d695cb in read () from /lib/libpthread.so.0


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted


Any help would be appreciated

thanks

---

### Post by linuxaz on 2008-04-26
Serge,
I had the exact same problem.  I filed a bug report at launchpad for it.  I think it is a Mono problem.....

linuxaz

---

### Post by blackbeastofaarrgh on 2008-04-28
Having the same problem, guys. :(

---

### Post by Psykotik on 2008-05-04
If you think it is related to the bug openend on launchpad : [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/223079](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/223079)

feel you free to share your experience, we seem to be very few to experiment this bug.

---

