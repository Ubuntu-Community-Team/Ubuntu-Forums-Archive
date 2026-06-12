---
title: "Problems with Games"
date: 2006-10-31
forum: General Help
---

### Post by 2pacalypse on 2006-10-31
I've recently bought 3 Linux native games (Jagged Alliance 2, Doom3 , Savage The battle for Newerth) but neither one of them works, and I think that the problem is with the system rather then the game. heres the console outputs the games give me

Doom3:
```

anarch@anarch-desktop:~$ doom3
DOOM 1.1.1286 linux-x86 Nov 24 2004 17:56:04
Hostname: anarch-desktop
local IP: 127.0.1.1
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0x7dafc4d4
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x16cf3b8a
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Current search path:
/home/anarch/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg
anarch@anarch-desktop:~$

```

Savage Battle for Newerth
```

anarch@anarch-desktop:~$ /home/anarch/savage
Traceback (most recent call last):
  File "<string>", line 11, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 362, in doimport
  File "/home/slothy/cvs/src/s2update/builds2update/out1.pyz/wxPython", line 20, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 338, in doimport
  File "iu.py", line 184, in getmod
  File "archive.py", line 386, in getmod
  File "iu.py", line 46, in getmod
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory
There was an error (error 65280 - Unknown error 65280) running the updater!  bailing out
anarch@anarch-desktop:~

```

Jagged Alliance 2
```

anarch@anarch-desktop:~$ /home/anarch/ja2/ja2
Jagged Alliance 2

(c) 1999 by Sir-tech Canada Ltd. All rights reserved.
Jagged Alliance is registered trademark of 1259191 Ontario Inc.
You must mount the Jagged Alliance 2 for Linux game disk.

anarch@anarch-desktop:~$ /home/anarch/ja2/ja2
Jagged Alliance 2

(c) 1999 by Sir-tech Canada Ltd. All rights reserved.
Jagged Alliance is registered trademark of 1259191 Ontario Inc.
You must mount the Jagged Alliance 2 for Linux game disk.

anarch@anarch-desktop:~$

```
*Note* I made perfectly sure that the cd IS mounted, but the game doesn't see it for some reason

Furthermore i want to install KDE to experience the diffrent between it and Gnome but when ever i try to install it, he asks to install some dependencies and remove kdesvn-kio-plugins. but when ever i do ok, and try to install it he says

```

kde:
 Depends: kde-core but it is not going to be installed
 Depends: kde-amusements but it is not going to be installed
 Depends: kdeaddons but it is not going to be installed

```
when i try to install any one of those dependencies he leads me on a long chain on dependency will not be install, which end with the message
```

kdesktop:
  Depends: kdebase-bin (=4:3.5.2-0ubuntu26) but 4:3.5.2-0ubuntu27 is to be installed

```

Does any1 have a solution for these issues?

---

### Post by luvinit on 2007-01-15
In Jagged alliance you must mount disk 2 as the game disk, don't know whether that is the problem?

---

