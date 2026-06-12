---
title: "Acer Aspire E1-432 running 13.10 and 14.04"
date: 2014-10-09
forum: General Help
---

### Post by jesus-freak on 2014-10-09
I bought a new laptop for my wife and at the time the latest version of Ubuntu was 13.10 so that is what I installed. It worked ok but had some freezing issues especially with web browsers freezing up and going dim. I didn't do anything about it because I knew 14.04 would be out soon so I just figured after I updated it, it would be fixed. BUT after updating her laptop to 14.04, we have the exact same issues, maybe even a little worse. Can someone look at the specs for this computer and tell me if there is something here that Ubuntu just doesn't like? It's not just a browser issue because we have tried several with the same results and it doesn't just happen with browsers. It's just overall not very stable. For example when we plug it into an external monitor, it will almost always freeze up and crash. I'm just about to the point of switching to a none-buntu distro and seeing if it still has the same problems or even, god forbid, putting Windows 8 on it since that is the OS it was built for. Here is the link with the specs. Any thoughts or advice would be great!!

[http://www.pcworld.com/product/1264578/acer-aspire-e1-432-29554g50mnkk-notebook.html](http://www.pcworld.com/product/1264578/acer-aspire-e1-432-29554g50mnkk-notebook.html)

---

### Post by jesus-freak on 2014-10-10
No ideas? I've seen some other posts with similar problems but that all had to do with nvidia drivers. As far as I know this one doesn't have an nvidia graphics card.
Graphics Controller Manufacturer	 - Intel
Graphics Controller Model -	Graphics Media Accelerator HD

---

### Post by Dennis N on 2014-10-10
I don't see anything that stands out as a problem - Intel components almost without exception work well in Ubuntu. You have Intel HD graphics and Intel processor and overall it looks like the laptop should be Linux compatable. I assume the wireless works? Searching for that same model, I even see it offered by Acer with Linux already installed (in Cambodia and Myanmar) so it should be good. 

Possibly it is not the operating system at all, but some internal component problem. Is it possible where you live to exchange it  and try another unit and see if it shows the same behavior?

---

### Post by jesus-freak on 2014-10-10
Yes, I have always had good luck with intel components and Ubuntu, that is why I selected that model. I'm an American but I now live in the Philippines. They do things a lot differently here. First of all even though that laptop is built for Windows 8, they will sell it without any OS and give you the choice of having them install Windows 8 and pay extra for it, or have them install linux for free. While that is pretty cool, all sales are final and returns or replacements after one week are pretty impossible.

---

### Post by Dennis N on 2014-10-10
Have you tried the memory test?

[https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

---

### Post by jesus-freak on 2014-10-10
When I go to the grub screen there are two options for memory tests so I did them both and took screen shots.

---

### Post by jesus-freak on 2014-10-10
Computer

Summary
```
Computer
Processor    2x Intel(R) Celeron(R) 2955U @ 1.40GHz
Memory    3944MB (947MB used)
Operating System    Ubuntu 14.04.1 LTS
User Name    wawab (wawab)
Date/Time    Friday, 10 October, 2014 04:16:25 PM PHT
Display
Resolution    1366x768 pixels
OpenGL Renderer    Mesa DRI Intel(R) Haswell Mobile x86/MMX/SSE2
X11 Vendor    The X.Org Foundation
Multimedia
Audio Adapter    HDA-Intel - HDA Intel HDMI
Audio Adapter    USB-Audio - USB PnP Sound Device
Audio Adapter    HDA-Intel - HDA Intel PCH
Input Devices
Lid Switch    
Sleep Button    
Power Button    
AT Translated Set 2 keyboard    
USB PnP Sound Device    
ETPS/2 Elantech Touchpad    
HD WebCam    
Video Bus    
HDA Intel HDMI HDMI/DP,pcm    8=
HDA Intel HDMI HDMI/DP,pcm    7=
HDA Intel HDMI HDMI/DP,pcm    3=
HDA Intel PCH Headphone    
Acer WMI hotkeys    
Acer BMA150 accelerometer    
PixArt USB Optical Mouse    
Printers
No printers found    
SCSI Disks
ATA WDC WD7500BPVX-2    
HL-DT-ST DVDRAM GU71N    
Operating System
Version
Kernel    Linux 3.13.0-37-generic (i686)
Compiled    #64-Ubuntu SMP Mon Sep 22 21:30:01 UTC 2014
C Library    Unknown
Default C Compiler    GNU C Compiler version 4.8.2 (Ubuntu 4.8.2-19ubuntu1)
Distribution    Ubuntu 14.04.1 LTS
Current Session
Computer Name    wawab-Aspire-E1-432
User Name    wawab (wawab)
Home Directory    /home/wawab
Desktop Environment    Unity (ubuntu)
Misc
Uptime    1 hour, 1 minute
Load Average    0.73, 0.31, 0.18
Kernel Modules
Loaded Modules
ctr    CTR Counter block mode
ccm    Counter with CBC MAC
bnep    Bluetooth BNEP ver 1.3
rfcomm    Bluetooth RFCOMM ver 1.11
acer_wmi    Acer Laptop WMI Extras Driver
sparse_keymap    Generic support for sparse keymaps
snd_hda_codec_hdmi    HDMI HD-audio codec
snd_hda_codec_realtek    Realtek HD-audio codec
uvcvideo    USB Video Class driver
videobuf2_vmalloc    vmalloc memory handling routines for videobuf2
videobuf2_memops    common memory handling routines for videobuf2
videobuf2_core    Driver helper framework for Video for Linux 2
videodev    Device registrar for Video4Linux drivers v2
intel_rapl    Driver for Intel RAPL (Running Average Power Limit)
snd_usb_audio    USB Audio
x86_pkg_temp_thermal    X86 PKG TEMP Thermal Driver
snd_usbmidi_lib    USB Audio/MIDI helper module
intel_powerclamp    Package Level C-state Idle Injection for Intel CPUs
coretemp    Intel Core temperature monitor
kvm_intel    
kvm    
crc32_pclmul    
snd_hda_intel    Intel HDA driver
snd_hda_codec    HDA codec core
snd_hwdep    Hardware dependent layer
joydev    Joystick device interfaces
snd_pcm    Midlevel PCM code for ALSA.
snd_page_alloc    Memory allocator for ALSA system.
serio_raw    Raw serio driver
snd_seq_midi    Advanced Linux Sound Architecture sequencer MIDI synth.
snd_seq_midi_event    MIDI byte <-> sequencer event coder
arc4    ARC4 Cipher Algorithm
snd_rawmidi    Midlevel RawMidi code for ALSA.
ath9k    Support for Atheros 802.11n wireless LAN cards.
ath9k_common    Shared library for Atheros wireless 802.11n LAN cards.
snd_seq    Advanced Linux Sound Architecture sequencer.
ath9k_hw    Support for Atheros 802.11n wireless LAN cards.
rtsx_pci_ms    Realtek PCI-E Memstick Card Host Driver
mei_me    Intel(R) Management Engine Interface
memstick    Sony MemoryStick core driver
ath    Shared library for Atheros wireless LAN cards.
mac80211    IEEE 802.11 subsystem
lpc_ich    LPC interface for Intel ICH
mei    Intel(R) Management Engine Interface
cfg80211    wireless configuration support
btusb    Generic Bluetooth USB driver ver 0.6
snd_seq_device    ALSA sequencer device management
snd_timer    ALSA timer interface
bluetooth    Bluetooth Core ver 2.17
snd    Advanced Linux Sound Architecture driver for soundcards.
i915    Intel Graphics
soundcore    Core sound module
drm_kms_helper    DRM KMS helper
wmi    ACPI-WMI Mapping Driver
parport_pc    PC-style parallel port driver
video    ACPI Video Driver
drm    DRM shared core routines
i2c_algo_bit    I2C-Bus bit-banging algorithm
ppdev    
mac_hid    
lp    
parport    
hid_generic    HID generic driver
usbhid    USB HID core driver
hid    
rtsx_pci_sdmmc    Realtek PCI-E SD/MMC Card Host Driver
r8169    RealTek RTL-8169 Gigabit Ethernet driver
psmouse    PS/2 mouse driver
mii    MII hardware support library
rtsx_pci    Realtek PCI-E Card Reader Driver
ahci    AHCI SATA low-level driver
libahci    Common AHCI SATA low-level routines
Boots
Boots
Fri Oct 10 15:15    3..13.0-37-generi|-
Fri Oct 10 08:02    3..13.0-37-generi|-
Fri Oct 10 00:07    3..13.0-37-generi|-
Thu Oct 9 11:23-    3..13.0-37-generi|02:000
Wed Oct 8 11:18-    3..13.0-37-generi|02:000
Wed Oct 8 08:19-    3..13.0-37-generi|02:000
Tue Oct 7 07:57-    3..13.0-37-generi|03:066
Mon Oct 6 08:14-    3..13.0-37-generi|02:022
Sun Oct 5 11:52-    3..13.0-37-generi|01:388
Sat Oct 4 12:06-    3..13.0-37-generi|02:033
Fri Oct 3 22:03-    3..13.0-37-generi|02:233
Fri Oct 3 15:51-    3..13.0-37-generi|22:033
Fri Oct 3 08:03-    3..13.0-37-generi|22:033
Languages
Available Languages
en_AG    English language locale for Antigua and Barbuda
en_AG.utf8    English language locale for Antigua and Barbuda
en_AU.utf8    English locale for Australia
en_BW.utf8    English locale for Botswana
en_CA.utf8    English locale for Canada
en_DK.utf8    English locale for Denmark
en_GB.utf8    English locale for Britain
en_HK.utf8    English locale for Hong Kong
en_IE.utf8    English locale for Ireland
en_IN    English language locale for India
en_IN.utf8    English language locale for India
en_NG    English locale for Nigeria
en_NG.utf8    English locale for Nigeria
en_NZ.utf8    English locale for New Zealand
en_PH.utf8    English language locale for Philippines
en_SG.utf8    English language locale for Singapore
en_US.utf8    English locale for the USA
en_ZA.utf8    English locale for South Africa
en_ZM    English locale for Zambia
en_ZM.utf8    English locale for Zambia
en_ZW.utf8    English locale for Zimbabwe
Filesystems
Mounted File Systems
/dev/sda5    /    9.86 % (303.0 GiB of 336.1 GiB)
none    /sys/fs/cgroup    0.00 % (4.0 KiB of 4.0 KiB)
udev    /dev    0.00 % (1.9 GiB of 1.9 GiB)
tmpfs    /run    0.31 % (384.0 MiB of 385.2 MiB)
none    /run/lock    0.00 % (5.0 MiB of 5.0 MiB)
none    /run/shm    0.78 % (1.9 GiB of 1.9 GiB)
none    /run/user    0.13 % (99.9 MiB of 100.0 MiB)
none    /tmp/guest-X5i6dc    0.08 % (1.9 GiB of 1.9 GiB)
Display
Display
Resolution    1366x768 pixels
Vendor    The X.Org Foundation
Version    1.15.1
Monitors
Monitor 0    1366x768 pixels
Extensions
BIG-REQUESTS    
Composite    
DAMAGE    
DOUBLE-BUFFER    
DPMS    
DRI2    
DRI3    
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
OpenGL
Vendor    Intel Open Source Technology Center
Renderer    Mesa DRI Intel(R) Haswell Mobile x86/MMX/SSE2
Version    3.0 Mesa 10.1.3
Direct Rendering    Yes
Environment Variables
Environment Variables
GNOME_KEYRING_PID    1633
USER    wawab
LANGUAGE    en_PH:en
XDG_SEAT    seat0
TEXTDOMAIN    im-config
COMPIZ_CONFIG_PROFILE    ubuntu
SSH_AGENT_PID    1702
SESSION    ubuntu
HOME    /home/wawab
QT4_IM_MODULE    xim
DESKTOP_SESSION    ubuntu
XDG_SEAT_PATH    /org/freedesktop/DisplayManager/Seat0
GTK_MODULES    overlay-scrollbar:unity-gtk-module
INSTANCE    
DBUS_SESSION_BUS_ADDRESS    unix:abstract=/tmp/dbus-sWmcrZI3vw
GNOME_KEYRING_CONTROL    /run/user/1000/keyring-irt6th
UBUNTU_MENUPROXY    1
QT_QPA_PLATFORMTHEME    appmenu-qt5
MANDATORY_PATH    /usr/share/gconf/ubuntu.mandatory.path
IM_CONFIG_PHASE    1
SESSIONTYPE    gnome-session
LOGNAME    wawab
GTK_IM_MODULE    ibus
DEFAULTS_PATH    /usr/share/gconf/ubuntu.default.path
XDG_SESSION_ID    c2
GNOME_DESKTOP_SESSION_ID    this-is-deprecated
PATH    /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
GDM_LANG    en_US
SELINUX_INIT    YES
XDG_SESSION_PATH    /org/freedesktop/DisplayManager/Session0
XDG_RUNTIME_DIR    /run/user/1000
DISPLAY    :0
XDG_CURRENT_DESKTOP    Unity
LANG    en_PH.UTF-8
XAUTHORITY    /home/wawab/.Xauthority
XMODIFIERS    @im=ibus
XDG_GREETER_DATA_DIR    /var/lib/lightdm-data/wawab
SSH_AUTH_SOCK    /run/user/1000/keyring-irt6th/ssh
SSH_AGENT_LAUNCHER    upstart
SHELL    /bin/bash
GDMSESSION    ubuntu
TEXTDOMAINDIR    /usr/share/locale/
UPSTART_SESSION    unix:abstract=/com/ubuntu/upstart-session/1000/1635
XDG_VTNR    7
QT_IM_MODULE    ibus
PWD    /home/wawab
XDG_CONFIG_DIRS    /etc/xdg/xdg-ubuntu:/usr/share/upstart/xdg:/etc/xdg
XDG_DATA_DIRS    /usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/
CLUTTER_IM_MODULE    xim
JOB    dbus
XDG_MENU_PREFIX    gnome-
SESSION_MANAGER    local/wawab-Aspire-E1-432:@/tmp/.ICE-unix/1768,unix/wawab-Aspire-E1-432:/tmp/.ICE-unix/1768
GPG_AGENT_INFO    /run/user/1000/keyring-irt6th/gpg:0:1
GIO_LAUNCHED_DESKTOP_FILE    /usr/share/applications/hardinfo.desktop
GIO_LAUNCHED_DESKTOP_FILE_PID    5837
COMPIZ_BIN_PATH    /usr/bin/
Users
Users
root    root
daemon    daemon
bin    bin
sys    sys
sync    sync
games    games
man    man
lp    lp
mail    mail
news    news
uucp    uucp
proxy    proxy
www-data    www-data
backup    backup
list    Mailing List Manager
irc    ircd
gnats    Gnats Bug-Reporting System (admin)
nobody    nobody
libuuid    
syslog    
messagebus    
usbmux    usbmux daemon
dnsmasq    dnsmasq
avahi-autoipd    Avahi autoip daemon
kernoops    Kernel Oops Tracking Daemon
rtkit    RealtimeKit
saned    
whoopsie    
speech-dispatcher    Speech Dispatcher
avahi    Avahi mDNS daemon
lightdm    Light Display Manager
colord    colord colour management daemon
hplip    HPLIP system user
pulse    PulseAudio daemon
wawab    wawab
usermetrics    User Metrics
guest-lk6zWM    Guest
guest-X5i6dc    Guest
Devices

Processor
Processors
Intel(R) Celeron(R) 2955U @ 1.40GHz    800.00MHz
Intel(R) Celeron(R) 2955U @ 1.40GHz    1400.00MHz
Memory
Memory
Total Memory    3944252 kB
Free Memory    1909124 kB
Buffers    77436 kB
Cached    1088428 kB
Cached Swap    0 kB
Active    1042768 kB
Inactive    885824 kB
Active(anon)    766252 kB
Inactive(anon)    396076 kB
Active(file)    276516 kB
Inactive(file)    489748 kB
Unevictable    32 kB
Mlocked    32 kB
High Memory    3089600 kB
Free High Memory    1431840 kB
Low Memory    854652 kB
Free Low Memory    477284 kB
Virtual Memory    4000764 kB
Free Virtual Memory    4000764 kB
Dirty    1464 kB
Writeback    0 kB
AnonPages    762788 kB
Mapped    297756 kB
Shmem    399604 kB
Slab    57608 kB
SReclaimable    34732 kB
SUnreclaim    22876 kB
KernelStack    4856 kB
PageTables    14636 kB
NFS_Unstable    0 kB
Bounce    0 kB
WritebackTmp    0 kB
CommitLimit    5972888 kB
Committed_AS    5738504 kB
VmallocTotal    122880 kB
VmallocUsed    19248 kB
VmallocChunk    97052 kB
HardwareCorrupted    0 kB
AnonHugePages    333824 kB
HugePages_Total    0
HugePages_Free    0
HugePages_Rsvd    0
HugePages_Surp    0
Hugepagesize    2048 kB
DirectMap4k    40952 kB
DirectMap2M    872448 kB
PCI Devices
PCI Devices
Host bridge    Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
VGA compatible controller    Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b) (prog-if 00 [VGA controller])
Audio device    Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
USB controller    Intel Corporation Lynx Point-LP USB xHCI HC (rev 04) (prog-if 30 [XHCI])
Communication controller    Intel Corporation Lynx Point-LP HECI #0 (rev 04)
Audio device    Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
PCI bridge    Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4) (prog-if 00 [Normal decode])
PCI bridge    Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4) (prog-if 00 [Normal decode])
PCI bridge    Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4) (prog-if 00 [Normal decode])
USB controller    Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04) (prog-if 20 [EHCI])
ISA bridge    Intel Corporation Lynx Point-LP LPC Controller (rev 04)
SATA controller    Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
SMBus    Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
Network controller    Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
USB Devices
Printers
Printers
No printers found    
Battery
Battery: BAT0
State    discharging (load: 0 mA)
Capacity    2109 mAh / 2500 mAh (84.36%)
Battery Technology    rechargeable (LION)
Model Number    AL12A32
Serial Number    16507
Sensors
Input Devices
Input Devices
Lid Switch    
Sleep Button    
Power Button    
AT Translated Set 2 keyboard    
USB PnP Sound Device    
ETPS/2 Elantech Touchpad    
HD WebCam    
Video Bus    
HDA Intel HDMI HDMI/DP,pcm    8=
HDA Intel HDMI HDMI/DP,pcm    7=
HDA Intel HDMI HDMI/DP,pcm    3=
HDA Intel PCH Headphone    
Acer WMI hotkeys    
Acer BMA150 accelerometer    
PixArt USB Optical Mouse    
Storage
SCSI Disks
ATA WDC WD7500BPVX-2    
HL-DT-ST DVDRAM GU71N    
DMI
BIOS
Date    08/16/2013
Vendor    Phoenix Technologies Ltd. ([www.phoenix.com]("http://www.phoenix.com"))
Version    V2.04.
Board
Name    EA40_HW
Vendor    Acer ([www.acer.com]("http://www.acer.com"))
Resources
I/O Ports
0000-0cf7    PCI Bus 0000:00
0000-001f    dma1
0020-0021    pic1
0040-0043    timer0
0050-0053    timer1
0060-0060    keyboard
0062-0062    EC data
0064-0064    keyboard
0066-0066    EC cmd
0070-0077    rtc0
0080-008f    dma page reg
00a0-00a1    pic2
00c0-00df    dma2
00f0-00ff    fpu
03c0-03df    vesafb
0cf8-0cff    PCI conf1
0d00-ffff    PCI Bus 0000:00
1800-1803    ACPI PM1a_EVT_BLK
1804-1805    ACPI PM1a_CNT_BLK
1808-180b    ACPI PM_TMR
1810-1815    ACPI CPU throttle
1830-1833    iTCO_wdt
1850-1850    ACPI PM2_CNT_BLK
1854-1857    pnp 00:05
1860-187f    iTCO_wdt
1880-189f    ACPI GPE0_BLK
2000-2fff    PCI Bus 0000:01
3000-3fff    PCI Bus 0000:03
3000-30ff    Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0f)
3000-30ff    RealTek RTL-8169 Gigabit Ethernet driver
4000-403f    Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b) (prog-if 00 [VGA controller])
4060-407f    Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
4060-407f    AHCI SATA low-level driver
4080-4087    Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
4080-4087    AHCI SATA low-level driver
4088-408f    Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
4088-408f    AHCI SATA low-level driver
4090-4093    Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
4090-4093    AHCI SATA low-level driver
4094-4097    Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
4094-4097    AHCI SATA low-level driver
efa0-efbf    Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
ffff-ffff    pnp 00:03
ffff-ffff    pnp 00:03
ffff-ffff    pnp 00:03
Memory
00000000-00000fff    reserved
00001000-0009cfff    System RAM
0009d000-0009ffff    reserved
000a0000-000bffff    PCI Bus 0000:00
000a0000-000bffff    Video RAM area
000c0000-000cebff    Video ROM
000e0000-000fffff    reserved
000f0000-000fffff    System ROM
00100000-c654afff    System RAM
01000000-01663131    Kernel code
01663132-019b81ff    Kernel data
01a9b000-01b81fff    Kernel bss
c654b000-c674cfff    reserved
c674d000-d512efff    System RAM
d512f000-d6eeefff    reserved
d6eef000-d6f9efff    ACPI Non-volatile Storage
d6f9f000-d6ffefff    ACPI Tables
d6fff000-d6ffffff    System RAM
d7000000-df9fffff    reserved
d7a00000-df9fffff    Graphics Stolen Memory
dfa00000-feafffff    PCI Bus 0000:00
dfa00000-dfa00fff    pnp 00:08
dfb00000-dfcfffff    PCI Bus 0000:01
dfd00000-dfefffff    PCI Bus 0000:01
dff00000-dfffffff    PCI Bus 0000:02
dff00000-dff0ffff    Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
e0000000-efffffff    Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b) (prog-if 00 [VGA controller])
f0000000-f03fffff    Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b) (prog-if 00 [VGA controller])
f0400000-f04fffff    PCI Bus 0000:03
f0400000-f0403fff    Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0f)
f0400000-f0403fff    RealTek RTL-8169 Gigabit Ethernet driver
f0404000-f0404fff    Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0f)
f0404000-f0404fff    RealTek RTL-8169 Gigabit Ethernet driver
f0500000-f05fffff    PCI Bus 0000:03
f0500000-f050ffff    Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
f0500000-f050ffff    Realtek PCI-E Card Reader Driver
f0600000-f06fffff    PCI Bus 0000:02
f0600000-f067ffff    Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
f0600000-f067ffff    Support for Atheros 802.11n wireless LAN cards.
f0700000-f070ffff    Intel Corporation Lynx Point-LP USB xHCI HC (rev 04) (prog-if 30 [XHCI])
f0700000-f070ffff    xhci_hcd
f0710000-f0713fff    Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
f0710000-f0713fff    ICH HD audio
f0714000-f0717fff    Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
f0714000-f0717fff    ICH HD audio
f0718000-f07180ff    Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
f0719000-f071901f    Intel Corporation Lynx Point-LP HECI #0 (rev 04)
f0719000-f071901f    Intel(R) Management Engine Interface
f071c000-f071c7ff    Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
f071c000-f071c7ff    AHCI SATA low-level driver
f071d000-f071d3ff    Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04) (prog-if 20 [EHCI])
f071d000-f071d3ff    ehci_hcd
f8000000-fbffffff    PCI MMCONFIG 0000 [bus 00-3f]
f8000000-fbffffff    reserved
f8000000-fbffffff    pnp 00:08
fe101000-fe112fff    reserved
fe800000-fe80ffff    pnp 00:03
fec00000-fec00fff    reserved
fec00000-fec003ff    IOAPIC 0
fed00000-fed003ff    HPET 0
fed08000-fed08fff    reserved
fed10000-fed19fff    reserved
fed10000-fed17fff    pnp 00:08
fed18000-fed18fff    pnp 00:08
fed19000-fed19fff    pnp 00:08
fed1c000-fed1ffff    reserved
fed1c000-fed1ffff    pnp 00:08
fed1f410-fed1f414    iTCO_wdt
fed20000-fed3ffff    pnp 00:08
fed45000-fed8ffff    pnp 00:08
fed90000-fed93fff    pnp 00:08
fee00000-fee00fff    Local APIC
fee00000-fee00fff    reserved
ffa00000-ffffffff    reserved
100000000-11f5fffff    System RAM
11f600000-11fffffff    RAM buffer
DMA
4    cascade
Network

Interfaces
Network Interfaces
wlan0    4.61MiB    1.53MiB    192.168.254.104
lo    0.16MiB    0.16MiB    127.0.0.1
eth0    0.00MiB    0.00MiB    
IP Connections
Connections
127.0.1.1:53        0.0.0.0:*    udp
127.0.0.1:631    LISTEN    0.0.0.0:*    tcp
192.168.254.104:41721    LISTEN    0.0.0.0:*    tcp
127.0.0.1:41722    LISTEN    0.0.0.0:*    tcp
192.168.254.104:50916    CLOSE_WAIT    91.189.94.41:80    tcp
192.168.254.104:43904    CLOSE_WAIT    91.189.94.25:80    tcp
192.168.254.104:53731    ESTABLISHED    74.125.130.188:5228    tcp
192.168.254.104:52283    TIME_WAIT    202.90.158.94:80    tcp
192.168.254.104:42657    CLOSE_WAIT    91.189.89.31:80    tcp
::1:631    LISTEN    :::*    tcp6
::1:39036    CLOSE_WAIT    ::1:631    tcp6
0.0.0.0:55323        0.0.0.0:*    udp
127.0.1.1:53        0.0.0.0:*    udp
0.0.0.0:68        0.0.0.0:*    udp
0.0.0.0:37999        0.0.0.0:*    udp
0.0.0.0:631        0.0.0.0:*    udp
0.0.0.0:58048        0.0.0.0:*    udp
0.0.0.0:5353        0.0.0.0:*    udp
0.0.0.0:5353        0.0.0.0:*    udp
0.0.0.0:41720        0.0.0.0:*    udp
:::40417        :::*    udp6
:::30422        :::*    udp6
:::5353        :::*    udp6
Routing Table
IP routing table
0.0.0.0 / 192.168.254.254    0.0.0.0    UG    wlan0
192.168.254.0 / 0.0.0.0    255.255.255.0    U    wlan0
ARP Table
ARP Table
192.168.254.102    00:23:15:76:2a:00    wlan0
192.168.254.254    00:26:75:83:54:d2    wlan0
DNS Servers
Name servers
127.0.1.1    
Statistics
IP
9408    Total packets received
0    Incoming packets discarded
0    Incoming packets discarded
9407    Incoming packets delivered
7779    Requests sent out
4    Outgoing packets dropped
ICMP
23    ICMP messages received
0    ICMP messages failed
26    ICMP messages sent
0    ICMP messages failed
ICMPMSG
TCP
359    Active connections openings
100    Passive connection openings
60    Failed connection attempts
35    Connection resets received
1    Connections established
6799    Segments received
6367    Segments send out
62    Segments retransmited
6    Bad segments received.
218    Resets sent
UDP
2011    Packets received
26    Packets to unknown port received.
0    Packet receive errors
1364    Packets sent
UDPLITE
TCPEXT
140    TCP sockets finished time wait in fast timer
150    Delayed acks sent
588    Packets directly queued to recvmsg prequeue.
774376    Bytes directly received in process context from prequeue
2740    Packet headers predicted
583    Packets header predicted and directly queued to user
1406    Acknowledgments not containing data payload received
314    Predicted acknowledgments
4    Fast retransmits
6    Congestion windows recovered without slow start after partial ack
4    Fast retransmits
30    Retransmits in slow start
27    Connections reset due to early user close
1    SACK retransmits failed
10    DSACKs sent for old packets
3    DSACKs sent for out of order packets
8    DSACKs received
55    Connections reset due to unexpected data
27    Connections reset due to early user close
IPEXT
Shared Directories
SAMBA
NFS
Benchmarks

CPU Blowfish
CPU Blowfish
This Machine    800 MHz    12.304
Intel(R) Celeron(R) M processor 1.50GHz    (null)    26.1876862
PowerPC 740/750 (280.00MHz)    (null)    172.816713
CPU CryptoHash
CPU CryptoHash
This Machine    800 MHz    127.981
CPU Fibonacci
CPU Fibonacci
This Machine    800 MHz    2.905
Intel(R) Celeron(R) M processor 1.50GHz    (null)    8.1375674
PowerPC 740/750 (280.00MHz)    (null)    58.07682
CPU N-Queens
CPU N-Queens
This Machine    800 MHz    13.351
FPU FFT
FPU FFT
This Machine    800 MHz    3.618
FPU Raytracing
FPU Raytracing
This Machine    800 MHz    29.849
Intel(R) Celeron(R) M processor 1.50GHz    (null)    40.8816714
PowerPC 740/750 (280.00MHz)    (null)    161.312647
```

---

### Post by jesus-freak on 2014-10-10
Here are the results of the system test in unity.

---

### Post by jesus-freak on 2014-10-10
Did any of this info give anyone any ideas on what is wrong here?

---

### Post by oldfred on 2014-10-10
Please use code tags with long text output. Easy to add with # in advanced editor.

Intermittent issues are the hardest to resolve.

My now old laptop, will go dim if I load too many applications at once. But I know it has limited RAM and if too much is going on at once it starts using swap which is very slow compared to RAM.

When it dims, immediately open a terminal and run top to see if something is consuming all cpu or RAM, q to exit top. I run gnome-panel/fallback and add a icon for system monitor in top panel showing cpu use and can sometimes see when system goes crazy, not sure if possible with any other gui/desktop. You may be also able to run system monitor and immediately switch to it.

---

### Post by jesus-freak on 2014-10-10
I'm sorry about the long text thing, I've never had to post that much text before so I didn't know how to do it.

As for the top thing, I'll try that next time if I can. Sometimes the browser goes dim and freezes up and she has to close it and restart it. Other times it freezes and goes dim but the entire system freezes, not just the browser. Is these cases I can't run anything to see what is happening. And also when you plug in an external monitor the entire system freezes and you can't open a term to run the top. But hopefully I can run that command next time and see what is happening.

---

### Post by oldfred on 2014-10-10
If system seems to totally lockup do not use power switch unless you try this first. Forced shutdown can corrupt system and require a fsck to repair. Be sure to have working live installer to do repairs, if that is the case.

 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by jesus-freak on 2014-10-11
Okay, the browser just crashed while my wife was watching a youtube video and I got the top

```
Tasks: 180 total,   2 running, 178 sleeping,   0 stopped,   0 zombie
%Cpu(s):  7.5 us,  1.6 sy,  0.5 ni, 89.4 id,  1.0 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem:   3944252 total,  3339252 used,   605000 free,   143668 buffers
KiB Swap:  4000764 total,        0 used,  4000764 free.  1181540 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 4565 wawab     20   0 2094244 1.293g  29756 S  25.7 34.4   2:30.74 chrome      
 2414 wawab     20   0   70664  11592   9148 S   6.4  0.3   0:01.24 update-not+ 
 4673 root      25   5    9180   2124   1820 S   6.4  0.1   0:03.76 http        
 4831 wawab     20   0    5428   1352    988 R   6.4  0.0   0:00.01 top         
    1 root      20   0    4444   2484   1464 S   0.0  0.1   0:01.89 init        
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd    
    3 root      20   0       0      0      0 S   0.0  0.0   0:01.12 ksoftirqd/0 
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:+ 
    7 root      20   0       0      0      0 S   0.0  0.0   0:06.79 rcu_sched   
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh      
    9 root      rt   0       0      0      0 S   0.0  0.0   0:00.02 migration/0 
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.11 watchdog/0  
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.11 watchdog/1  
   12 root      rt   0       0      0      0 S   0.0  0.0   0:00.02 migration/1 
   13 root      20   0       0      0      0 S   0.0  0.0   0:01.00 ksoftirqd/1 
   15 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:+ 
   16 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 khelper 
```

And then I restarted the browser and reloaded the exact same video and while working properly this was the top

```
top - 14:31:09 up  5:13,  2 users,  load average: 1.16, 1.05, 1.02
Tasks: 182 total,   2 running, 180 sleeping,   0 stopped,   0 zombie
%Cpu(s):  7.5 us,  1.6 sy,  0.5 ni, 89.3 id,  1.0 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem:   3944252 total,  1859024 used,  2085228 free,    85688 buffers
KiB Swap:  4000764 total,      172 used,  4000592 free.  1008920 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 2063 wawab     20   0  305724  83556  30264 S   6.4  2.1   6:35.41 compiz      
 4673 root      25   5    9180   2124   1820 S   6.4  0.1   0:11.16 http        
 4911 wawab     20   0  614632 105456  57244 S   6.4  2.7   0:05.47 chrome      
 5002 wawab     20   0  377812 118264  34000 S   6.4  3.0   0:06.64 chrome      
 5076 wawab     20   0    5428   1352    988 R   6.4  0.0   0:00.01 top         
    1 root      20   0    4444   2484   1464 S   0.0  0.1   0:01.89 init        
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd    
    3 root      20   0       0      0      0 S   0.0  0.0   0:01.20 ksoftirqd/0 
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:+ 
    7 root      20   0       0      0      0 S   0.0  0.0   0:07.12 rcu_sched   
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh      
    9 root      rt   0       0      0      0 S   0.0  0.0   0:00.02 migration/0 
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.11 watchdog/0  
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.12 watchdog/1  
   12 root      rt   0       0      0      0 S   0.0  0.0   0:00.02 migration/1 
   13 root      20   0       0      0      0 S   0.0  0.0   0:01.06 ksoftirqd/1 
   15 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:+
```

---

### Post by jesus-freak on 2014-10-11
I just noticed that when it is working correctly that the compiz is running and using 2.1% memory but when it crashed, compiz isn't even there and the memory Chrome uses goes from 3.0% up to 34.4%. Could this be compiz crashing causing these problems?

---

### Post by Dennis N on 2014-10-11
> **jesus-freak said:**
> I just noticed that when it is working correctly that the compiz is running and using 2.1% memory but when it crashed, compiz isn't even there and the memory Chrome uses goes from 3.0% up to 34.4%. Could this be compiz crashing causing these problems?

I'm pretty sure your output from top is just the first few rows - you need to scroll down with arrow keys to get the rest. Mine is much longer. So, Compiz may be farther down in the output. I suggest you install and use **htop** instead of **top**. htop is searchable and more usable (and colorful). In htop, press F3 and enter the search term (compiz, for example) F3 again for next match (if any).

I also get occasional crashes from flash player so I wouldn't read to much into that behavior.

---

### Post by oldfred on 2014-10-11
If it is chrome it that not inside wine? And chromium is the Linux version?
Wine can add a level of complexity.

---

### Post by jesus-freak on 2014-10-11
We use the linux version of chrome, it runs in ubuntu without wine or anything. We are not running anything with wine. We tried chromium and firefox and all do the same thing.... Dennis N, my top files are complete and it is beyond occasional crashes. And as I have said before, it's not just the browser. It also happens when we try to use an external monitor.

---

### Post by Dennis N on 2014-10-11
In your top window, it says (2nd window) Tasks=182. I think that the number of current processes, and you should therefore see that many lines. Just now, mine said Tasks=178, and I can use page down through five screens of 36 lines each which is approx = number of tasks. I killed one process and the Tasks immediately decreased by 1 so that seems to confirm that interpretation. Or have I got something wrong about this?

---

### Post by Dennis N on 2014-10-11
> it is beyond occasional crashes.
I would try the computer with other cd based software like Fedora live cd, or Open Suse live cd or even gparted stand alone cd. Let it sit for awhile and see if any crashes occur. That to me (admittedly a non-expert view) would suggest some hardware problem independent of what is running.

---

### Post by jesus-freak on 2014-10-15
Hey, there are some more developments with this issue. It appears that there is some kind of a clitch when it comes to mouse/mouse pad settings that also causes some freezing issues. My wife uses a mouse on her laptop and she also hates how the mouse pad acts when she is typing because she is always accidentally touching the pad and messing up her documents. So I showed her the settings to control the mouse pad (it doesn't have a physical off button). First she selected "Disable while typing" but it never stays on, it might work for a little bit but then it gets turned back on. So then she used the Ubuntu settings to just completely turn off the mouse pad. Again it worked for a little while but then it comes back on. It kind of seems like when ever this happens and she is using her mouse or keyboard it causes some kind of conflict and freezes. I don't know if this is a cause or a symptom of something.> I would try the computer with other cd based software like Fedora live cd, or Open Suse live cd or even gparted stand alone cd. Let it sit for awhile and see if any crashes occur. That to me (admittedly a non-expert view) would suggest some hardware problem independent of what is running.That is actually a good thought!! But instead of running it from a live CD would it be possible to install as dual boot? That way she could really use it long enough to see if all of the weird little problems still exist.

---

### Post by oldfred on 2014-10-15
You can dual boot as many systems as will fit on system. 

With multilple systems I prefer separate data partition so each install can share data without changing user settings that might occur if you try to share a /home.
So I usually use 20 or 25GB for my / (root) and usually keep /home inside / but have large data partition. 

If not Debian based you may need to check UID & GID if using a data partition. Ubuntu users UID of 1000 for first user, some other distributions were using 500.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)


 Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

