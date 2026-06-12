---
title: "Multiple (Virtual?) X Displays"
date: 2006-08-07
forum: General Help
---

### Post by compwiz18 on 2006-08-07
First off: I don't know the terminology for this so hang with me here.

I know that when you press control-alt-f1, a Linux console pops up and I can run commands.  Is there a way I can start an X display in this with Gnome and stuff?  I want to run Enemy Territory in there because I can't minimize it, so in order to use other programs I have to exit and then load it again...it gets annoying.

Anyone? Thanks in advance.

---

### Post by skale on 2006-08-07
I've wanted to do that too, sort of like the "fast user switching" capability in Windows XP. I know that in /etc/inittab only tty7 is reserved for X.

---

### Post by steve.horsley on 2006-08-07
Use Alt-Ctrl-F1 to drop to a TTY console, log in and then use the command:
> startx -- :1
which starts a new X session on Alt-Ctrl-F8. You can still Alt-Ctrl-F7 back to the original GUI. You can of course start another one on F9 with startx -- :2. 

But the catch is...
The game is likely to capture the keystrokes and prevent you switching until the game exits. Still, you can always try it.

---

### Post by compwiz18 on 2006-08-07
> **steve.horsley said:**
> Use Alt-Ctrl-F1 to drop to a TTY console, log in and then use the command:

which starts a new X session on Alt-Ctrl-F8. You can still Alt-Ctrl-F7 back to the original GUI. You can of course start another one on F9 with startx -- :2. 

But the catch is...
The game is likely to capture the keystrokes and prevent you switching until the game exits. Still, you can always try it.
IT WORKS :D if I run it as root...which gives me that feeling of insecurity that no one likes.  Any idea how to run it as me so that I don't have to be root? (I can post output and stuff if need be and if you give me a command to capture it with)

Thanks in advance.

---

### Post by hopstah on 2006-08-07
give yourself permissions to the directory where the game is installed, or if it was installed in your games directory, add yourself to the games group.

---

### Post by compwiz18 on 2006-08-07
> **hopstah said:**
> give yourself permissions to the directory where the game is installed, or if it was installed in your games directory, add yourself to the games group.
Sorry if I wasn't clear.  The game works great, but I can only **startx** as root...which automagically logs me into the root gnome desktop which is bad, I believe.

---

### Post by trent dillman on 2006-08-07
...

---

### Post by compwiz18 on 2006-08-07
> **trent dillman said:**
> You could try running 2 instances of GDM, with ET as a session....
How would I go about doing that?

---

### Post by hanzomon4 on 2006-08-07
> **compwiz18 said:**
> How would I go about doing that?

Yeah I wanna know to

---

### Post by steve.horsley on 2006-08-08
> **compwiz18 said:**
> Sorry if I wasn't clear.  The game works great, but I can only **startx** as root...which automagically logs me into the root gnome desktop which is bad, I believe.

I've never seen that before. What error do you get runing **startx -- :1** as a normal user?

---

### Post by compwiz18 on 2006-08-08
> **steve.horsley said:**
> I've never seen that before. What error do you get runing **startx -- :1** as a normal user?
Well, you asked:

Log of starting X on :2
```

Log of startx -- :2 
Tue Aug  8 13:59:23 2006

xauth:  creating new authority file /home/adam/.serverauth.23602
xauth:  error in locking authority file /home/adam/.Xauthority
xauth:  error in locking authority file /home/adam/.Xauthority
xauth:  error in locking authority file /home/adam/.Xauthority
xauth:  error in locking authority file /home/adam/.Xauthority

_XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/adam:2
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux adam 2.6.15-26-k7 #1 SMP PREEMPT Thu Aug 3 03:40:32 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.2.log", Time: Tue Aug  8 13:59:23 2006
(==) Using config file: "/etc/X11/xorg.conf"
(EE) fglrx(0): Hardware already been locked. 
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
AUDIT: Tue Aug  8 13:59:28 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified




waiting for X server to begin accepting connections .
AUDIT: Tue Aug  8 13:59:30 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 13:59:32 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 13:59:34 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 13:59:36 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 13:59:38 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 13:59:40 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 13:59:42 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 13:59:44 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 13:59:46 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 13:59:48 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 13:59:50 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 13:59:52 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 13:59:54 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 13:59:56 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 13:59:58 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:00 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:02 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:04 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:06 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:08 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:10 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:12 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:14 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:16 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:18 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:20 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:22 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:24 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:26 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:28 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:30 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:32 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:34 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:36 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:38 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:40 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:42 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:44 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:46 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:48 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:50 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:52 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:54 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:56 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:00:58 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:00 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:02 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:04 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:06 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:08 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:10 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:12 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:14 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:16 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:18 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:20 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:22 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:24 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:26 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:28 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:30 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:32 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:34 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:36 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:38 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:40 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:42 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:44 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:46 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:48 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:50 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:52 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:54 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:56 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:01:58 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:00 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:02 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:04 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:06 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:08 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:10 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:12 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:14 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:16 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:18 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:20 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:22 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:24 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:26 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:28 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:30 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:32 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:34 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:36 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:39 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:41 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:43 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:45 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:47 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:49 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:51 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:53 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:55 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:57 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:02:59 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:03:01 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:03:03 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:03:05 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:03:07 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:03:09 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:03:11 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:03:13 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:03:15 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:03:17 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:03:19 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:03:21 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:03:23 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:03:25 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
AUDIT: Tue Aug  8 14:03:27 2006: 23620 X: client 1 rejected from local host
Xlib: connection to ":2.0" refused by server

Xlib: No protocol specified


..
giving up.

xinit:  unable to connect to X server



waiting for X server to shut down Synaptics DeviceOff called
...FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.



xinit:  Server error.
xauth:  error in locking authority file /home/adam/.Xauthority

Tue Aug  8 14:03:33 2006
----------------


```

I get the same thing when attempting to connect to :1 as well.

---

### Post by steve.horsley on 2006-08-09
If you ehter the command **ls -l .Xauthority** you will probably find that .Xauthority is owned by root. That's bad, and is a result of running GUI programs with **sudo**. Stop your GUI applications and delete .Xauthority with **rm .Xauthority** and try again. If you must run gui applications as root, launch them with gksudo and not sudo, and that should avoid the .Xauthority problem.

---

### Post by hanzomon4 on 2006-08-09
That worked for me thanks

---

### Post by maka on 2006-08-09
this is pretty cool.  is there any way to have a launcher to run this?

to create the second X and to run a game?

](*,)

---

### Post by compwiz18 on 2006-08-09
> **maka said:**
> this is pretty cool.  is there any way to have a launcher to run this?

to create the second X and to run a game?

](*,)
If you use special video drivers like fglrx (or the nVidia ones maybe?) then the second X display won't have video acceleration, I believe.

---

### Post by hanzomon4 on 2006-08-10
I think you're right, If I try to "switch user" and pick the xgl server it won't work but the if I pick the regular xserver it works.

---

### Post by maka on 2006-08-10
> **hanzomon4 said:**
> I think you're right, If I try to "switch user" and pick the xgl server it won't work but the if I pick the regular xserver it works.

thats why i rather not use xgl.. it works for me when i dont use it and have regular nvidia

---

### Post by hanzomon4 on 2006-08-10
It's not a problem it defaults to the regular xserver if you have xgl running.

---

