---
title: "Oh no, Beryl !"
date: 2007-05-30
forum: General Help
---

### Post by sdil on 2007-05-30
Last month, I install Ubuntu Feisty 7.04 in my other partition. I just now install beryl. when I open beryl using terminal, it say : Segment fault ( core dumped )

Any idea or suggestions ?

---

### Post by sdil on 2007-05-30
This is the output :

wow@ubuntu:~$ beryl
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

[Warning ]: Relaunching beryl with __GL_YIELD="NOTHING"

**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Segmentation fault (core dumped)

---

### Post by MACRI on 2007-06-01
EXACT SAME PROBLEM RIGHT HERE, EVER SINCE I INSTALLED KIBA-DOCK!!!
what is the fix for said things?

---

### Post by AlexenderReez on 2007-06-01
this is mine and my beryl working great----->> 
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

[Warning ]: Relaunching beryl with __GL_YIELD="NOTHING"

**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
[FireFly]: Loaded Texture /usr/share/beryl//firefly1.png
[FireFly]: Loaded Texture /usr/share/beryl//firefly1.png
[FireFly]: Loaded Texture /usr/share/beryl//firefly1.png
[Star]: Loaded Texture /usr/share/beryl/star1.png
[Star]: Loaded Texture /usr/share/beryl/star1.png
[Star]: Loaded Texture /usr/share/beryl/star1.png
Initiating splash


this is my howto in ubuntu doc ----->

> [http://doc.gwos.org/index.php/HowToInstallBeryl](http://doc.gwos.org/index.php/HowToInstallBeryl)

---

### Post by gp2x on 2007-06-05
I have this problem now, any clues anyone?

---

### Post by gp2x on 2007-06-06
OK, here's where I got to :

An strace of beryl revealed (in part)

```

gettimeofday({1181127814, 931764}, NULL) = 0
poll([{fd=10, events=POLLIN, revents=POLLIN}], 1, 25000) = 1
read(10, "l\4\1\1\32\0\0\0\3\0\0\0\215\0\0\0\1\1o\0\25\0\0\0/org"..., 2048) = 270
read(10, 0x8250af8, 2048)               = -1 EAGAIN (Resource temporarily unavailable)
open("icon.png", O_RDONLY)              = -1 ENOENT (No such file or directory)
open("/home/simon/.beryl/images/icon.png", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/beryl/icon.png", O_RDONLY) = 11
fstat64(11, {st_mode=S_IFREG|0644, st_size=480, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb42e0000
read(11, "\211PNG\r\n\32\n\0\0\0\rIHDR\0\0\0000\0\0\0000\10\6\0\0"..., 4096) = 480
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
Process 5897 detached

```

It appears to core dump when trying to handle the png icon. I then jumped into beryl-settings and switched off the png handling, and voila! Beryl starts without issue.

Ofcourse, I cant use PNG files :) But I guess the problem is somewhere in libpng? Just guessing.

EDIT: nah, dumb guess :) Its segfaulting reading the logo png into a buffer?!?!?! How the hell can that be wrong?

EDIT2: I renamed the icon file and straced beryl again:

```

read(4, "\1\1\\\v\0\0\0\0\3\0\0\4\0\0\0\0\0\0\0\0\30a\357\277\250"..., 32) = 32
write(4, "!\1\4\0\206\1\0\0\36\0i\1\1\0\0\0+\0\1\0", 20) = 20
read(4, "\1\1^\v\0\0\0\0\3\0\0\4\0\0\0\0\0\0\0\0\30a\357\277\250"..., 32) = 32
open("/usr/share/beryl/cubecaps.png.svg", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/beryl/cubecaps.png", O_RDONLY) = 11
fstat64(11, {st_mode=S_IFREG|0644, st_size=505251, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb4335000
read(11, "\211PNG\r\n\32\n\0\0\0\rIHDR\0\0\6@\0\0\4\260\10\6\0\0"..., 4096) = 4096
brk(0x8293000)                          = 0x8293000
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
Process 12869 detached

```

same thing, different png.... coincidence?

---

