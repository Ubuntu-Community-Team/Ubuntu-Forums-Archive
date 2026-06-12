---
title: "After Dist Upgrade, My Custom Software Launcher Stopped Working"
date: 2018-11-09
forum: General Help
---

### Post by a.hurt on 2018-11-09
Hello All, 

I hope this is the right place to ask this question. 

I recently upgraded a machine to 17.04, and in doing so, a software launcher that I saved to the desktop that allows me to launch the software with administrator privileges no longer works. It starts firing off errors in the terminal window, all of which I do not understand.  It was a simple thing that worked really well, prompting the administrative password, then launching the software.

Here is the output I am getting now:

```
QMetaObject::connectSlotsByName: No matching signal for on_event(quint32,const void*,quint32*)QFont::setPixelSize: Pixel size <= 0 (0)
libpng warning: iCCP: known incorrect sRGB profile
X Error: BadAccess (attempt to access private resource denied) 10
  Extension:    130 (MIT-SHM)
  Minor opcode: 1 (X_ShmAttach)
  Resource id:  0x141
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e00012
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e00012
X Error: BadAccess (attempt to access private resource denied) 10
  Extension:    130 (MIT-SHM)
  Minor opcode: 1 (X_ShmAttach)
  Resource id:  0x141
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e0001a
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e0001a
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e00012
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e0001a
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e0001a
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e0001a
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e0001a
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e0001a
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e00012
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e00012
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e00012
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e00012
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e00012
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e00012
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e00012
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e00012
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e00012
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e00012
X Error: BadShmSeg (invalid shared segment parameter) 128
  Extension:    130 (MIT-SHM)
  Minor opcode: 3 (X_ShmPutImage)
  Resource id:  0x1e00012
```

Does anyone have thoughts on how I can remedy this? I would really appreciate help. Thanks.

---

### Post by QIII on 2018-11-09
Hello!

Given that 17.04 is no longer supported, it is not surprising that things are wonky.  What is surprising is that you were able to update to it.

It would not be worth your time, neither that of the community, to attempt to resolve this for an unsupported release.

Best to back up your data and do a fresh installation of one of the currently supported LTS releases:  16.04 or 18.04.  Although 14.04 is still currently supported, that ends in April so you'd be right back to an unsupported release.

---

