---
title: "blender 4.0.2 locking up on Ubuntu 22.04.4 LTS!?"
date: 2024-03-17
forum: General Help
---

### Post by artunix on 2024-03-17
Anyone else having issues with blender 4.0.2 locking up?!
It was working fine until one day it wasn’t 
running ubuntu 22.04.4 lts. Had it on xorg, switched over to wayland to see if that would it fix, but no.
I uninstalled and reinstalled blender 4.0.2, still locks up.
When blender 4.0.2 does lock up; now all the time when I work with it; the laptop fans go into high gear. And the system monitor shows that cpu number 4(core 4) is ‘used’ 100%.
when I resize blender some of the blender windows show bad content, like a bad video signal.
I keep ubuntu up to date. MAYBE a ‘bad’ mesa update??
tried glxinfo | grep “opengl version” got this:
string: 4.6 (Compatibility Profile) Mesa 23.2.1-1ubuntu3.1~22.04.2

---

### Post by artunix on 2024-03-17
more infor from another system also having issues with blender:
from the crash file:
# Blender 4.0.2, Commit date: 2023-12-05 07:41, Hash 9be62e85b727

# backtrace
/snap/blender/4300/blender() [0xf3a7b0]
/snap/blender/4300/blender() [0x8c42ec]
/lib/x86_64-linux-gnu/libc.so.6(+0x42520) [0x73be58e42520]
/snap/blender/4300/blender() [0xf7c36d]
/snap/blender/4300/blender() [0xf7c3cd]
/snap/blender/4300/blender() [0xf484b4]
/snap/blender/4300/blender() [0xf5cf01]
/snap/blender/4300/blender() [0xf62414]
/snap/blender/4300/blender() [0x725166]
/lib/x86_64-linux-gnu/libc.so.6(+0x29d90) [0x73be58e29d90]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0x80) [0x73be58e29e40]
/snap/blender/4300/blender() [0x8c022e]

# Python backtrace

---

