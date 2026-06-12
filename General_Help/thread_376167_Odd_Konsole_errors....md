---
title: "Odd Konsole errors..."
date: 2007-03-04
forum: General Help
---

### Post by Lateralus@desktop on 2007-03-04
Just now, when I went into Konsole and tried to command line my way to a folder via Konqueror, it threw back a load of errors. I've got no idea what any of it means, so I thought I'd come back here and see if I can get an insight. 

I typed in 'sudo konqueror /home/Lateralus/Desktop/', and this is what came up:

Password:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DCOPClient::attachInternal. Attach failed Could not open network socket
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-4995' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
konqueror: WARNING: Profile Loading Error: No orientation specified in Container  

Konqueror did open after that, but I just found these errors odd...

---

### Post by caldevil on 2007-03-04
First two errors "X errors" are just because you have some extra things in xorg.conf for tablet pc. Its nothing serious. Last error or warning is because you are tring to run konqueror as root.

Overall nothing to worry about.

---

