---
title: "KDE Apps Won't Launch"
date: 2007-11-12
forum: General Help
---

### Post by ksenos on 2007-11-12
Hello,

I have installed a couple of KDE applications that I prefer to the Gnome equivalents. Recently it has become impossible to run these apps on my sister's account. However, both amarok and k3b work flawlessly though my account. I deleted all the settings from her account (except for the .bash* files) but still the problem persists. Any suggestions? Thanks in advance.

---

### Post by taurus on 2007-11-12
Try running it from a terminal to see what the error message is.

Applications -> Accessories -> Terminal
```
amarok
```

---

### Post by ksenos on 2007-11-12
Well, the output of amarok is a little vague... it just hangs

```
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

```

The same output (except for the last line) comes when I execute amarok from my account, only in that case it starts normally.

---

