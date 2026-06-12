---
title: "gnome-rdp libmono runtime error"
date: 2007-03-28
forum: General Help
---

### Post by miguelbmartinez on 2007-03-28
I seem to be having an issue with gnome-rdp and libmono.  When I try to run gnome-rdp I get the following;
root@athena:/etc/apt# gnome-rdp

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.
=================================================================

Stacktrace:


Native stacktrace:

        /usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xe3) [0x4009d43f]
        /usr/lib/libmono.so.0 [0x4005f03e]
        /lib/libpthread.so.0 [0x402985ca]
        [0xffffe440]
        [0x40cc9f72]
        [0x40cc97f8]
        [0x40cc3b49]
        [0x40cc38fa]
        [0x40cc3823]
        /usr/lib/libmono.so.0 [0x4007c438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0x400deeed]
        /usr/lib/libmono.so.0(mono_runtime_exec_main+0x67) [0x400e1a88]
        /usr/lib/libmono.so.0(mono_runtime_run_main+0x188) [0x400e4bf0]
        /usr/lib/libmono.so.0(mono_jit_exec+0x90) [0x4008eb5e]
        /usr/lib/libmono.so.0(mono_main+0x962) [0x4008f54f]
        /lib/libc.so.6(__libc_start_main+0xa3) [0x4032731f]
        /usr/bin/mono [0x8048459]
Aborted
root@athena:/etc/apt#

In this case you can see that I'm trying to run as root, but I get the same error using my own account.  I've tried reinstalling the libraries and gnome-rdp, thinking that maybe I corrupted something during one of it's past crashes, but I've got nothing.  Anyone got an idea about this?

Thanks

---

### Post by miguelbmartinez on 2007-03-28
Is this the wrong forum to put this question in?

---

