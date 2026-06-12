---
title: "F-spot Encountered an error"
date: 2007-11-26
forum: General Help
---

### Post by bone2006 on 2007-11-26
I'm running kubuntu and I did a "sudo apt-get install f-spot" and I haven't been able to run f-spot.  I'm trying to use f-spot to upload to gallery

I get an error that says:
F-spot Encountered a Fatal Error
F-spot cannot find dbus session dbus.  Make sure dbus is configured properly or start a  new session for fspot using "dbus-launch f-spot"

If I open up a terminal and type in dbus-launch f-spot, then it will launch and it seems I can only import and there isn't anything to export to gallery.  And the shortcut keeps giving me the same error.

---

### Post by philven on 2008-02-15
I have the same problem and have not found a solution anywhere on the Internet nor in this forum.  I wonder if the programmer ever reads these posts?

---

### Post by hamid.nyc on 2008-04-25
In a terminal, try typing "dbus-launch f-stop" of course without the quotes.

---

### Post by linuxaz on 2008-04-26
Well,
I have the same error.  This is the output for me:

robert@robert-laptop:~$ dbus-launch f-spot
Unable to create /home/robert/.dbus/session-bus
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
	/lib/libpthread.so.0 [0x7fdcff95e7d0]
	/lib/libc.so.6(memcpy+0x60) [0x7fdcff3e9d50]
	f-spot(mono_breakpoint_clean_code+0x1b) [0x42725b]
	f-spot [0x43f78d]
	f-spot [0x44005e]
	[0x4024a15b]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7fdd006427a0 (LWP 20339)]
