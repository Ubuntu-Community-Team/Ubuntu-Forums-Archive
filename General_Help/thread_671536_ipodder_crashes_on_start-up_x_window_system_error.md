---
title: "ipodder crashes on start-up: x window system error"
date: 2008-01-18
forum: General Help
---

### Post by andrej_ on 2008-01-18
I've been running ipodder for months now without problems, but since about two days ago I can't open it anymore: it crashes on start-up and produces the following error message:

~$ [<class 'ipodder.players.XMMSPlayer'>, <class 'ipodder.players.NoPlayer'>]
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
The program 'python' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2145 error_code 11 request_code 144 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


What can I do? Are there any alternatives to ipodder?

---

