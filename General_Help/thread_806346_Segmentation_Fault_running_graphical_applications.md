---
title: "Segmentation Fault running graphical applications"
date: 2008-05-24
forum: General Help
---

### Post by rampageoberon on 2008-05-24
I seem to get graphical applications crash with Segmentation Fault when I insert a blank disc. i am running these applications as a different user from the user logged in (firewall purposes).

Not sure what the problem can be, as it only seems to happen with a blank disc in and the applications run fine under the user logged in with the disc in the drive.

Thanks

---

### Post by rampageoberon on 2008-05-27
Anyone able to help with this please?

---

### Post by rampageoberon on 2008-06-02
I'm guessing thats a no then :(

---

### Post by RAOF on 2008-06-02
You aren't providing enough information to make a reasonable diagnosis of your problem.  Interesting information would include: what program(s) are affected.  If you run them from the terminal, what is the output generated when you insert a blank disc?  There's plenty more interesting information, but this would probably be enough to get started.

---

### Post by rampageoberon on 2008-06-02
I've tried this with LinuxDC++ and VLC only. So At a guess I'd say graphical applications.

Here is the output I get running LinuxDC++ (it is the same for VLC)

```

Loading: Hash database
Loading: Shared Files
Loading: Download Queue
Segmentation Fault

```

I tried running a gdb trace but it was not helpful. Here is the output:

```

GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law. Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(gdb) start
Breakpoint 1 at 0x8260eed: file linux/wulfor.cc, line 40.
Starting program: /usr/bin/linuxdcpp
[Thread debugging using libthread_db enabled]
[New Thread 0xb71c2b20 (LWP 7739)]
[Switching to Thread 0xb71c2b20 (LWP 7739)]
main (argc=1, argv=0xbf8b6ea4) at linux/wulfor.cc:40
40 bindtextdomain("linuxdcpp", _DATADIR "/locale");
(gdb) cont
Continuing.
Thrown: FileException: Could not open file
Thrown: FileException: Could not open file
Loading: Hash database
[New Thread 0xb707db90 (LWP 7742)]
Loading: Shared Files
UnBZFilter end, 773401/271746 = 2.8460
[New Thread 0xb687cb90 (LWP 7743)]
Loading: Download Queue
[New Thread 0xb607bb90 (LWP 7744)]
[New Thread 0xb582fb90 (LWP 7745)]
[New Thread 0xb502eb90 (LWP 7746)]
[New Thread 0xb4746b90 (LWP 7748)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb4746b90 (LWP 7748)]
0x00000000 in ?? ()
(gdb) bt full
#0 0x00000000 in ?? ()
No symbol table info available.
#1 0xb47c9f31 in ?? () from /usr/lib/libgio-2.0.so.0
No symbol table info available.
#2 0x086c5348 in ?? ()
No symbol table info available.
#3 0x00000000 in ?? ()
No symbol table info available.
(gdb) quit
The program is running. Exit anyway? (y or n) y

```

Hope that is helpful for you. Thanks again

---

### Post by RAOF on 2008-06-02
Hm.  Curious.  I'm surprised that GIO is even *loaded* by linux DC++.  This should probably be filed as a bug on Launchpad, possibly against the glib2.0 source package.

Installing the debugging symbols for glib would probably be useful.  [https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash) for details there.

---

### Post by rampageoberon on 2008-06-02
I had installed the libglib2.0-0-dbg before I ran the gdb.

As adviced by the linuxdc++ development team I posted a bug report about this on launchpad. [https://bugs.launchpad.net/ubuntu/+bug/229688](https://bugs.launchpad.net/ubuntu/+bug/229688)

I hope I'm not doing anything wrong with the debugging.

Edit: I'll try doing a debug with valgrind and get back

---

### Post by rampageoberon on 2008-06-03
Okay, I did the debug with valgrind using the guide on the wiki and I am attaching the logfile here.

Hope this is helpful.

---