[New Thread 0x4045a950 (LWP 20346)]
[New Thread 0x40cd6950 (LWP 20345)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0x00007fdcff43dda2 in select () from /lib/libc.so.6
  3 Thread 0x40cd6950 (LWP 20345)  0x00007fdcff95de81 in nanosleep ()
   from /lib/libpthread.so.0
  2 Thread 0x4045a950 (LWP 20346)  0x00007fdcff95ab99 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  1 Thread 0x7fdd006427a0 (LWP 20339)  0x00007fdcff43dda2 in select ()
   from /lib/libc.so.6

Thread 3 (Thread 0x40cd6950 (LWP 20345)):
#0  0x00007fdcff95de81 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000004b8f4f in ?? ()
#2  0x00007fdcff9563f7 in start_thread () from /lib/libpthread.so.0
#3  0x00007fdcff444b2d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x4045a950 (LWP 20346)):
#0  0x00007fdcff95ab99 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb585 in ?? ()
#2  0x00000000004bdb37 in ?? ()
#3  0x00000000004cbc03 in ?? ()
#4  0x000000000046b3c1 in ?? ()
#5  0x00000000004855c3 in ?? ()
#6  0x00000000004cb287 in ?? ()
#7  0x00000000004e07d2 in ?? ()
#8  0x00007fdcff9563f7 in start_thread () from /lib/libpthread.so.0
#9  0x00007fdcff444b2d in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7fdd006427a0 (LWP 20339)):
#0  0x00007fdcff43dda2 in select () from /lib/libc.so.6
#1  0x00007fdcffdda9bc in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#2  0x00007fdcffddad98 in g_spawn_command_line_sync ()
   from /usr/lib/libglib-2.0.so.0
#3  0x000000000051bbf9 in ?? ()
#4  0x000000000043dacd in ?? ()
#5  <signal handler called>
#6  0x00007fdcff3e9d50 in memcpy () from /lib/libc.so.6
#7  0x000000000042725b in mono_breakpoint_clean_code ()
#8  0x000000000043f78d in ?? ()
#9  0x000000000044005e in ?? ()
#10 0x000000004024a15b in ?? ()
#11 0x0000000000000000 in ?? ()
#0  0x00007fdcff43dda2 in select () from /lib/libc.so.6


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

---

### Post by dozch on 2008-04-28
I got this error after upgrading from gutsy to hardy. The problem seemed to be that there was an old version of NDesk.DBus.dll in the /usr/lib/f-spot folder. Since this is the first folder f-spot will look in, this is the dbus dll that will be found and used. I don't know how it got there, as the NDesk dll's don't get installed here (by gutsy or hardy)

Anyway, what I did to fix it:

* uninstall f-spot using Synaptic/apt
* move (as sudo) the remainders of /usr/lib/f-spot some place safe:

  # sudo mv /usr/lib/f-spot ~/tmp/

* install f-spot again.

After this it worked again for me.

(I have seen this error reported for Banshee as well and it will probably have the same cause - so just clean up /usr/lib/banshee)

---

### Post by dozch on 2008-04-28
BTW For the record - my error message was:

System.ApplicationException: F-Spot cannot find the Dbus session bus.  Make
sure dbus is configured properly or start a new session for f-spot using
"dbus-launch f-spot" ---> System.Exception: Unable to open the system message
bus. ---> System.NullReferenceException: Object reference not set to an
instance of an object
  at NDesk.DBus.Signature.TypeToDType (System.Type type) [0x00000]
  at NDesk.DBus.Signature.TypeToDType (System.Type type) [0x00000]
  at NDesk.DBus.MessageWriter.Write (System.Type type, System.Object val)
[0x00000]
  at NDesk.DBus.MessageWriter.WriteStruct (System.Type type, System.Object val)
[0x00000]
  at NDesk.DBus.Message.WriteHeader () [0x00000]
  at NDesk.DBus.Connection.Send (NDesk.DBus.Message msg) [0x00000]
  at NDesk.DBus.Connection.SendWithReply (NDesk.DBus.Message msg) [0x00000]
  at NDesk.DBus.Connection.SendWithReplyAndBlock (NDesk.DBus.Message msg)
[0x00000]
  at NDesk.DBus.BusObject.Invoke (System.Reflection.MethodBase methodBase,
System.String methodName, System.Object[] inArgs, System.Object[]& outArgs,
System.Object& retVal, System.Exception& exception) [0x00000]
  at NDesk.DBus.DProxy.Invoke (IMessage message) [0x00000]
  at System.Runtime.Remoting.Proxies.RealProxy.PrivateInvoke
(System.Runtime.Remoting.Proxies.RealProxy rp, IMessage msg, System.Exception&
exc, System.Object[]& out_args) [0x00000] --- End of inner exception stack
trace ---

  at NDesk.DBus.Bus.get_System () [0x00000]
  at NDesk.DBus.BusG.Init () [0x00000]
  at FSpot.Driver.Main (System.String[] args) [0x00000] --- End of inner
exception stack trace ---

Bug report on Novell site: [https://bugzilla.novell.com/show_bug.cgi?id=338324]("https://bugzilla.novell.com/show_bug.cgi?id=338324")

---

### Post by linuxaz on 2008-04-28
I don't seem to have that .dll in the /usr/lib64/f-spot directory....
I do have one called Ndesk.Glitz.dll


Is this a global problem or just a select few?

linuxaz

---

### Post by Psykotik on 2008-05-04
If you think it is related to the bug openend on launchpad : [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/223079](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/223079)

feel you free to share your experience, we seem to be very few to experiment this bug.

---

### Post by johnruben on 2008-05-20
> **Psykotik said:**
> If you think it is related to the bug openend on launchpad : [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/223079](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/223079)

feel you free to share your experience, we seem to be very few to experiment this bug.
I'm also having the same problems as you guys with F-Spot listed above. Have you found a fix yet? If so, please let me have it.
Thanks
John

---

### Post by Psykotik on 2008-05-20
Check the launchpad link I gave; you'll found a workaround :)

---

### Post by linuxaz on 2008-05-20
Just and FYI,
My issues have been resolved by installing the updates to f-spot in the "proposed updates" repository.  You may wish to try them.

linuxaz

---

