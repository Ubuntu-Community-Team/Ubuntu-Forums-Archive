---
title: "F-spot crashed upon startup"
date: 2008-05-10
forum: General Help
---

### Post by enoughsaid05 on 2008-05-10
Hi all

I just installed F-spot and it crashed upon start up, as in it couldn't start in the first place.

How do I resolve the problem?

---

### Post by ibutho on 2008-05-10
Run Menu -> Accessories -> Terminal and enter the command "f-spot" (without the quotes). If it fails to start an error message will be printed on the screen. Post the error message here.

---

### Post by enoughsaid05 on 2008-05-11
Hi

sorry for the late reply, this is the output:

user@user-laptop~$ f-spot
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
	/lib/libpthread.so.0 [0x7f777859f7d0]
	/lib/libc.so.6(memcpy+0x60) [0x7f777802ad50]
	f-spot(mono_breakpoint_clean_code+0x1b) [0x42725b]
	f-spot [0x43f78d]
	f-spot [0x44005e]
	[0x4034015b]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7f77792807a0 (LWP 7452)]
[New Thread 0x40b5a950 (LWP 7454)]
[New Thread 0x41090950 (LWP 7453)]
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
0x00007f777807eda2 in select () from /lib/libc.so.6
  3 Thread 0x41090950 (LWP 7453)  0x00007f777859ee81 in nanosleep ()
   from /lib/libpthread.so.0
  2 Thread 0x40b5a950 (LWP 7454)  0x00007f777859bb99 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  1 Thread 0x7f77792807a0 (LWP 7452)  0x00007f777807eda2 in select ()
   from /lib/libc.so.6

Thread 3 (Thread 0x41090950 (LWP 7453)):
#0  0x00007f777859ee81 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000004b8f4f in ?? ()
#2  0x00007f77785973f7 in start_thread () from /lib/libpthread.so.0
#3  0x00007f7778085b2d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x40b5a950 (LWP 7454)):
#0  0x00007f777859bb99 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb585 in ?? ()
#2  0x00000000004bdb37 in ?? ()
#3  0x00000000004cbc03 in ?? ()
#4  0x000000000046b3c1 in ?? ()
#5  0x00000000004855c3 in ?? ()
#6  0x00000000004cb287 in ?? ()
#7  0x00000000004e07d2 in ?? ()
#8  0x00007f77785973f7 in start_thread () from /lib/libpthread.so.0
#9  0x00007f7778085b2d in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f77792807a0 (LWP 7452)):
#0  0x00007f777807eda2 in select () from /lib/libc.so.6
#1  0x00007f7778a1b9bc in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#2  0x00007f7778a1bd98 in g_spawn_command_line_sync ()
   from /usr/lib/libglib-2.0.so.0
#3  0x000000000051bbf9 in ?? ()
#4  0x000000000043dacd in ?? ()
#5  <signal handler called>
#6  0x00007f777802ad50 in memcpy () from /lib/libc.so.6
#7  0x000000000042725b in mono_breakpoint_clean_code ()
#8  0x000000000043f78d in ?? ()
#9  0x000000000044005e in ?? ()
#10 0x000000004034015b in ?? ()
#11 0x0000000000000000 in ?? ()
#0  0x00007f777807eda2 in select () from /lib/libc.so.6


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

---

### Post by Timokl on 2008-05-11
I face the same problem with the same error message.

I run Hardy 64 Bit. 

There seems to be an issue with Mono.

Timo

---

### Post by PsychoAlienDog on 2008-05-18
I'm having a similar problem.  I'm running Kubuntu 8.04 32bit. Try starting f-spot with:
```

dbus-launch f-spot

```

---

### Post by Rocktman2 on 2008-10-22
I'm also having a startup problem with f-spot (mine is installed by default). I've uninstalled & re-installed it. No success.

Running it in a terminal:

Starting new FSpot server
Updating F-Spot Database
Updated database from version NULL to 1
Updated database from version 1 to 2

Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000]

