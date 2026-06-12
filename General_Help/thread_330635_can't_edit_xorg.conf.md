---
title: "can't edit xorg.conf"
date: 2007-01-03
forum: General Help
---

### Post by Ksmith3637 on 2007-01-03
i am running kubuntu and needed to edit the xorg.conf for double buffering. says i do not have premission.. so tried sudo gedit and kate but always comes up with error..also tried gksudo with errors..
any ideas??
thanks ksmith3637  ](*,) 

dell@dell-laptop:~$ sudo kate /etc/x11/xorg.conf
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
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
QObject::disconnect: Unexpected null parameter

or
gksudo kate /etc/x11/xorg.conf
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
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by _simon_ on 2007-01-03
It's case sensitive. 

It's X11 not x11

---

### Post by meng on 2007-01-03
Also better off using kdesu rather than sudo
kdesu kate ...

---

