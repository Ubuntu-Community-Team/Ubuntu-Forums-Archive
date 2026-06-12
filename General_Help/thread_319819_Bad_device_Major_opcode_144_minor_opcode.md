---
title: "Bad device: Major opcode 144 minor opcode"
date: 2006-12-16
forum: General Help
---

### Post by mirons on 2006-12-16
Hi everybody. I noticed many people had this kind of trouble (which is not a trouble maybe, but I'd like to understand). launching an app from shell I get this error:
```


X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```


this happens with everything from gimp to amarok. But then the program just work fine. While when I launch flock web browser the same error is followed by the lines:

```

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 143 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

and the program crashes. This has happened also with firefox once. Is there a X.org misconfiguration?

---

### Post by petrockthief on 2006-12-17
I've also had this problem. No one seems to have a solution. Perhaps it is something from a new update?

---

### Post by dcw112 on 2007-01-06
Does your xorg.conf file have wacom devices in it? In post 7 of [This thread]("http://ubuntuforums.org/showthread.php?t=288406&highlight=X+Error%3A+Bad+Device") they removed wacom device entries in their xorg.conf file. I'm going to try tonight and see what happens

---

### Post by mirons on 2007-01-07
I'm running Edgy, kernel is 2.6.17-generic (I used a cd for i386 platform while I have an intel centrino duo... ....btw which is the best kernel for this platform?). Without wacom device X seems not to work (I haven't really restarted it, just tried to startup a new session from k menu...)

---

### Post by dcw112 on 2007-01-07
Under Section "ServerLayout" in your Xorg.conf file did you comment out the stylus, cursor and eraser? Is it a 32bit or 64 bit processor?

---

### Post by tucurious on 2007-04-21
I'm having this same bad device problem when trying to open opera.
It looks like it started right after an auto update of 4 unknown files.
Opera won't open from pull down list but I hear the hard drive trying.
Terminal then gives me the bad device stuff.
Does anyone know if I can just remove Opera and then install to get
around this?
art

---

### Post by Colonel Kilkenny on 2007-04-22
Errors regarding Bad Devices should not cause Opera to crash. And your problem is somewhere else.

Upgrade your Opera to the newest version (9.20, [http://opera.com](http://opera.com)) and your problem is fixed. The segmentation fault (I guess your getting this error also although you didn't mention it) is caused by recent upgrade to X libraries and has nothing to do with error messages talked in this thread.

---

