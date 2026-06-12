---
title: "Amarok startup issues"
date: 2007-04-29
forum: General Help
---

### Post by AlexDe on 2007-04-29
For some reason Amarok refuses to start up.. I checked the command line and it dies on the following error:

```

shm.c: shm_open() failed: Read-only file system

```

The error seems pretty self explanatory.. but I can't find much reference to it / why it randomly happened (I didn't change anything in fstab / mount anything aside from ripping a few CD's)

Any help would be appreciated, thanks :)

****EDIT****

Some reason in the fstab it was mounting as read-only (duh!)

To fix I changed:

```

tmpfs     /dev/shm     tmpfs     defaults,ro     0 0

```

to the following:

```

tmpfs     /dev/shm     tmpfs     defaults,rw     0 0

```

Still not sure why it got changed, but all is well :)

---

### Post by mordak13 on 2007-04-29
I have startup failure with Amarok now since my Feisty upgrade. when trying to start from the command line I get this:

```
mordak@kubuntu:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

I'm not sure what the input device 167 is. Any ideas?

---

