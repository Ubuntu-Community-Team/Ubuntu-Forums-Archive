---
title: "Opera issue"
date: 2007-07-01
forum: General Help
---

### Post by Prey on 2007-07-01
I have been trying to get opera up and runnign on my systema nd well i have never had this issue in the past.  After i get it installed and click on the icon nothing hppens, so when i try to get it started in the konsole i get this:

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault


I have read the wiki on how to get it working when you get that error, but well I can't get opera to start to begin with,  any one have any ideas

---

### Post by kidders on 2007-07-02
Hi there,

You seem to be running into lots of problems, all at the same time...

[SIZE=1][COLOR=DimGray] ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
[/COLOR][/SIZE]
These are probably caused by java-related system libraries that are missing or corrupt.

[SIZE=1][COLOR=DimGray]X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/COLOR]
[/SIZE]
There may be misconfigured or non-existent input devices referenced in your xorg.conf.

[SIZE=1][COLOR=DimGray]Segmentation fault
[/COLOR][/SIZE] 
This is the only fatal error, but it could be caused by a wide variety of things. You've probably mis-installed Opera.

Could you post a little detail about your system, what you've done to it, and how you installed Opera?

---

### Post by Colonel Kilkenny on 2007-07-05
I'd guess you have Opera 9.10 installed. Download newest Opera (9.21) from opera.com

---