Running it in a terminal with dbus-launch f-spot:

Starting new FSpot server
Updating F-Spot Database
Updated database from version NULL to 1
Updated database from version 1 to 2

Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000]

It doesn't run in either case. Anybody got a clue?

---

### Post by directhex on 2008-10-22
> **Rocktman2 said:**
> I'm also having a startup problem with f-spot (mine is installed by default). I've uninstalled & re-installed it. No success.

Running it in a terminal:

Starting new FSpot server
Updating F-Spot Database
Updated database from version NULL to 1
Updated database from version 1 to 2

Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000]

Running it in a terminal with dbus-launch f-spot:

Starting new FSpot server
Updating F-Spot Database
Updated database from version NULL to 1
Updated database from version 1 to 2

Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000]

It doesn't run in either case. Anybody got a clue?

First, try running "f-spot-sqlite-upgrade"

Failing that (and this will delete all of F-Spot's configs), run "rm -r ~/.gnome2/f-spot"

---

### Post by directhex on 2008-10-22
> **enoughsaid05 said:**
> Hi

sorry for the late reply, this is the output:

*snip*

A native stack trace is a bad thing to see. What kind of CPU are you using?

---

### Post by Rocktman2 on 2008-10-22
> **directhex said:**
> First, try running "f-spot-sqlite-upgrade"

Failing that (and this will delete all of F-Spot's configs), run "rm -r ~/.gnome2/f-spot"

"f-spot-sqlite-upgrade" returned "Database is already upgraded"

However, "rm -r ~/.gnome2/f-spot" appears to have solved the problem.

Thanks directhex.

---

### Post by Jac[ITA] on 2008-11-30
Same problem here. Any info on how to solve? 

For reference here is the message:
> jacopo@HAL9001:~$ f-spot
[Info  21:03:06.596] Initializing DBus
[Info  21:03:07.137] Initializing Mono.Addins
[Info  21:03:07.987] Starting new FSpot server
[Info  21:03:11.467] Starting BeagleService
[Info  21:03:11.468] Hack for gnome-settings-daemon engaged
Stacktrace:

  at (wrapper managed-to-native) Gtk.Style.gtk_paint_box (intptr,intptr,int,int,intptr,intptr,intptr,int,int,int,int) <0x00004>
  at (wrapper managed-to-native) Gtk.Style.gtk_paint_box (intptr,intptr,int,int,intptr,intptr,intptr,int,int,int,int) <0xffffffff>
  at Gtk.Style.PaintBox (Gtk.Style,Gdk.Drawable,Gtk.StateType,Gtk.ShadowType,Gdk.Rectangle,Gtk.Widget,string,int,int,int,int) <0x0016c>
  at Limit.Draw (Gdk.Rectangle) <0x0015f>
  at FSpot.GroupSelector.OnExposeEvent (Gdk.EventExpose) <0x00716>
  at Gtk.Widget.exposeevent_cb (intptr,intptr) <0x00060>
  at (wrapper native-to-managed) Gtk.Widget.exposeevent_cb (intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x00007>
  at Gnome.Program.Run () <0x00007>
  at FSpot.Driver.Main (string[]) <0x015ec>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	f-spot [0x817b4ae]
	f-spot [0x807f78b]
	[0xb8066410]
	/usr/lib/libgdk-x11-2.0.so.0 [0xb672bc1d]
	/usr/lib/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x162) [0xb66ffac2]
	/usr/lib/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x162) [0xb66ffac2]
	/usr/lib/libgdk-x11-2.0.so.0 [0xb671af74]
	/usr/lib/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x162) [0xb66ffac2]
	/usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so [0xb5aadebd]
	/usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so [0xb5aaf2aa]
	/usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so [0xb5aabd16]
	/usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so [0xb5aace25]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_paint_box+0xee) [0xb6915c2e]
	[0xb41cbbaf]
	[0xb41cbb1d]
	[0xb41cb7d8]
	[0xb41ca887]
	[0xb41c9009]
	[0xb44031a8]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb68a0036]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab) [0xb6543c4b]
	/usr/lib/libgobject-2.0.so.0 [0xb6559d3d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x65b) [0xb655b62b]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb655bc26]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb69b533e]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1b3) [0xb6816163]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6816191]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb67e4816]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96) [0xb6816d36]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6818420]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb68a0036]
	/usr/lib/libgobject-2.0.so.0 [0xb65423c9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0xb6543b78]
	/usr/lib/libgobject-2.0.so.0 [0xb6559d3d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x65b) [0xb655b62b]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb655bc26]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb69b533e]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1b3) [0xb6816163]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6816191]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb68c4dda]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96) [0xb6816d36]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6818420]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb68c797f]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb68a0036]
	/usr/lib/libgobject-2.0.so.0 [0xb65423c9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0xb6543b78]
	/usr/lib/libgobject-2.0.so.0 [0xb6559d3d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x65b) [0xb655b62b]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb655bc26]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb69b533e]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1b3) [0xb6816163]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6816191]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb67e4816]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96) [0xb6816d36]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6818420]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb68a0036]

	/usr/lib/libgobject-2.0.so.0 [0xb65423c9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0xb6543b78]
	/usr/lib/libgobject-2.0.so.0 [0xb6559d3d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x65b) [0xb655b62b]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb655bc26]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb69b533e]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1b3) [0xb6816163]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6816191]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb67e4816]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96) [0xb6816d36]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6818420]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb68a0036]
	/usr/lib/libgobject-2.0.so.0 [0xb65423c9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0xb6543b78]
	/usr/lib/libgobject-2.0.so.0 [0xb6559d3d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x65b) [0xb655b62b]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb655bc26]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb69b533e]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1b3) [0xb6816163]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6816191]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb67e086d]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96) [0xb6816d36]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6818420]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb69ceeb1]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb68a0036]
	/usr/lib/libgobject-2.0.so.0 [0xb65423c9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab) [0xb6543c4b]
	/usr/lib/libgobject-2.0.so.0 [0xb6559d3d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x65b) [0xb655b62b]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb655bc26]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb69b533e]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x52d) [0xb689a13d]
	/usr/lib/libgdk-x11-2.0.so.0 [0xb67189b5]
	/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0xff) [0xb6718fcf]
	/usr/lib/libgdk-x11-2.0.so.0 [0xb6718ffb]
	/usr/lib/libgdk-x11-2.0.so.0 [0xb66fc46b]
	/usr/lib/libglib-2.0.so.0 [0xb7faa7c1]
	/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8) [0xb7fac6f8]
	/usr/lib/libglib-2.0.so.0 [0xb7fafda3]
	/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1d2) [0xb7fb02c2]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9) [0xb689a3a9]
	[0xb41c46ee]
	[0xb41c46b8]
	[0xb41c46a0]
	[0xb7897dfd]
	[0xb78961c4]
	f-spot(mono_runtime_exec_main+0xf7) [0x809cbb7]
	f-spot(mono_runtime_run_main+0x16b) [0x809d19b]
	f-spot(mono_main+0x60e) [0x805af2e]
	f-spot [0x805a432]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7de8685]
	f-spot [0x805a371]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7da66d0 (LWP 13098)]
