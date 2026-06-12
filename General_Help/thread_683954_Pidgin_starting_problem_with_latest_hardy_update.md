---
title: "Pidgin starting problem with latest hardy update"
date: 2008-01-31
forum: General Help
---

### Post by phin on 2008-01-31
Hey.  I've been using hardy for the last month or two now without any major issues.

But for some reason after i did an upgrade last night, i started to have an issue with running pidgin.

what i get is a Trace/breakpoint trap error and it just crashes.

so i went and installed the dbg package of pidgin and went ahead and ran it with pidgin.  here is the out put and i'll input comments on what happens to the program as it goes along.

(gdb) start
Breakpoint 1 at 0x80bb667: file ../../pidgin/gtkmain.c, line 462.
Starting program: /usr/bin/pidgin 
[Thread debugging using libthread_db enabled]
[New Thread 0xb6fce6c0 (LWP 6183)]
[Switching to Thread 0xb6fce6c0 (LWP 6183)]
main (argc=-1221623120, argv=0xb72f8558) at ../../pidgin/gtkmain.c:462
462	../../pidgin/gtkmain.c: No such file or directory.
	in ../../pidgin/gtkmain.c

## at this point, nothing is happening

(gdb) continue
Continuing.
[New Thread 0xb5e9bb90 (LWP 6186)]

Program received signal SIGTRAP, Trace/breakpoint trap.
0xb7792fcc in g_logv () from /usr/lib/libglib-2.0.so.0
(gdb) continue
Continuing.

## at this point, i get my buddy list to show.  interesting, i couldn't get this far with a normal load........ but im having issues with connecting to a couple of accounts.

Program received signal SIGTRAP, Trace/breakpoint trap.
0xb7792fcc in g_logv () from /usr/lib/libglib-2.0.so.0
(gdb) continue
Continuing.

## at this point, a couple of my accounts load up and all seems well.

Program received signal SIGTRAP, Trace/breakpoint trap.
0xb7792fcc in g_logv () from /usr/lib/libglib-2.0.so.0
(gdb) continue
Continuing.

## at this point, someone has sent me a msg but i had to manually continue again.



I'm not sure what this all means, im by no means a technical guy when it comes to software support.  any pointers to try would be great.

please note that at this time, i have not found any issues with any other programs.  any help would be great :)

---

### Post by FrankQuist on 2008-01-31
See [http://ubuntuforums.org/showthread.php?t=639641](http://ubuntuforums.org/showthread.php?t=639641). Hope that helps.

That's probably also the best forum to ask about things in Hardy!

---

### Post by phin on 2008-01-31
[http://ubuntuforums.org/showthread.php?t=639641](http://ubuntuforums.org/showthread.php?t=639641)

ok, seems this issue is already addressed.  the unset G_DEBUG thing seems to work

---

