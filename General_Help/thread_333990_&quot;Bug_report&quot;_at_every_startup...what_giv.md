---
title: "&quot;Bug report&quot; at every startup...what gives?"
date: 2007-01-08
forum: General Help
---

### Post by lucas9000 on 2007-01-08
First, the basics: I'm running Xubuntu, Edgy Eft 6.10, on an AMD64 machine.  I originally installed Ubuntu, but then installed Xubuntu as an additional desktop environment and really like it, so I've stuck with it.

Second, the problem: since I started using Xubuntu, I get a bug reporting tool message after every boot up.  I don't know how to interpret it, much less how to fix whatever is wrong.  I'd appreciate any help.  Here is the message I got most recently:

Memory status: size: 139247616 vsize: 139247616 resident: 11571200 share: 9207808 rss: 11571200 rss_rlim: -1
CPU usage: start_time: 1168239952 rtime: 22 utime: 16 stime: 6 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 100

Backtrace was generated from '/usr/libexec/evolution-alarm-notify'

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 47395412378432 (LWP 4862)]
[New Thread 1074006352 (LWP 4881)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0x00002b1b1624b5cf in waitpid () from /lib/libc.so.6
#0  0x00002b1b1624b5cf in waitpid () from /lib/libc.so.6
#1  0x00002b1b133dfa07 in gnome_gtk_module_info_get ()
   from /usr/lib64/libgnomeui-2.so.0
#2  0x00002b1b161e7510 in killpg () from /lib/libc.so.6
#3  0x0000000000000000 in ?? ()

Thread 2 (Thread 1074006352 (LWP 4881)):
#0  0x00002b1b1627b7f6 in poll () from /lib/libc.so.6
No symbol table info available.
#1  0x00002b1b15a9e91e in g_main_context_check ()
   from /usr/lib64/libglib-2.0.so.0
No symbol table info available.
#2  0x00002b1b15a9edda in g_main_loop_run () from /usr/lib64/libglib-2.0.so.0
No symbol table info available.
#3  0x00002b1b147d4fb0 in link_set_io_thread ()
   from /usr/lib64/libORBit-2.so.0
No symbol table info available.
#4  0x00002b1b15ab7c04 in g_thread_create_full ()
   from /usr/lib64/libglib-2.0.so.0
No symbol table info available.
#5  0x00002b1b170f13ca in start_thread () from /lib/libpthread.so.0
No symbol table info available.
#6  0x00002b1b1628455d in clone () from /lib/libc.so.6
No symbol table info available.
#7  0x0000000000000000 in ?? ()
No symbol table info available.

Thread 1 (Thread 47395412378432 (LWP 4862)):
#0  0x00002b1b1624b5cf in waitpid () from /lib/libc.so.6
No symbol table info available.
#1  0x00002b1b133dfa07 in gnome_gtk_module_info_get ()
   from /usr/lib64/libgnomeui-2.so.0
No symbol table info available.
#2  0x00002b1b161e7510 in killpg () from /lib/libc.so.6
No symbol table info available.
#3  0x0000000000000000 in ?? ()
No symbol table info available.
#0  0x00002b1b1624b5cf in waitpid () from /lib/libc.so.6

---

### Post by tokj on 2007-01-08
Seems to be a bug that affect a lot of users. The problem has been already reported on Launchpad.

The strange thing is that the crash occured only on Feisty Fawn. This is the first time that i read about this problem also on Edgy.

Was evolution recently upgraded on Edgy? Did you noticed something?

---

### Post by lucas9000 on 2007-01-09
This has happened ever since I switched to Xubuntu, which was a couple weeks ago.

---

### Post by tokj on 2007-01-09
I had other confirmes about this bug on Xubuntu Edgy. If you don't use evolution you can uninstall it or remove evolution-alarm-notify from startup applications list.

---

### Post by argotnaut on 2007-01-17
I'm getting this on regular (no X) Ubuntu Edgy, too. And I *do* use Evolution, so I can't get rid of this. :(

---

### Post by commonplace on 2007-01-19
Still no fix for this? It's been happening to me for a long time now (on Edgy), and as an Evolution user, I don't want to just turn it off.

/Kevin

---

### Post by Hubris2 on 2007-01-22
I'm getting this message only when I sign into a virtual term via Vnc4Server - I don't even get it when I connect to session 0 via vino.

---

### Post by ggbuntu on 2007-11-29
I also got the same error after switched to Xubuntu.
This problem is related to $HOME/.cache directory.
But when I try to remove it, the directory is always 
recreated again when log out from GUI.

So I try like this:
1. Log out from the GUI.
2. Switch to Text mode ( e.g. CTRL-ALT-F1 )
3. Rename/move the .cache, for example to $HOME/tmp/.cache
4. Switch to GUI mode ( e.g. ALT-F7 ) 
5. Log in to the GUI.

Creating a new user and use the new user name 
also 'solved' the problem.

---

