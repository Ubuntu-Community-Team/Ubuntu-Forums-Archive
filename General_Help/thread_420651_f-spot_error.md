---
title: "f-spot error"
date: 2007-04-23
forum: General Help
---

### Post by auditory on 2007-04-23
using feisty upgraded from edgy,
f-spot doesn't start up after upgrade.

i searched forum and other people fixed it by installing libgl1-mesa-dev,
but in my case it doesn't work.

here is error message in console.

```
$ f-spot
Starting new FSpot server

(f-spot:2291): libglade-WARNING **: unknown attribute `comment' for <property>.
Stacktrace:

  at (wrapper managed-to-native) Gtk.Container.gtk_container_add (intptr,intptr) <0x00004>
  at (wrapper managed-to-native) Gtk.Container.gtk_container_add (intptr,intptr) <0xffffffff>
  at Gtk.Container.Add (Gtk.Widget) <0x00037>
  at MainWindow..ctor (Db) <0x0191d>
  at FSpot.Core.get_MainWindow () <0x0002a>
  at FSpot.Core.Organize () <0x0000f>
  at FSpot.Driver.Main (string[]) <0x006ea>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

        f-spot [0x818f7de]
        f-spot [0x8171be4]
        [0xffffe440]
        /usr/lib/libstdc++.so.6(_ZdlPv+0x21) [0xa1606d11]
        /usr/lib/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1d) [0xa15e3a5d]
        /usr/lib/libstdc++.so.6(_ZNSsD1Ev+0x57) [0xa15e65e7]
        /usr/lib/libscim-1.0.so.8 [0xa168e04b]
        /usr/lib/libscim-1.0.so.8(_ZN4scim23scim_global_config_readERKSsi+0x95) [0xa168ffe5]
        /usr/lib/libscim-1.0.so.8(_ZN4scim31scim_get_default_socket_timeoutEv+0x46) [0xa16bc3c6]
        /usr/lib/libscim-1.0.so.8(_ZN4scim11PanelClient15PanelClientImplC1Ev+0x24) [0xa16b8714]
        /usr/lib/libscim-1.0.so.8(_ZN4scim11PanelClientC1Ev+0x30) [0xa16b7e90]
        /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so [0xa18a07e1]
        /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so [0xa18b0306]
        /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so [0xa189e941]
        /lib/ld-linux.so.2 [0xb7f00373]
        /lib/ld-linux.so.2 [0xb7f00483]
        /lib/ld-linux.so.2 [0xb7f03fad]
        /lib/ld-linux.so.2 [0xb7efffa6]
        /lib/ld-linux.so.2 [0xb7f038ee]
        /lib/tls/i686/cmov/libdl.so.2 [0xb7e3ac2d]
        /lib/ld-linux.so.2 [0xb7efffa6]
        /lib/tls/i686/cmov/libdl.so.2 [0xb7e3b2ac]
        /lib/tls/i686/cmov/libdl.so.2(dlopen+0x44) [0xb7e3ab64]
        /usr/lib/libgmodule-2.0.so.0(g_module_open+0x169) [0xb7ed45d9]
        /usr/lib/libgtk-x11-2.0.so.0 [0xb66fd429]
        /usr/lib/libgobject-2.0.so.0(g_type_module_use+0x88) [0xb61c89e8]
        /usr/lib/libgtk-x11-2.0.so.0(_gtk_im_module_create+0x5e) [0xb66fdcce]
        /usr/lib/libgtk-x11-2.0.so.0 [0xb66fe93b]
        /usr/lib/libgtk-x11-2.0.so.0 [0xb66feb39]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_im_context_set_client_window+0x4e) [0xb66fbf0e]
        /usr/lib/libgtk-x11-2.0.so.0 [0xb66a571f]
        /usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49) [0xb61b49d9]
        /usr/lib/libgobject-2.0.so.0 [0xb61a5e49]
        /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b) [0xb61a762b]
        /usr/lib/libgobject-2.0.so.0 [0xb61b859a]
        /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7) [0xb61b9627]
        /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29) [0xb61b97e9]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xba) [0xb6839bea]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x1de) [0xb683a1ce]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_box_pack_start+0x10c) [0xb664c71c]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_box_pack_start_defaults+0x30) [0xb664c7d0]
        /usr/lib/libgtk-x11-2.0.so.0 [0xb664c7f8]
        /usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x59) [0xb61b3ee9]
        /usr/lib/libgobject-2.0.so.0 [0xb61a5e49]
        /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b) [0xb61a762b]
        /usr/lib/libgobject-2.0.so.0 [0xb61b859a]
        /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7) [0xb61b9627]
        /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29) [0xb61b97e9]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_container_add+0x12c) [0xb66891bc]
        [0xb4a57328]
        [0xb4a572d8]
        [0xb4bd8a66]
        [0xb4bd5923]
        [0xb4bd58b8]
        [0xb71a75eb]
        [0xb71a6063]
        f-spot [0x8171aaf]
        f-spot(mono_runtime_invoke+0x27) [0x80b038f]
        f-spot(mono_runtime_exec_main+0x142) [0x80b4bd4]
        f-spot(mono_runtime_run_main+0x27e) [0x80b4e84]
        f-spot(mono_jit_exec+0xbd) [0x805a55b]
        f-spot [0x805a638]
        f-spot(mono_main+0x1666) [0x805be3c]
        f-spot [0x80596c6]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7cd0ebc]
        f-spot [0x8059621]

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
[New Thread -1211394336 (LWP 2291)]
[New Thread -1281856624 (LWP 2297)]
[New Thread -1280803952 (LWP 2296)]
[New Thread -1223017584 (LWP 2293)]
[New Thread -1217266800 (LWP 2292)]
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
  5 Thread -1217266800 (LWP 2292)  0xffffe410 in __kernel_vsyscall ()
  4 Thread -1223017584 (LWP 2293)  0xffffe410 in __kernel_vsyscall ()
  3 Thread -1280803952 (LWP 2296)  0xffffe410 in __kernel_vsyscall ()
  2 Thread -1281856624 (LWP 2297)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1211394336 (LWP 2291)  0xffffe410 in __kernel_vsyscall ()

Thread 5 (Thread -1217266800 (LWP 2292)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e2f986 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811700b in ?? ()
#3  0xb771f39c in ?? ()
#4  0x00000000 in ?? ()

Thread 4 (Thread -1223017584 (LWP 2293)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e2c5c6 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811c14a in ?? ()
#3  0xb768d1dc in ?? ()
#4  0xb768d1c4 in ?? ()
#5  0xb71a3178 in ?? ()
#6  0x00000000 in ?? ()

Thread 3 (Thread -1280803952 (LWP 2296)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e2c84c in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811c1c7 in ?? ()
#3  0xb768d614 in ?? ()
#4  0xb768d5fc in ?? ()
#5  0xb3a87054 in ?? ()
#6  0x00000000 in ?? ()

Thread 2 (Thread -1281856624 (LWP 2297)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e2c84c in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811c1c7 in ?? ()
#3  0xb768d6ec in ?? ()
#4  0xb768d6d4 in ?? ()
#5  0xb398604c in ?? ()
#6  0x00000000 in ?? ()

Thread 1 (Thread -1211394336 (LWP 2291)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7d833d1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e974a0 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7e9786c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0818f8bc in ?? ()
#5  0xbfaaad74 in ?? ()
#6  0xbfaaad5c in ?? ()
#7  0xbfaaad58 in ?? ()
#8  0xbfaaad54 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```

---

