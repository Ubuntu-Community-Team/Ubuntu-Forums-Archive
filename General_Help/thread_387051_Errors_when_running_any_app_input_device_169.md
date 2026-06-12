---
title: "Errors when running any app? input device 169?"
date: 2007-03-17
forum: General Help
---

### Post by strabes on 2007-03-17
I get errors when I run applications in the terminal. Here are some examples:

> alex@alex-laptop:~$ sudo kedit /etc/X11/xorg.conf
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
No protocol specified
kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
No protocol specified
kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-9134' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.

> alex@alex-laptop:~$ kdesu kedit /etc/X11/xorg.conf
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

> alex@alex-laptop:~$ kdesu firefox
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by ewankho on 2007-03-18
Try to search the forums. This has been answered many times before.

---

