---
title: "Segmentation fault in gnome-keybinding-properties"
date: 2007-09-10
forum: General Help
---

### Post by Neatchee on 2007-09-10
Hi all.  I went to check on some keyboard shortcuts today and found that the keybinding properties control panel wouldn't open.  Upon trying to load it from a terminal, I found I was getting a segmentation fault!  What follows is all the relevant information I could think of to provide:

Version of Ubuntu: Ubuntu 7.04 Feisty Fawn
Architecture: AMD64
Other active software possibly conflicting?:  xbindkeys, xfwm4 (replacing metacity)

I found that booting into recovery mode, moving away my entire home directory, and restarting (producing a virtually fresh gnome environment) solved the problem, however closing out gdm, moving away the following directories, and reloading gdm for the following directories did not produce positive results:  ${HOME}/[.gnome, .gnome2, .gnome2_private, .config, .fonts, .themes, .gconf, .gconfd]

I managed to track down the debug packages for gnome-control-panel.  The following is the result of a backtrace, as instructed by the Ubuntu wiki entry for backtracing, and an strace stderr output:

====================================================
-----------------------------BACKTRACE---------------------------------
====================================================
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...
Using host libthread_db library "/lib/libthread_db.so.1".
(gdb) handle SIG33 pass noprint nostop
Signal        Stop	Print	Pass to program	Description
SIG33         No	No	Yes		Real-time event 33
(gdb) set pagination 0
(gdb) run
Starting program: /usr/bin/gnome-keybinding-properties 
[Thread debugging using libthread_db enabled]
[New Thread 47951608263936 (LWP 19401)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 47951608263936 (LWP 19401)]
0x00002b9c933b8239 in free () from /lib/libc.so.6
(gdb) backtrace full
#0  0x00002b9c933b8239 in free () from /lib/libc.so.6
No symbol table info available.
#1  0x0000000000406bd2 in main (argc=1, argv=0x7fff19920ed8) at gnome-keybinding-properties.c:972
	program = (GnomeProgram *) 0x648040
	dialog = (GladeXML *) 0x64c300
(gdb) info registers
rax            0x4b434548435f4d	21184588097478477
rbx            0x2b9c93691960	47951488031072
rcx            0x0	0
rdx            0x40b781	4241281
rsi            0x40b782	4241282
rdi            0x40b781	4241281
rbp            0x648040	0x648040
rsp            0x7fff19920d60	0x7fff19920d60
r8             0x8331c0	8597952
r9             0x1	1
r10            0xd	13
r11            0x2b9c933b81e0	47951485043168
r12            0x64c300	6603520
r13            0x6ea080	7250048
r14            0x68cdd0	6868432
r15            0x6450c0	6574272
rip            0x2b9c933b8239	0x2b9c933b8239 <free+89>
eflags         0x10246	[ PF ZF IF RF ]
cs             0x33	51
ss             0x2b	43
ds             0x0	0
es             0x0	0
fs             0x0	0
gs             0x0	0
fctrl          0x37f	895
fstat          0x0	0
ftag           0xffff	65535
fiseg          0x0	0
fioff          0x0	0
foseg          0x0	0
fooff          0x0	0
fop            0x0	0
mxcsr          0x1fa0	[ PE IM DM ZM OM UM PM ]
(gdb) thread apply all backtrace

Thread 1 (Thread 47951608263936 (LWP 19401)):
#0  0x00002b9c933b8239 in free () from /lib/libc.so.6
#1  0x0000000000406bd2 in main (argc=1, argv=0x7fff19920ed8) at gnome-keybinding-properties.c:972
(gdb) quit
The program is running.  Exit anyway? (y or n) 

====================================================
--------------------------END BACKTRACE------------------------------
====================================================

strace: [http://paste.ubuntu-nl.org/37066/](http://paste.ubuntu-nl.org/37066/)

Thanks in advance for any help you can offer!

---

