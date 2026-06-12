---
title: "All browser crash in lubuntu 16.04 LTS"
date: 2016-12-24
forum: General Help
---

### Post by cyttorak on 2016-12-24
I have installed Lubuntu 16.04 LTS today in a AMD Athlon(tm) XP 1800+ and I could not boot any browser, they all failed to boot.

I have tried with Firefox, Chromium and Midori and everyone have failed.

```
$ chromium-browser 
Instrucción ilegal (`core' generado)
$ midori 
Instrucción ilegal (`core' generado)
$ firefox 
ExceptionHandler::GenerateDump cloned child 13198
ExceptionHandler::SendContinueSignalToChild sent continue signal to child
ExceptionHandler::WaitForContinueSignal waiting for continue signal...
```

And the Mozilla Crash Report have been:

```
Add-ons: ubufox%40ubuntu.com:3.2,%7B972ce4c6-7e08-4474-a285-3208198ce6fd%7D:50.1.0,e10srollout%40mozilla.org:1.5,firefox%40getpocket.com:1.0.5,aushelper%40mozilla.org:1.0,webcompat%40mozilla.org:1.0,langpack-es-AR%40firefox.mozilla.org:50.1.0,langpack-es-MX%40firefox.mozilla.org:50.1.0,langpack-en-GB%40firefox.mozilla.org:50.1.0,langpack-es-CL%40firefox.mozilla.org:50.1.0,langpack-en-ZA%40firefox.mozilla.org:50.1.0,langpack-es-ES%40firefox.mozilla.org:50.1.0
AddonsShouldHaveBlockedE10s: 1
BuildID: 20161209094930
ContentSandboxCapabilities: 117
CrashTime: 1482622777
E10SCohort: disqualified-test
EMCheckCompatibility: true
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1482617290
Notes: FP(D000-L10000-W00000000-T0000) OpenGL: Mesa Project -- Mesa DRI R200 (RV280 5964) x86/MMX+/3DNow!+/SSE DRI2 -- 1.3 Mesa 11.2.0 -- texture_from_pixmap

ProductID: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
ProductName: Firefox
ReleaseChannel: release
SafeMode: 0
SecondsSinceLastCrash: 418
StartupTime: 1482622765
TelemetryEnvironment: {"build":{"applicationId":"{ec8030f7-c20a-464f-9b0e-13a3a9e97384}","applicationName":"Firefox","architecture":"x86","buildId":"20161209094930","version":"50.1.0","vendor":"Mozilla","platformVersion":"50.1.0","xpcomAbi":"x86-gcc3","hotfixVersion":null},"partner":{"distributionId":null,"distributionVersion":null,"partnerId":null,"distributor":null,"distributorChannel":null,"partnerNames":[]},"system":{"memoryMB":493,"virtualMaxMB":null,"cpu":{"count":1,"cores":1,"vendor":"AuthenticAMD","family":6,"model":8,"stepping":1,"l2cacheKB":256,"l3cacheKB":256,"speedMHz":1500,"extensions":["hasMMX","hasSSE"]},"os":{"name":"Linux","version":"4.4.0-57-generic","locale":"es-ES"},"hdd":{"profile":{"model":null,"revision":null},"binary":{"model":null,"revision":null},"system":{"model":null,"revision":null}},"gfx":{"D2DEnabled":null,"DWriteEnabled":null,"adapters":[{"description":"Mesa Project -- Mesa DRI R200 (RV280 5964) x86/MMX+/3DNow!+/SSE DRI2","vendorID":"Mesa Project","deviceID":"Mesa DRI R200 (RV280 5964) x86/MMX+/3DNow!+/SSE DRI2","subsysID":null,"RAM":null,"driver":null,"driverVersion":"1.3 Mesa 11.2.0","driverDate":null,"GPUActive":true}],"monitors":[],"features":{"compositor":"none"}}},"settings":{"blocklistEnabled":true,"e10sEnabled":false,"e10sCohort":"disqualified-test","telemetryEnabled":false,"locale":"es-ES","update":{"channel":"release","enabled":true,"autoDownload":true},"userPrefs":{"browser.newtabpage.enhanced":true},"addonCompatibilityCheckEnabled":true,"isDefaultBrowser":false},"profile":{}}
Theme: classic/1.0
Throttleable: 1
UptimeTS: 13.574324
Vendor: Mozilla
Version: 50.1.0
useragent_locale: es-ES

This report also contains technical information about the state of the application when it crashed.
```

What can I do?

Thanks.

---

### Post by Keith_Helms on 2016-12-25
Pentium III is quite an old processor.  You may not have the minimum requirements to run the current versions of browsers.

---

### Post by mörgæs on 2016-12-25
Yes, most likely too weak hardware for a standard browser. 

Have you tried a browser like **links2**? It takes some time to get used to but it's worth the while learning.

---

### Post by cyttorak on 2016-12-25
Before Lubuntu 16.04 I had installed LXLE 14 and the browser works fine, so I think it is no a problem of hardware.

Anyway It is my hardware according to hardinfo:



```
Computer
********




Summary
-------


-Computer-
Processor        : AMD Athlon(tm) XP 1800+
Memory        : 505MB (210MB used)
Operating System        : Ubuntu 16.04.1 LTS
User Name        : vati (Valentín)
Date/Time        : dom 25 dic 2016 12:52:42 CET
-Display-
Resolution        : 1280x1024 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : NFORCE - NVidia nForce2
-Input Devices-
 Power Button
 Power Button
 Microsoft Comfort Curve Keyboard 2000
 Microsoft Comfort Curve Keyboard 2000
 PS/2+USB Mouse
 bttv IR (card        : 13)=
-Printers-
No printers found
-SCSI Disks-
ATA ST3120022A
_NEC DVD_RW ND-3540A
SanDisk Cruzer


Operating System
----------------


-Version-
Kernel        : Linux 4.4.0-57-generic (i686)
Compiled        : #78-Ubuntu SMP Fri Dec 9 23:46:51 UTC 2016
C Library        : Unknown
Default C Compiler        : GNU C Compiler version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4) 
Distribution        : Ubuntu 16.04.1 LTS
-Current Session-
Computer Name        : torre
User Name        : vati (Valentín)
Home Directory        : /home/vati
Desktop Environment        : LXDE (Lubuntu)
-Misc-
Uptime        : 26 minutes
Load Average        : 1,00, 0,00, 0,00


Kernel Modules
--------------


-Loaded Modules-
usblp        : USB Printer Device Class driver
nls_iso8859_1
uas
usb_storage        : USB Mass Storage driver for Linux
binfmt_misc
arc4        : ARC4 Cipher Algorithm
rc_avermedia
tuner_simple        : Simple 4-control-bytes style tuner driver
tuner_types        : Simple tuner device type database
rt2500pci        : Ralink RT2500 PCI &amp; PCMCIA Wireless LAN driver.
rt2x00pci        : rt2x00 pci library
rt2x00mmio        : rt2x00 mmio library
rt2x00lib        : rt2x00 library
mac80211        : IEEE 802.11 subsystem
tuner        : device driver for various TV and TV+FM radio tuners
snd_wavefront        : Turtle Beach Wavefront
tda7432        : bttv driver for the tda7432 audio processor chip
tvaudio        : device driver for various i2c TV sound decoder / audiomux chips
msp3400        : device driver for msp34xx TV sound processor
snd_cs4236        : Cirrus Logic CS4232-9
snd_intel8x0        : Intel 82801AA,82901AB,i810,i820,i830,i840,i845,MX440; SiS 7012; Ali 5455
bttv        : bttv - v4l/v4l2 driver module for bt848/878 based cards
cfg80211        : wireless configuration support
snd_opl3_lib        : Routines for control of AdLib FM cards (OPL2/OPL3/OPL4 chips)
snd_ac97_codec        : Universal interface for Audio Codec &apos;97
ppdev
snd_hwdep        : Hardware dependent layer
snd_wss_lib        : Routines for control of CS4231(A)/CS4232/InterWave &amp; compatible chips
ac97_bus
tea575x        : Routines for control of TEA5757/5759 Philips AM/FM radio tuner chips
tveeprom        : i2c Hauppauge eeprom decoder driver
eeprom_93cx6        : EEPROM 93cx6 chip driver
videobuf_dma_sg        : helper module to manage video4linux dma sg buffers
snd_pcm        : Midlevel PCM code for ALSA.
rc_core
videobuf_core        : helper module to manage video4linux buffers
snd_mpu401_uart        : Routines for control of MPU-401 in UART mode
v4l2_common        : misc helper functions for v4l2 device drivers
input_leds        : Input -&gt; LEDs Bridge
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
joydev        : Joystick device interfaces
videodev        : Device registrar for Video4Linux drivers v2
snd_seq_midi_event        : MIDI byte &lt;-&gt; sequencer event coder
media        : Device node registration for media drivers
snd_rawmidi        : Midlevel RawMidi code for ALSA.
snd_seq        : Advanced Linux Sound Architecture sequencer.
snd_seq_device        : ALSA sequencer device management
snd_timer        : ALSA timer interface
snd        : Advanced Linux Sound Architecture driver for soundcards.
soundcore        : Core sound module
serio_raw        : Raw serio driver
shpchp        : Standard Hot Plug PCI Controller Driver
ns558        : Classic gameport (ISA/PnP) driver
gameport        : Generic gameport layer
i2c_nforce2        : nForce2/3/4/5xx SMBus driver
8250_fintek        : Fintek F812164 module
parport_pc        : PC-style parallel port driver
parport
mac_hid
autofs4
hid_generic        : HID generic driver
usbhid        : USB HID core driver
hid
pata_acpi        : SCSI low-level driver for ATA in ACPI mode
radeon        : ATI Radeon
i2c_algo_bit        : I2C-Bus bit-banging algorithm
ttm        : TTM memory manager subsystem (for DRM device)
drm_kms_helper        : DRM KMS helper
syscopyarea        : Generic copyarea (sys-to-sys)
sysfillrect        : Generic fill rectangle (sys-to-sys)
sysimgblt        : 1-bit/8-bit to 1-32 bit color expansion (sys-to-sys)
fb_sys_fops        : Generic file read (fb in system RAM)
drm        : DRM shared core routines
firewire_ohci        : Driver for PCI OHCI IEEE1394 controllers
8139too        : RealTek RTL-8139 Fast Ethernet driver
firewire_core        : Core IEEE1394 transaction logic
8139cp        : RealTek RTL-8139C+ series 10/100 PCI Ethernet driver
pata_amd        : low-level driver for AMD and Nvidia PATA IDE
crc_itu_t        : CRC ITU-T V.41 calculations
mii        : MII hardware support library
fjes        : FUJITSU Extended Socket Network Device Driver
floppy


Boots
-----


-Boots-
Sun Dec 25 12:26        : 4.4.0-57-generic|still
Sun Dec 25 00:03        : 4.4.0-57-generic|still
Sat Dec 24 23:11        : 4.4.0-57-generic|still
Sat Dec 24 22:38        : 4.4.0-31-generic|-


Languages
---------


-Available Languages-
en_AG        : English language locale for Antigua and Barbuda
en_AG.utf8        : English language locale for Antigua and Barbuda
en_AU.utf8        : English locale for Australia
en_BW.utf8        : English locale for Botswana
en_CA.utf8        : English locale for Canada
en_DK.utf8        : English locale for Denmark
en_GB.utf8        : English locale for Britain
en_HK.utf8        : English locale for Hong Kong
en_IE.utf8        : English locale for Ireland
en_IN        : English language locale for India
en_IN.utf8        : English language locale for India
en_NG        : English locale for Nigeria
en_NG.utf8        : English locale for Nigeria
en_NZ.utf8        : English locale for New Zealand
en_PH.utf8        : English language locale for Philippines
en_SG.utf8        : English language locale for Singapore
en_US.utf8        : English locale for the USA
en_ZA.utf8        : English locale for South Africa
en_ZM        : English locale for Zambia
en_ZM.utf8        : English locale for Zambia
en_ZW.utf8        : English locale for Zimbabwe
es_AR.utf8        : Spanish locale for Argentina
es_BO.utf8        : Spanish locale for Bolivia
es_CL.utf8        : Spanish locale for Chile
es_CO.utf8        : Spanish locale for Colombia
es_CR.utf8        : Spanish locale for Costa Rica
es_CU        : Spanish locale for Cuba
es_CU.utf8        : Spanish locale for Cuba
es_DO.utf8        : Spanish locale for Dominican Republic
es_EC.utf8        : Spanish locale for Ecuador
es_ES.utf8        : Spanish locale for Spain
es_GT.utf8        : Spanish locale for Guatemala
es_HN.utf8        : Spanish locale for Honduras
es_MX.utf8        : Spanish locale for Mexico
es_NI.utf8        : Spanish locale for Nicaragua
es_PA.utf8        : Spanish locale for Panama
es_PE.utf8        : Spanish locale for Peru
es_PR.utf8        : Spanish locale for Puerto Rico
es_PY.utf8        : Spanish locale for Paraguay
es_SV.utf8        : Spanish locale for El Salvador
es_US.utf8        : Spanish locale for the USA
es_UY.utf8        : Spanish locale for Uruguay
es_VE.utf8        : Spanish locale for Venezuela


Filesystems
-----------


-Mounted File Systems-
udev    /dev    0,00 % (228,6 MiB of 228,6 MiB)    
tmpfs    /run    6,09 % (46,3 MiB of 49,4 MiB)    
/dev/sda1    /    24,32 % (82,8 GiB of 109,4 GiB)    
tmpfs    /dev/shm    0,00 % (246,7 MiB of 246,7 MiB)    
tmpfs    /run/lock    0,08 % (5,0 MiB of 5,0 MiB)    
tmpfs    /sys/fs/cgroup    0,00 % (246,7 MiB of 246,7 MiB)    
tmpfs    /run/user/1000    0,02 % (49,3 MiB of 49,4 MiB)    
/dev/sdb    /media/vati/GF    0,00 % (14,9 GiB of 14,9 GiB)    


Display
-------


-Display-
Resolution        : 1280x1024 pixels
Vendor        : The X.Org Foundation
Version        : 1.18.4
-Monitors-
Monitor 0        : 1280x1024 pixels
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
Present
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
XVideo-MotionCompensation
-OpenGL-
Vendor        : Unknown
Renderer        : Unknown
Version        : Unknown
Direct Rendering        : No


Environment Variables
---------------------


-Environment Variables-
XDG_VTNR        : 7
SSH_AGENT_PID        : 1455
XDG_SESSION_ID        : c2
SAL_USE_VCLPLUGIN        : gtk
XDG_GREETER_DATA_DIR        : /var/lib/lightdm-data/vati
TERM        : xterm
SHELL        : /bin/bash
XDG_MENU_PREFIX        : lxde-
USER        : vati
LS_COLORS        : rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
XDG_SESSION_PATH        : /org/freedesktop/DisplayManager/Session0
XDG_SEAT_PATH        : /org/freedesktop/DisplayManager/Seat0
SSH_AUTH_SOCK        : /tmp/ssh-FLeo5TiZEdLn/agent.1409
DEFAULTS_PATH        : /usr/share/gconf/Lubuntu.default.path
XDG_CONFIG_DIRS        : /etc/xdg/lubuntu:/etc/xdg/xdg-Lubuntu:/etc/xdg
PATH        : /home/vati/bin:/home/vati/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
DESKTOP_SESSION        : Lubuntu
QT_QPA_PLATFORMTHEME        : lxqt
XDG_SESSION_TYPE        : x11
PWD        : /home/vati
LANG        : es_ES.UTF-8
GDM_LANG        : es_ES
MANDATORY_PATH        : /usr/share/gconf/Lubuntu.mandatory.path
GDMSESSION        : Lubuntu
_LXSESSION_PID        : 1409
QT_PLATFORM_PLUGIN        : lxqt
XDG_SEAT        : seat0
HOME        : /home/vati
SHLVL        : 1
XDG_CONFIG_HOME        : /home/vati/.config
LANGUAGE        : es_ES
XDG_SESSION_DESKTOP        : Lubuntu
LOGNAME        : vati
XDG_DATA_DIRS        : /etc/xdg/lubuntu:/usr/local/share:/usr/share:/usr/share/gdm:/var/lib/menu-xdg:/usr/share/Lubuntu:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS        : unix:abstract=/tmp/dbus-MkE2MtDa4c,guid=5b7fdc50a1e18a21cf72d1fc585fae5e
LESSOPEN        : | /usr/bin/lesspipe %s
XDG_RUNTIME_DIR        : /run/user/1000
DISPLAY        : :0.0
XDG_CURRENT_DESKTOP        : LXDE
LESSCLOSE        : /usr/bin/lesspipe %s %s
XAUTHORITY        : /home/vati/.Xauthority
_        : /usr/bin/hardinfo


Users
-----


-Users-
root        : root
daemon        : daemon
bin        : bin
sys        : sys
sync        : sync
games        : games
man        : man
lp        : lp
mail        : mail
news        : news
uucp        : uucp
proxy        : proxy
www-data        : www-data
backup        : backup
list        : Mailing List Manager
irc        : ircd
gnats        : Gnats Bug-Reporting System (admin)
nobody        : nobody
systemd-timesync        : systemd Time Synchronization
systemd-network        : systemd Network Management
systemd-resolve        : systemd Resolver
systemd-bus-proxy        : systemd Bus Proxy
syslog
_apt
messagebus
uuidd
lightdm        : Light Display Manager
ntp
whoopsie
dnsmasq        : dnsmasq
vati        : Valentín
avahi        : Avahi mDNS daemon
colord        : colord colour management daemon


Devices
*******




Processor
---------


-Processor-
Name        : AMD Athlon(tm) XP 1800+
Family, model, stepping        : 6, 8, 1 (AMD Athlon XP/MP (Thoroughbred))
Vendor        : AuthenticAMD
-Configuration-
Cache Size        : 256kb
Frequency        : 1500,00MHz
BogoMIPS        : 3014,00
Byte Order        : Little Endian
-Features-
FDIV Bug        : no
HLT Bug        : no
F00F Bug        : no
Coma Bug        : no
Has FPU        : yes
-Cache-
Level 1 (Data)        : 2-way set-associative, 512 sets, 64KB size
Level 1 (Instruction)        : 2-way set-associative, 512 sets, 64KB size
Level 2 (Unified)        : 16-way set-associative, 256 sets, 256KB size
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
apic        : Advanced Programmable Interrupt Controller
sep        : Fast System Call (SYSENTER/SYSEXIT)
mtrr        : Memory Type Range Registers
pge        : Page Global Enable
mca        : Machine Check Architecture
cmov        : Conditional Move instruction
pat        : Page Attribute Table
pse36        : 36bit Page Size Extensions
mmx        : MMX technology
fxsr        : FXSAVE and FXRSTOR instructions
sse        : SSE instructions
syscall        : SYSCALL and SYSEXIT instructions
mmxext        : Extended MMX Technology
3dnowext        : Extended 3DNow! Technology
3dnow        : 3DNow! Technology
3dnowprefetch
vmmcall


Memory
------


-Memory-
Total Memory        : 505328 kB
Free Memory        : 45632 kB
MemAvailable        : 343212 kB
Buffers        : 41960 kB
Cached        : 249424 kB
Cached Swap        : 232 kB
Active        : 213236 kB
Inactive        : 185604 kB
Active(anon)        : 17560 kB
Inactive(anon)        : 96500 kB
Active(file)        : 195676 kB
Inactive(file)        : 89104 kB
Unevictable        : 32 kB
Mlocked        : 32 kB
High Memory        : 0 kB
Free High Memory        : 0 kB
Low Memory        : 505328 kB
Free Low Memory        : 45632 kB
Virtual Memory        : 523260 kB
Free Virtual Memory        : 520196 kB
Dirty        : 64 kB
Writeback        : 0 kB
AnonPages        : 107276 kB
Mapped        : 87908 kB
Shmem        : 6600 kB
Slab        : 36768 kB
SReclaimable        : 25740 kB
SUnreclaim        : 11028 kB
KernelStack        : 1952 kB
PageTables        : 3676 kB
NFS_Unstable        : 0 kB
Bounce        : 0 kB
WritebackTmp        : 0 kB
CommitLimit        : 775924 kB
Committed_AS        : 1242828 kB
VmallocTotal        : 512056 kB
VmallocUsed        : 0 kB
VmallocChunk        : 0 kB
AnonHugePages        : 0 kB
CmaTotal        : 0 kB
CmaFree        : 0 kB
HugePages_Total        : 0
HugePages_Free        : 0
HugePages_Rsvd        : 0
HugePages_Surp        : 0
Hugepagesize        : 2048 kB
DirectMap4k        : 94144 kB
DirectMap2M        : 430080 kB


PCI Devices
-----------


-PCI Devices-
Host bridge        : NVIDIA Corporation nForce2 IGP2 (rev c1)
RAM memory        : NVIDIA Corporation nForce2 Memory Controller 0 (rev c1)
RAM memory        : NVIDIA Corporation nForce2 Memory Controller 4 (rev c1)
RAM memory        : NVIDIA Corporation nForce2 Memory Controller 3 (rev c1)
RAM memory        : NVIDIA Corporation nForce2 Memory Controller 2 (rev c1)
RAM memory        : NVIDIA Corporation nForce2 Memory Controller 5 (rev c1)
ISA bridge        : NVIDIA Corporation nForce2 ISA Bridge (rev a4)
SMBus        : NVIDIA Corporation nForce2 SMBus (MCP) (rev a2)
USB controller        : NVIDIA Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
USB controller        : NVIDIA Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
USB controller        : NVIDIA Corporation nForce2 USB Controller (rev a4) (prog-if 20 [EHCI])
Multimedia audio controller        : NVIDIA Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
PCI bridge        : NVIDIA Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])
IDE interface        : NVIDIA Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
PCI bridge        : NVIDIA Corporation nForce2 AGP (rev c1) (prog-if 00 [Normal decode])
Ethernet controller        : Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
Multimedia video controller        : Brooktree Corporation Bt878 Video Capture (rev 02)
Multimedia controller        : Brooktree Corporation Bt878 Audio Capture (rev 02)
Network controller        : Ralink corp. RT2500 Wireless 802.11bg (rev 01)
FireWire (IEEE 1394)        : LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 61) (prog-if 10 [OHCI])
Ethernet controller        : Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
VGA compatible controller        : Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200 SE] (rev 01) (prog-if 00 [VGA controller])
Display controller        : Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200 SE] (Secondary) (rev 01)


USB Devices
-----------




Printers
--------


-Printers-
No printers found


Battery
-------


-No batteries-
No batteries found on this system


Sensors
-------




Input Devices
-------------


-Input Devices-
 Power Button
 Power Button
 Microsoft Comfort Curve Keyboard 2000
 Microsoft Comfort Curve Keyboard 2000
 PS/2+USB Mouse
 bttv IR (card        : 13)=


Storage
-------


-SCSI Disks-
ATA ST3120022A
_NEC DVD_RW ND-3540A
SanDisk Cruzer


DMI
---


-BIOS-
Date        : 08/02/2004
Vendor        : Award Software International, Inc. ([www.award-bios.com]("http://www.award-bios.com"))
Version        : F6
-Board-
Name        : nVidia-nForce2 (NVIDIA, [www.nvidia.com]("http://www.nvidia.com"))
Vendor        : Gigabyte Technology Co., Ltd. ([www.gigabyte.com.tw]("http://www.gigabyte.com.tw"))


Resources
---------


-I/O Ports-
<tt>0000-0cf7 </tt>        : PCI Bus 0000:00
<tt>  0000-001f </tt>        : dma1
<tt>  0020-0021 </tt>        : pic1
<tt>  0040-0043 </tt>        : timer0
<tt>  0050-0053 </tt>        : timer1
<tt>  0060-0060 </tt>        : keyboard
<tt>  0061-0061 </tt>        : PNP0800:00
<tt>  0064-0064 </tt>        : keyboard
<tt>  0070-0073 </tt>        : rtc0
<tt>  0080-008f </tt>        : dma page reg
<tt>  00a0-00a1 </tt>        : pic2
<tt>  00c0-00df </tt>        : dma2
<tt>  00f0-00ff </tt>        : PNP0C04:00
<tt>    00f0-00ff </tt>        : fpu
<tt>  0170-0177 </tt>        : NVIDIA Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
<tt>    0170-0177 </tt>        : low-level driver for AMD and Nvidia PATA IDE
<tt>  01f0-01f7 </tt>        : NVIDIA Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
<tt>    01f0-01f7 </tt>        : low-level driver for AMD and Nvidia PATA IDE
<tt>  0201-0201 </tt>        : ns558-pnp
<tt>  0290-029f </tt>        : pnp 00:03
<tt>  02f8-02ff </tt>        : serial
<tt>  0376-0376 </tt>        : NVIDIA Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
<tt>    0376-0376 </tt>        : low-level driver for AMD and Nvidia PATA IDE
<tt>  0378-037a </tt>        : parport0
<tt>  03c0-03df </tt>        : vesafb
<tt>  03f2-03f2 </tt>        : floppy
<tt>  03f4-03f5 </tt>        : floppy
<tt>  03f6-03f6 </tt>        : NVIDIA Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
<tt>    03f6-03f6 </tt>        : low-level driver for AMD and Nvidia PATA IDE
<tt>  03f7-03f7 </tt>        : floppy
<tt>  03f8-03ff </tt>        : serial
<tt>  04d0-04d1 </tt>        : pnp 00:03
<tt>  0778-077a </tt>        : parport0
<tt>  0800-0805 </tt>        : pnp 00:03
<tt>0cf8-0cff </tt>        : PCI conf1
<tt>0d00-ffff </tt>        : PCI Bus 0000:00
<tt>  1000-107f </tt>        : pnp 00:00
<tt>    1000-1003 </tt>        : ACPI PM1a_EVT_BLK
<tt>    1004-1005 </tt>        : ACPI PM1a_CNT_BLK
<tt>    1008-100b </tt>        : ACPI PM_TMR
<tt>    1020-1027 </tt>        : ACPI GPE0_BLK
<tt>  1080-10ff </tt>        : pnp 00:00
<tt>  1400-147f </tt>        : pnp 00:00
<tt>  1480-14ff </tt>        : pnp 00:00
<tt>    14a0-14af </tt>        : ACPI GPE1_BLK
<tt>  1800-187f </tt>        : pnp 00:00
<tt>  1880-18ff </tt>        : pnp 00:00
<tt>  1c00-1c3f </tt>        : pnp 00:01
<tt>    1c00-1c3f </tt>        : nForce2_smbus
<tt>  2000-203f </tt>        : pnp 00:01
<tt>    2000-203f </tt>        : nForce2_smbus
<tt>  9000-9fff </tt>        : PCI Bus 0000:01
<tt>    9000-90ff </tt>        : Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
<tt>      9000-90ff </tt>        : RealTek RTL-8139 Fast Ethernet driver
<tt>    9400-94ff </tt>        : Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
<tt>      9400-94ff </tt>        : RealTek RTL-8139 Fast Ethernet driver
<tt>  a000-afff </tt>        : PCI Bus 0000:02
<tt>    a000-a0ff </tt>        : Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200 SE] (rev 01) (prog-if 00 [VGA controller])
<tt>  b000-b0ff </tt>        : NVIDIA Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
<tt>    b000-b0ff </tt>        : NVidia nForce2
<tt>  b400-b47f </tt>        : NVIDIA Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
<tt>    b400-b47f </tt>        : NVidia nForce2
<tt>  c000-c01f </tt>        : NVIDIA Corporation nForce2 SMBus (MCP) (rev a2)
<tt>  f000-f00f </tt>        : NVIDIA Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
<tt>    f000-f00f </tt>        : low-level driver for AMD and Nvidia PATA IDE
-Memory-
<tt>00000000-00000fff </tt>        : reserved
<tt>00001000-0009ffff </tt>        : System RAM
<tt>000a0000-000bffff </tt>        : PCI Bus 0000:00
<tt>  000a0000-000bffff </tt>        : Video RAM area
<tt>000c0000-000dffff </tt>        : PCI Bus 0000:00
<tt>  000c0000-000ccfff </tt>        : Video ROM
<tt>  000d0000-000d27ff </tt>        : Adapter ROM
<tt>  000d2800-000d3fff </tt>        : pnp 00:02
<tt>000f0000-000fffff </tt>        : reserved
<tt>  000f0000-000fffff </tt>        : System ROM
<tt>00100000-1ffeffff </tt>        : System RAM
<tt>  01000000-017ba73a </tt>        : Kernel code
<tt>  017ba73b-01b8f3ff </tt>        : Kernel data
<tt>  01c84000-01d4bfff </tt>        : Kernel bss
<tt>1fff0000-1fff2fff </tt>        : ACPI Non-volatile Storage
<tt>1fff3000-1fffffff </tt>        : ACPI Tables
<tt>20000000-febfffff </tt>        : PCI Bus 0000:00
<tt>  d0000000-dfffffff </tt>        : PCI Bus 0000:02
<tt>    d0000000-d7ffffff </tt>        : Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200 SE] (rev 01) (prog-if 00 [VGA controller])
<tt>    d8000000-dfffffff </tt>        : Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200 SE] (Secondary) (rev 01)
<tt>  e0000000-e3ffffff </tt>        : NVIDIA Corporation nForce2 IGP2 (rev c1)
<tt>  e4000000-e4ffffff </tt>        : PCI Bus 0000:01
<tt>    e4000000-e4000fff </tt>        : Brooktree Corporation Bt878 Video Capture (rev 02)
<tt>      e4000000-e4000fff </tt>        : bttv0
<tt>    e4001000-e4001fff </tt>        : Brooktree Corporation Bt878 Audio Capture (rev 02)
<tt>  e5000000-e6ffffff </tt>        : PCI Bus 0000:02
<tt>    e5000000-e501ffff </tt>        : Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200 SE] (rev 01) (prog-if 00 [VGA controller])
<tt>    e6000000-e600ffff </tt>        : Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200 SE] (rev 01) (prog-if 00 [VGA controller])
<tt>    e6010000-e601ffff </tt>        : Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200 SE] (Secondary) (rev 01)
<tt>  e7000000-e7ffffff </tt>        : PCI Bus 0000:01
<tt>    e7000000-e7001fff </tt>        : Ralink corp. RT2500 Wireless 802.11bg (rev 01)
<tt>      e7000000-e7001fff </tt>        : Ralink corp. RT2500 Wireless 802.11bg (rev 01)
<tt>    e7002000-e70020ff </tt>        : Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
<tt>      e7002000-e70020ff </tt>        : RealTek RTL-8139 Fast Ethernet driver
<tt>    e7003000-e7003fff </tt>        : LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 61) (prog-if 10 [OHCI])
<tt>      e7003000-e7003fff </tt>        : Driver for PCI OHCI IEEE1394 controllers
<tt>    e7004000-e70040ff </tt>        : Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
<tt>      e7004000-e70040ff </tt>        : RealTek RTL-8139 Fast Ethernet driver
<tt>  e8000000-e8000fff </tt>        : NVIDIA Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
<tt>    e8000000-e8000fff </tt>        : NVidia nForce2
<tt>  e8002000-e8002fff </tt>        : NVIDIA Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
<tt>    e8002000-e8002fff </tt>        : ohci_hcd
<tt>  e8003000-e8003fff </tt>        : NVIDIA Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
<tt>    e8003000-e8003fff </tt>        : ohci_hcd
<tt>  e8004000-e80040ff </tt>        : NVIDIA Corporation nForce2 USB Controller (rev a4) (prog-if 20 [EHCI])
<tt>    e8004000-e80040ff </tt>        : ehci_hcd
<tt>fec00000-fec00fff </tt>        : reserved
<tt>  fec00000-fec003ff </tt>        : IOAPIC 0
<tt>fee00000-fee00fff </tt>        : Local APIC
<tt>  fee00000-fee00fff </tt>        : reserved
<tt>    fee00000-fee00fff </tt>        : pnp 00:02
<tt>ffff0000-ffffffff </tt>        : reserved
<tt>  ffff0000-ffffffff </tt>        : pnp 00:02
-DMA-
<tt> 2</tt>        : floppy
<tt> 3</tt>        : parport0
<tt> 4</tt>        : cascade
```

---

### Post by RobGoss on 2016-12-25
You really should use the **code tags** when posting your information it will make it much easier to read, from looking at your specs your RAM is not enough. I see you have **Memory : 505MB (210MB used) ** I believe 512-MB is the minimum to run even the lighter versions of Ubuntu

---

### Post by mörgæs on 2016-12-26
You don't have a Pentium 3 but an AMD Athlon XP from 2002. Not that it makes much difference.

In combination with limited memory and a slow graphics adaptor I think you should set your expectations accordingly.

Best you can do is trying a selection of browsers. How did **links2** behave?

---