[New Thread 0xb42ceb90 (LWP 13110)]
[New Thread 0xb4402b90 (LWP 13109)]
[New Thread 0xb489ab90 (LWP 13103)]
[New Thread 0xb730db90 (LWP 13100)]
[New Thread 0xb7331b90 (LWP 13099)]
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
0xb8066430 in __kernel_vsyscall ()
  6 Thread 0xb7331b90 (LWP 13099)  0xb8066430 in __kernel_vsyscall ()
  5 Thread 0xb730db90 (LWP 13100)  0xb8066430 in __kernel_vsyscall ()
  4 Thread 0xb489ab90 (LWP 13103)  0xb8066430 in __kernel_vsyscall ()
  3 Thread 0xb4402b90 (LWP 13109)  0xb8066430 in __kernel_vsyscall ()
  2 Thread 0xb42ceb90 (LWP 13110)  0xb8066430 in __kernel_vsyscall ()
  1 Thread 0xb7da66d0 (LWP 13098)  0xb8066430 in __kernel_vsyscall ()

Thread 6 (Thread 0xb7331b90 (LWP 13099)):
#0  0xb8066430 in __kernel_vsyscall ()
#1  0xb7f63906 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08110fc8 in ?? ()
#3  0xb7f5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7eb37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xb730db90 (LWP 13100)):
#0  0xb8066430 in __kernel_vsyscall ()
#1  0xb7f60075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081143b7 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080b5c1a in ?? ()
#7  0x080d5f74 in ?? ()
#8  0x081279de in ?? ()
#9  0x0813ff75 in ?? ()
#10 0xb7f5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7eb37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xb489ab90 (LWP 13103)):
#0  0xb8066430 in __kernel_vsyscall ()
#1  0xb7f603a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080d3013 in ?? ()
#7  0xb5a2ac92 in ?? ()
#8  0xb5a2aa83 in ?? ()
#9  0xb5a2a9ae in ?? ()
#10 0xb5c768f1 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d5fdf in ?? ()
#13 0x081279de in ?? ()
#14 0x0813ff75 in ?? ()
#15 0xb7f5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7eb37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xb4402b90 (LWP 13109)):
#0  0xb8066430 in __kernel_vsyscall ()
#1  0xb7f603a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080d1821 in ?? ()
#7  0xb42f620a in ?? ()
#8  0xb42f60ee in ?? ()
#9  0xb42f5fe0 in ?? ()
#10 0xb5c768f1 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d5fdf in ?? ()
#13 0x081279de in ?? ()
#14 0x0813ff75 in ?? ()
#15 0xb7f5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7eb37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb42ceb90 (LWP 13110)):
#0  0xb8066430 in __kernel_vsyscall ()
#1  0xb7f603a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080d1821 in ?? ()
#7  0xb42f620a in ?? ()
#8  0xb42f60ee in ?? ()
#9  0xb42f639e in ?? ()
#10 0xb5c768f1 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d5fdf in ?? ()
#13 0x081279de in ?? ()
#14 0x0813ff75 in ?? ()
#15 0xb7f5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7eb37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7da66d0 (LWP 13098)):
#0  0xb8066430 in __kernel_vsyscall ()
#1  0xb7eabc01 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7fe598b in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7fe5d3c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0817b565 in ?? ()
#5  0x0807f78b in ?? ()
#6  <signal handler called>
#7  0xb7e4ab56 in memcpy () from /lib/tls/i686/cmov/libc.so.6
#8  0x0a402e2c in ?? ()
#9  0xb672bc1d in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#10 0xb66ffac2 in gdk_draw_pixbuf () from /usr/lib/libgdk-x11-2.0.so.0
#11 0xb66ffac2 in gdk_draw_pixbuf () from /usr/lib/libgdk-x11-2.0.so.0
#12 0xb671af74 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#13 0xb66ffac2 in gdk_draw_pixbuf () from /usr/lib/libgdk-x11-2.0.so.0
#14 0xb5aadebd in ?? () from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
#15 0xb5aaf2aa in ?? () from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
#16 0xb5aabd16 in ?? () from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
#17 0xb5aace25 in ?? () from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
#18 0xb6915c2e in gtk_paint_box () from /usr/lib/libgtk-x11-2.0.so.0
#19 0xb41cbbaf in ?? ()
#20 0xb41cbb1d in ?? ()
#21 0xb41cb7d8 in ?? ()
#22 0xb41ca887 in ?? ()
#23 0xb41c9009 in ?? ()
#24 0xb44031a8 in ?? ()
#25 0xb68a0036 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#26 0xb6543c4b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#27 0xb6559d3d in ?? () from /usr/lib/libgobject-2.0.so.0
#28 0xb655b62b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#29 0xb655bc26 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#30 0xb69b533e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#31 0xb6816163 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#32 0xb6816191 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#33 0xb67e4816 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#34 0xb6816d36 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#35 0xb6818420 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#36 0xb68a0036 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#37 0xb65423c9 in ?? () from /usr/lib/libgobject-2.0.so.0
#38 0xb6543b78 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#39 0xb6559d3d in ?? () from /usr/lib/libgobject-2.0.so.0
#40 0xb655b62b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#41 0xb655bc26 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#42 0xb69b533e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#43 0xb6816163 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#44 0xb6816191 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#45 0xb68c4dda in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#46 0xb6816d36 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#47 0xb6818420 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#48 0xb68c797f in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#49 0xb68a0036 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#50 0xb65423c9 in ?? () from /usr/lib/libgobject-2.0.so.0
#51 0xb6543b78 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#52 0xb6559d3d in ?? () from /usr/lib/libgobject-2.0.so.0
#53 0xb655b62b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#54 0xb655bc26 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#55 0xb69b533e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#56 0xb6816163 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#57 0xb6816191 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#58 0xb67e4816 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#59 0xb6816d36 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#60 0xb6818420 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#61 0xb68a0036 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#62 0xb65423c9 in ?? () from /usr/lib/libgobject-2.0.so.0
#63 0xb6543b78 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#64 0xb6559d3d in ?? () from /usr/lib/libgobject-2.0.so.0
#65 0xb655b62b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#66 0xb655bc26 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#67 0xb69b533e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#68 0xb6816163 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#69 0xb6816191 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#70 0xb67e4816 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#71 0xb6816d36 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#72 0xb6818420 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#73 0xb68a0036 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#74 0xb65423c9 in ?? () from /usr/lib/libgobject-2.0.so.0
#75 0xb6543b78 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#76 0xb6559d3d in ?? () from /usr/lib/libgobject-2.0.so.0
#77 0xb655b62b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#78 0xb655bc26 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#79 0xb69b533e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#80 0xb6816163 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#81 0xb6816191 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#82 0xb67e086d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#83 0xb6816d36 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#84 0xb6818420 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#85 0xb69ceeb1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#86 0xb68a0036 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#87 0xb65423c9 in ?? () from /usr/lib/libgobject-2.0.so.0
#88 0xb6543c4b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#89 0xb6559d3d in ?? () from /usr/lib/libgobject-2.0.so.0
#90 0xb655b62b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#91 0xb655bc26 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#92 0xb69b533e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#93 0xb689a13d in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#94 0xb67189b5 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#95 0xb6718fcf in gdk_window_process_all_updates ()
   from /usr/lib/libgdk-x11-2.0.so.0
#96 0xb6718ffb in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#97 0xb66fc46b in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#98 0xb7faa7c1 in ?? () from /usr/lib/libglib-2.0.so.0
#99 0xb7fac6f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#100 0xb7fafda3 in ?? () from /usr/lib/libglib-2.0.so.0
#101 0xb7fb02c2 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#102 0xb689a3a9 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#103 0xb41c46ee in ?? ()
#104 0xb41c46b8 in ?? ()
#105 0xb41c46a0 in ?? ()
#106 0xb7897dfd in ?? ()
#107 0xb78961c4 in ?? ()
#108 0x0809cbb7 in mono_runtime_exec_main ()
#109 0x0809d19b in mono_runtime_run_main ()
#110 0x0805af2e in mono_main ()
#111 0x0805a432 in ?? ()
#112 0xb7de8685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#113 0x0805a371 in ?? ()
#0  0xb8066430 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
jacopo@HAL9001:~$ 


TIA

---

### Post by Jac[ITA] on 2008-12-02
Nevermind, probelm solved! It was a customized theme, I've put back the Human theme and now F-spot works.

---

