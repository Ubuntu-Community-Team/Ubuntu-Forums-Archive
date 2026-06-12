---
title: "Sound crackling /Buzzing Problems [Ubuntu 7.04]"
date: 2007-09-19
forum: General Help
---

### Post by wmcode on 2007-09-19
i have so many (2 years)  time with this problem:

when changing the volume, scrolling text, moving windows, and on various other actions performed in X,
I get a buzzing sound in the right audio channel.

[ when the GLX extension is enabled I get this annoying problem. ]

my info:
> -General-

Kernel		              : Linux 2.6.20-16-generic (i686)
Compiled		  : #2 SMP Fri Aug 31 00:55:27 UTC 2007
Processor		   : Intel(R) Pentium(R) 4 CPU 2.26GHz
Memory		            : 775MB (263MB used)
Operating System    : Ubuntu 7.04


-Display-
Resolution		: 1280x1024 pixels
OpenGL Renderer	    : GeForce FX 5200/AGP/SSE2
Vendor		: The X.Org Foundation
Version		: 7.2.0
-Monitors-
Monitor 0		: 1280x1024 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
Extended-Visual-Information
GLX
MIT-SCREEN-SAVER
MIT-SHM
MIT-SUNDRY-NONSTANDARD
NV-CONTROL
NV-GLX
RANDR
RECORD
RENDER
SECURITY
SHAPE
SYNC
TOG-CUP
X-Resource
XAccessControlExtension
XC-APPGROUP
XC-MISC
XFIXES
XFree86-Bigfont
XFree86-DGA
XFree86-Misc
XFree86-VidModeExtension
XInputExtension
XKEYBOARD
XTEST
XVideo
XVideo-MotionCompensation
-OpenGL-
Vendor		: NVIDIA Corporation
Renderer		: GeForce FX 5200/AGP/SSE2
Version		: 2.1.1 NVIDIA 100.14.11
Direct Rendering		: Yes

-Multimedia-

Audio Adapter		: SAA7134 - SAA7134
Audio Adapter		: VIA8237 - VIA 8237

-Input Devices-
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 PC Speaker
 Pinnacle PCTV
 ImPS/2 Generic Wheel Mouse
 Power Button (FF)
 Power Button (CM)

-Printers (CUPS)-
Stylus-CX3805

-IDE Disks-
SONY CD-RW CRX230EE

-SCSI Disks-
ATA HDS728080PLA380

Things what i already try:

> with:
[QUOTE]$ alsamixer
PUT ALL THE SOUND MIXER VALUES UNDER 80[/QUOTE]

> 
replace, reinstall & purge sound packages:
libsdl* , alsa, oss, etc. 

> [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_configure_sound_to_work_properly_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_configure_sound_to_work_properly_in_GNOME)
plus logic change of the files:
/etc/modules.conf
/home/x/.asoundrc /etc/asound.conf /home/ncode/.asoundrc.asoundconf
/etc/esound/esd.conf
/var/lib/alsa/asound.state
/home/x/.openalrc


> 
manual compile & package [.sh]  of the nvidia driver
[various versions, since 7185 version and up  to 100.14.11 ]


> removing the tv tunner [pinnacle pctv pro pci]

> replace the nvidia driver the the default mesa [original driver]
: IT WORKS !!!! [but i don't have 3d accel. and direct rend... blablabla]

here is a video of the bad quality sound in action:

[http://video.google.es/videoplay?docid=-8926491434163462902](http://video.google.es/videoplay?docid=-8926491434163462902)

please help me !
:-(

---

