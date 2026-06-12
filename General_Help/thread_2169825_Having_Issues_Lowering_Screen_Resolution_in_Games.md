---
title: "Having Issues Lowering Screen Resolution in Games"
date: 2013-08-23
forum: General Help
---

### Post by VicariousToast on 2013-08-23
I'm still pretty new to Linux, so please bear with me.

So my problem is that when I change the screen resolution in a game to something other than my laptop's native resolution, the screen gets messed up. The game is visible and works fine, but it's confined to a square in the top left corner of the screen (It's almost like a borderless window). The remainder of the screen is an extremely stretched image of the game (or part of it). I can't really see anything from the game in that part of the screen, it's all lines.

So the games function properly, but it's just annoying that my computer can't seem to stretch the image properly. This only seems to happen when I play games.

Here are my specs(most of it is probably unnecessary, but I didn't know what was useful information and what wasn't.): 

Toshiba Satellite M45-S331

-Computer-
Processor        : Intel(R) Pentium(R) M processor 1.60GHz
Memory        : 499MB (216MB used)
Operating System        : Ubuntu 13.04
-Display-
Resolution        : 1280x800 pixels
OpenGL Renderer        : Mesa DRI Intel(R) 915GM x86/MMX/SSE2
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : ICH4 - Intel ICH6
-SCSI Disks-
ATA IC25N080ATMR04-0
MATSHITA DVD-RAM UJ-830S

-Display-
Resolution        : 1280x800 pixels
Vendor        : The X.Org Foundation
Version        : 1.13.3
-Monitors-
Monitor 0        : 1280x800 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor        : Intel Open Source Technology Center
Renderer        : Mesa DRI Intel(R) 915GM x86/MMX/SSE2
Version        : 1.4 Mesa 9.1.3
Direct Rendering        : Yes

-Processor-
Name        : Intel(R) Pentium(R) M processor 1.60GHz
Family, model, stepping        : 6, 13, 8 (Pentium III/Pentium III Xeon/Celeron)
Vendor        : Intel
-Configuration-
Cache Size        : 2048kb
Frequency        : 800.00MHz
BogoMIPS        : 1596.00
Byte Order        : Little Endian
-Features-
FDIV Bug        : no
HLT Bug        : no
F00F Bug        : no
Coma Bug        : no
Has FPU        : yes
-Cache-
Cache information not available
-Capabilities-
fpu        : Floating Point Unit
vme        : Virtual 86 Mode Extension
de        : Debug Extensions - I/O breakpoints
pse        : Page Size Extensions (4MB pages)
tsc        : Time Stamp Counter and RDTSC instruction
msr        : Model Specific Registers
pae        : Physical Address Extensions
mce        : Machine Check Architeture
cx8        : CMPXCHG8 instruction
sep        : Fast System Call (SYSENTER/SYSEXIT)
mtrr        : Memory Type Range Registers
pge        : Page Global Enable
mca        : Machine Check Architecture
cmov        : Conditional Move instruction
clflush        : Cache Line Flush instruction
dts        : Debug Store
acpi        : Thermal Monitor and Software Controlled Clock
mmx        : MMX technology
fxsr        : FXSAVE and FXRSTOR instructions
sse        : SSE instructions
sse2        : SSE2 (WNI) instructions
ss        : Self Snoop
tm        : Thermal Monitor
pbe        : Pending Break Enable
nx        : No-execute Page Protection
bts        : Branch Trace Store
est        : Enhanced SpeedStep
tm2        : Thermal Monitor 2

Any help is greatly appreciated.

---

### Post by rai_shu2 on 2013-08-25
If you can get the games to run in windows, that will help quite a bit. Then, to fix various issues, you could resort to using xrandr for scaling or whatever:

```
xrandr -s 1024x640
xrandr --output DFP1 --scale 1x0.83
```

The "DFP1" is just the name of my current monitor. To get this info from your system, try:

```
xrandr --current
```

---

