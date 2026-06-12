---
title: "doom 3 segfaults when trying to init opengl"
date: 2007-07-25
forum: General Help
---

### Post by Bitch-Face Jones on 2007-07-25
I'm running Ubuntu 7.04 (Athalon 64 version) with a GeForce 8500 GT.  The binary nvidia driver included with Ubuntu was older than the pope and didn't support my card, so I had to use the latest binary driver from nVidia.  I've installed it successfully, and everything works great, (I get 'Direct Rendering: Yes' from glxinfo, OpenGL screensavers work, and desktop effects work fine) however, when I try to run Doom 3, it immediately segfaults when trying to open libGL.so.1:

```
cds@futaba:~$ doom3
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth1 - 192.168.0.184/255.255.255.0
found interface eth0:avahi - 169.254.5.109/255.255.0.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/cds/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Segmentation fault (core dumped)
```

Does anyone know what gives?  I've tried running Doom 3 by setting the GL driver to use /usr/lib32/libGL.so.1 but that doesn't work either.  I've successfully ran Doom 3 before under different versions of Ubuntu with the binary nvidia drivers provided with the distribution and it's worked fine, this is the first time I've ran into problems.

---

### Post by Bitch-Face Jones on 2007-07-25
Nevermind, I fixed it.  It worked fine after I re-installed nVidia's binary drivers and OpenGL files.  I'm thinking that I forgot to install the ia32-libs before I installed nVidia's 32-bit OpenGL compatibility libraries.

---

