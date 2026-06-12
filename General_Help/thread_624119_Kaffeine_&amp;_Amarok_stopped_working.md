---
title: "Kaffeine &amp; Amarok stopped working"
date: 2007-11-26
forum: General Help
---

### Post by daiwai on 2007-11-26
Since yesterday I got problems with both Kaffeine and Amarok.

I still can start Kaffeine, but as soon as I try to play a movie, it crashes with this backtrace:
```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
...
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1239640384 (LWP 11070)]
(no debugging symbols found)
...
(no debugging symbols found)
[KCrash handler]
#6  0xb5a126fc in ?? () from /usr/lib/libxine.so.1
#7  0x00000008 in ?? ()
#8  0x00000001 in ?? ()
#9  0xb5a3e128 in ?? () from /usr/lib/libxine.so.1
#10 0x085a8368 in ?? ()
#11 0x00000002 in ?? ()
#12 0xbfc42194 in ?? ()
#13 0xb65f1de8 in ?? () from /lib/tls/i686/cmov/libdl.so.2
#14 0xb7f2fff4 in ?? () from /lib/ld-linux.so.2
#15 0x00000000 in ?? ()

```

Amarok just doesn't start. When trying to start it from the command line it gives this output:

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8145c18 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8145c18 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
```

The strange thing is, that It was working fine before and I did not change anything in either Kaffeine or Amarok.

---

### Post by daiwai on 2007-11-27
Any ideas what might be the problem? :confused:

---

### Post by byorgey on 2007-11-28
I'm having the exact same problem with amarok.  I have a fully updated Ubuntu 7.10 on an i686.  I'm using xmonad, a tiling WM, and I initially suspected it might have to do with that, but other xmonad users have reported being able to use amarok just fine.  

I'd be happy to provide any additional information.

```

[08:38:20 brent@xenophon:~]$ amarok &
[1] 17128
[08:40:03 brent@xenophon:~]$ X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

```

---

### Post by daiwai on 2007-11-29
OK, I could solve my problem. It seems the problem was a broken catalog.cache file in ~/.xine I just renamed it and xine created a new one the next time I started Amarok.

Now I think this is probablya bug in xine. Surely it should discover the catalog.cache is corrupt and just create a new one instead of crashing, no?

@ byorgey

Actually the end of your Amarok output looks slightly different and thus Amarok not starting up might have a different cause. However, as I mentioned above,  it is probably pretty safe to just delete or rename the catalog.cache file in ~/.xine as it is recreated automatically by xine. So you might as well give it a try, see if it solves your problem as well.

---

### Post by byorgey on 2007-11-29
Hm, it seems that isn't my problem, I don't even have an .xine directory.  And creating one didn't help. Thanks for sharing your solution though.

---

