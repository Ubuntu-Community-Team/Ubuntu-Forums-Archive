---
title: "I broke Firefox, segmentaion fault and core dump"
date: 2007-03-05
forum: General Help
---

### Post by threethirty on 2007-03-05
I recently updated FireFox, and now it wont run.  Here is the terminal output...

```
three@Raptor:~$ firefox
/usr/lib/firefox/firefox-bin: /home/three/mono-1.2.3.1/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
kde-config: /home/three/mono-1.2.3.1/lib/libpng12.so.0: no version information available (required by /usr/lib/libqt-mt.so.3)
kde-config: /home/three/mono-1.2.3.1/lib/libpng12.so.0: no version information available (required by /usr/lib/libqt-mt.so.3)
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
                 AllPeers initiated successfully
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
Segmentation fault (core dumped)
three@Raptor:~$ 

```

it also tries to restore the last session (that's when it crashes) 

any ideas

---

