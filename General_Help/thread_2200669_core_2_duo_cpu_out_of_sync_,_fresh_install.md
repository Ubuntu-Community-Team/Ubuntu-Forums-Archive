---
title: "core 2 duo cpu out of sync , fresh install"
date: 2014-01-20
forum: General Help
---

### Post by atze_rotgans on 2014-01-20
Hi all, 

I just started with a fresh install and upgrade of Lubuntu.
After the install i did not have the performance i expected. 

Its not a very fast pc, but should do fine with this install, i went for the 32bit since the ammount of memory and cpu architecture performs better on a 32bit system.
However after installing i upgraded my old 13.x (i had an older dvd) to 13.10.
Upgrade went just fine, but when finnished my performance changed, and now core 1 is at 2.66ghz and 2 constantly arround 2.00ghz.
I also have windows 7 on my pc, where the cpu is perfectly synced.

How can i change this/get it back to normal, im rather new to the lubuntu universe :) so any help would be appreciated.

Below i have a list of info from the system profiler.

```

Computer

Summary
Computer
Processor     2x Intel(R) Core(TM)2 Duo CPU E6750 @ 2.66GHz
Memory     3084MB (282MB used)
Operating System     Ubuntu 13.10
User Name     atze (Atze)
Date/Time     Mon 20 Jan 2014 18:50:53 CET
Display
Resolution     1680x1050 pixels
OpenGL Renderer     Unknown
X11 Vendor     The X.Org Foundation
Multimedia
Audio Adapter     CA0106 - CA0106
Audio Adapter     HDA-Intel - HDA NVidia
Audio Adapter     USB-Audio - Hercules HD Exchange
Input Devices
Power Button     
Power Button     
Microsoft Microsoft® Nano Transceiver v2.0     
Microsoft Microsoft® Nano Transceiver v2.0     
Microsoft Microsoft® Nano Transceiver v2.0     
USB Keyboard     
USB Keyboard     
HDA NVidia HDMI/DP,pcm     9=
HDA NVidia HDMI/DP,pcm     8=
HDA NVidia HDMI/DP,pcm     7=
HDA NVidia HDMI/DP,pcm     3=
Hercules HD Exchange     
Printers
No printers found     
SCSI Disks
ATA WDC WD2500JS-75N     
TSSTcorp DVD-ROM TS-H353B     
ATA Maxtor 6L160M0     
ATA Hitachi HTS54755     
Operating System
Version
Kernel     Linux 3.11.0-15-generic (i686)
Compiled     #23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013
C Library     Unknown
Default C Compiler     GNU C Compiler version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu9)
Distribution     Ubuntu 13.10
Current Session
Computer Name     atze-PC
User Name     atze (Atze)
Home Directory     /home/atze
Desktop Environment     LXDE (Lubuntu)
Misc
Uptime     2 minutes
Load Average     0.60, 0.30, 0.11
Kernel Modules
Loaded Modules
zram     Compressed RAM Block Device
bnep     Bluetooth BNEP ver 1.3
rfcomm     Bluetooth RFCOMM ver 1.11
bluetooth     Bluetooth Core ver 2.16
nvidia     
coretemp     Intel Core temperature monitor
kvm     
ppdev     
dcdbas     Dell Systems Management Base Driver (version 5.6.0-3.2)
joydev     Joystick device interfaces
uvcvideo     USB Video Class driver
videobuf2_vmalloc     vmalloc memory handling routines for videobuf2
videobuf2_memops     common memory handling routines for videobuf2
snd_usb_audio     USB Audio
videobuf2_core     Driver helper framework for Video for Linux 2
videodev     Device registrar for Video4Linux drivers v2
snd_usbmidi_lib     USB Audio/MIDI helper module
snd_hda_codec_hdmi     HDMI HD-audio codec
snd_hda_intel     Intel HDA driver
microcode     Microcode Update Driver
snd_hda_codec     HDA codec core
snd_hwdep     Hardware dependent layer
snd_ca0106     CA0106
snd_ac97_codec     Universal interface for Audio Codec '97
psmouse     PS/2 mouse driver
serio_raw     Raw serio driver
ac97_bus     
snd_seq_midi     Advanced Linux Sound Architecture sequencer MIDI synth.
snd_seq_midi_event     MIDI byte <-> sequencer event coder
snd_seq     Advanced Linux Sound Architecture sequencer.
snd_rawmidi     Midlevel RawMidi code for ALSA.
snd_pcm     Midlevel PCM code for ALSA.
snd_page_alloc     Memory allocator for ALSA system.
snd_seq_device     ALSA sequencer device management
lpc_ich     LPC interface for Intel ICH
snd_timer     ALSA timer interface
snd     Advanced Linux Sound Architecture driver for soundcards.
drm     DRM shared core routines
soundcore     Core sound module
parport_pc     PC-style parallel port driver
mac_hid     
mei_me     Intel(R) Management Engine Interface
mei     Intel(R) Management Engine Interface
lp     
parport     
hid_generic     HID generic driver
usbhid     USB HID core driver
hid     
ahci     AHCI SATA low-level driver
e1000e     Intel(R) PRO/1000 Network Driver
libahci     Common AHCI SATA low-level routines
ptp     PTP clocks support
pps_core     LinuxPPS support (RFC 2783) - ver. 5.3.6
Boots
Boots
Mon Jan 20 18:48     3..11.0-15-generi|-
Mon Jan 20 18:42     3..11.0-15-generi|-
Mon Jan 20 17:08     3..8.0-35-generic|-
Languages
Available Languages
en_AG     English language locale for Antigua and Barbuda
en_AG.utf8     English language locale for Antigua and Barbuda
en_AU.utf8     English locale for Australia
en_BW.utf8     English locale for Botswana
en_CA.utf8     English locale for Canada
en_DK.utf8     English locale for Denmark
en_GB.utf8     English locale for Britain
en_HK.utf8     English locale for Hong Kong
en_IE.utf8     English locale for Ireland
en_IN     English language locale for India
en_IN.utf8     English language locale for India
en_NG     English locale for Nigeria
en_NG.utf8     English locale for Nigeria
en_NZ.utf8     English locale for New Zealand
en_PH.utf8     English language locale for Philippines
en_SG.utf8     English language locale for Singapore
en_US.utf8     English locale for the USA
en_ZA.utf8     English locale for South Africa
en_ZM     English locale for Zambia
en_ZM.utf8     English locale for Zambia
en_ZW.utf8     English locale for Zimbabwe
Filesystems
Mounted File Systems
/dev/sdb1     /     7.67 % (132.6 GiB of 143.6 GiB)
none     /sys/fs/cgroup     0.00 % (4.0 KiB of 4.0 KiB)
udev     /dev     0.00 % (1.5 GiB of 1.5 GiB)
tmpfs     /run     0.38 % (300.1 MiB of 301.2 MiB)
none     /run/lock     0.00 % (5.0 MiB of 5.0 MiB)
none     /run/shm     0.01 % (1.5 GiB of 1.5 GiB)
none     /run/user     0.02 % (100.0 MiB of 100.0 MiB)
Display
Display
Resolution     1680x1050 pixels
Vendor     The X.Org Foundation
Version     1.14.5
Monitors
Monitor 0     1680x1050 pixels
Extensions
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
NV-CONTROL     
NV-GLX     
RANDR     
RECORD     
RENDER     
SECURITY     
SHAPE     
SYNC     
X-Resource     
XC-MISC     
XFIXES     
XFree86-DGA     
XFree86-VidModeExtension     
XINERAMA     
XINERAMA     
XInputExtension     
XKEYBOARD     
XTEST     
XVideo     
OpenGL
Vendor     Unknown
Renderer     Unknown
Version     Unknown
Direct Rendering     No
Environment Variables
Environment Variables
GNOME_KEYRING_PID     1825
USER     atze
LANGUAGE     en_GB:en
UPSTART_INSTANCE     
XDG_SEAT     seat0
TEXTDOMAIN     im-config
SSH_AGENT_PID     1883
SESSION     Lubuntu
HOME     /home/atze
DESKTOP_SESSION     Lubuntu
XDG_SEAT_PATH     /org/freedesktop/DisplayManager/Seat0
GTK_MODULES     unity-gtk-module
INSTANCE     
DBUS_SESSION_BUS_ADDRESS     unix:abstract=/tmp/dbus-wU1edIk673
GNOME_KEYRING_CONTROL     /run/user/1000/keyring-5MLx0p
UBUNTU_MENUPROXY     1
MANDATORY_PATH     /usr/share/gconf/Lubuntu.mandatory.path
IM_CONFIG_PHASE     1
SESSIONTYPE     lxsession
UPSTART_JOB     lxsession
LOGNAME     atze
DEFAULTS_PATH     /usr/share/gconf/Lubuntu.default.path
XDG_SESSION_ID     c2
PATH     /usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
GDM_LANG     en_GB
XDG_SESSION_PATH     /org/freedesktop/DisplayManager/Session0
XDG_RUNTIME_DIR     /run/user/1000
DISPLAY     :0
LANG     en_GB.UTF-8
XAUTHORITY     /home/atze/.Xauthority
SSH_AUTH_SOCK     /tmp/ssh-XrU5uaP2O5qd/agent.1879
SHELL     /bin/bash
GDMSESSION     Lubuntu
UPSTART_EVENTS     started xsession
TEXTDOMAINDIR     /usr/share/locale/
UPSTART_SESSION     unix:abstract=/com/ubuntu/upstart-session/1000/1827
XDG_VTNR     7
PWD     /home/atze
XDG_CONFIG_DIRS     /etc/xdg/lubuntu:/etc/xdg:/etc/xdg/xdg-Lubuntu:/usr/share/upstart/xdg:/etc/xdg
XDG_DATA_DIRS     /etc/xdg/lubuntu:/usr/local/share:/usr/share:/usr/share/gdm:/var/lib/menu-xdg:/etc/xdg/xdg-Lubuntu:/usr/share/upstart/xdg:/etc/xdg
JOB     dbus
XDG_CURRENT_DESKTOP     LXDE
_LXSESSION_PID     1909
XDG_MENU_PREFIX     lxde-
SAL_USE_VCLPLUGIN     gtk
XDG_CONFIG_HOME     /home/atze/.config
Users
Users
root     root
daemon     daemon
bin     bin
sys     sys
sync     sync
games     games
man     man
lp     lp
mail     mail
news     news
uucp     uucp
proxy     proxy
www-data     www-data
backup     backup
list     Mailing List Manager
irc     ircd
gnats     Gnats Bug-Reporting System (admin)
nobody     nobody
libuuid     
syslog     
messagebus     
usbmux     usbmux daemon
lightdm     Light Display Manager
dnsmasq     dnsmasq
ntp     
whoopsie     
avahi     Avahi mDNS daemon
colord     colord colour management daemon
kernoops     Kernel Oops Tracking Daemon
pulse     PulseAudio daemon
rtkit     RealtimeKit
saned     
hplip     HPLIP system user
atze     Atze
Devices

Processor
Processors
Intel(R) Core(TM)2 Duo CPU E6750 @ 2.66GHz     2667.00MHz
Intel(R) Core(TM)2 Duo CPU E6750 @ 2.66GHz     2000.00MHz
Memory
Memory
Total Memory     3084292 kB
Free Memory     2477672 kB
Buffers     60008 kB
Cached     325940 kB
Cached Swap     0 kB
Active     226720 kB
Inactive     321656 kB
Active(anon)     163528 kB
Inactive(anon)     9116 kB
Active(file)     63192 kB
Inactive(file)     312540 kB
Unevictable     32 kB
Mlocked     32 kB
High Memory     2213892 kB
Free High Memory     1704676 kB
Low Memory     870400 kB
Free Low Memory     772996 kB
Virtual Memory     4667388 kB
Free Virtual Memory     4667388 kB
Dirty     1232 kB
Writeback     0 kB
AnonPages     162608 kB
Mapped     107632 kB
Shmem     10108 kB
Slab     26184 kB
SReclaimable     13208 kB
SUnreclaim     12976 kB
KernelStack     2408 kB
PageTables     3772 kB
NFS_Unstable     0 kB
Bounce     0 kB
WritebackTmp     0 kB
CommitLimit     6209532 kB
Committed_AS     1307376 kB
VmallocTotal     122880 kB
VmallocUsed     50576 kB
VmallocChunk     66036 kB
HardwareCorrupted     0 kB
AnonHugePages     0 kB
HugePages_Total     0
HugePages_Free     0
HugePages_Rsvd     0
HugePages_Surp     0
Hugepagesize     2048 kB
DirectMap4k     32760 kB
DirectMap2M     880640 kB
PCI Devices
PCI Devices
Host bridge     Intel Corporation 82Q35 Express DRAM Controller (rev 02)
PCI bridge     Intel Corporation 82Q35 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
Communication controller     Intel Corporation 82Q35 Express MEI Controller (rev 02)
IDE interface     Intel Corporation 82Q35 Express PT IDER Controller (rev 02) (prog-if 85 [Master SecO PriO])
Serial controller     Intel Corporation 82Q35 Express Serial KT Controller (rev 02) (prog-if 02 [16550])
Ethernet controller     Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
USB controller     Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
USB controller     Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
USB controller     Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
PCI bridge     Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
USB controller     Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
USB controller     Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
USB controller     Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
USB controller     Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
PCI bridge     Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
ISA bridge     Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
SATA controller     Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
SMBus     Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
VGA compatible controller     NVIDIA Corporation GT218 [GeForce 210] (rev a2) (prog-if 00 [VGA controller])
Audio device     NVIDIA Corporation High Definition Audio Controller (rev a1)
Multimedia audio controller     Creative Labs CA0106 Soundblaster
USB Devices
Printers
Printers
No printers found     
Battery
No batteries
No batteries found on this system     
Sensors
Cooling Fans
Temperatures
Voltage Values
Input Devices
Input Devices
Power Button     
Power Button     
Microsoft Microsoft® Nano Transceiver v2.0     
Microsoft Microsoft® Nano Transceiver v2.0     
Microsoft Microsoft® Nano Transceiver v2.0     
USB Keyboard     
USB Keyboard     
HDA NVidia HDMI/DP,pcm     9=
HDA NVidia HDMI/DP,pcm     8=
HDA NVidia HDMI/DP,pcm     7=
HDA NVidia HDMI/DP,pcm     3=
Hercules HD Exchange     
Storage
SCSI Disks
ATA WDC WD2500JS-75N     
TSSTcorp DVD-ROM TS-H353B     
ATA Maxtor 6L160M0     
ATA Hitachi HTS54755     
DMI
BIOS
Date     05/31/2011
Vendor     Dell Inc. (Dell Computer, www.dell.com)
Version     A19
Board
Name     0GM819
Vendor     Dell Inc. (Dell Computer, www.dell.com)
Resources
I/O Ports
0000-0cf7     PCI Bus 0000:00
0000-001f     dma1
0020-0021     pic1
0040-0043     timer0
0050-0053     timer1
0060-0060     keyboard
0064-0064     keyboard
0070-007f     rtc0
0080-008f     dma page reg
00a0-00a1     pic2
00c0-00df     dma2
00f0-00ff     fpu
0378-037a     parport0
03c0-03df     vga+
03f8-03ff     serial
0778-077a     parport0
0800-0803     ACPI PM1a_EVT_BLK
0804-0805     ACPI PM1a_CNT_BLK
0808-080b     ACPI PM_TMR
0810-0815     ACPI CPU throttle
0820-082f     ACPI GPE0_BLK
0830-0833     iTCO_wdt
0860-087f     iTCO_wdt
0880-08bf     Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
0c00-0c7f     pnp 00:00
0cf8-0cff     PCI conf1
0d00-ffff     PCI Bus 0000:00
1000-1fff     PCI Bus 0000:02
c000-cfff     PCI Bus 0000:03
cce0-ccff     Creative Labs CA0106 Soundblaster
cce0-ccff     CA0106
d000-dfff     PCI Bus 0000:01
dc80-dcff     NVIDIA Corporation GT218 [GeForce 210] (rev a2) (prog-if 00 [VGA controller])
ec98-ec9f     Intel Corporation 82Q35 Express Serial KT Controller (rev 02) (prog-if 02 [16550])
ec98-ec9f     serial
ecc0-ecdf     Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
ece0-ecff     Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
fe00-fe07     Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
fe00-fe07     AHCI SATA low-level driver
fe10-fe13     Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
fe10-fe13     AHCI SATA low-level driver
fe20-fe27     Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
fe20-fe27     AHCI SATA low-level driver
fe30-fe33     Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
fe30-fe33     AHCI SATA low-level driver
fe80-fe87     Intel Corporation 82Q35 Express PT IDER Controller (rev 02) (prog-if 85 [Master SecO PriO])
fe80-fe87     ata_generic
fe90-fe93     Intel Corporation 82Q35 Express PT IDER Controller (rev 02) (prog-if 85 [Master SecO PriO])
fe90-fe93     ata_generic
fea0-fea7     Intel Corporation 82Q35 Express PT IDER Controller (rev 02) (prog-if 85 [Master SecO PriO])
fea0-fea7     ata_generic
feb0-feb3     Intel Corporation 82Q35 Express PT IDER Controller (rev 02) (prog-if 85 [Master SecO PriO])
feb0-feb3     ata_generic
fec0-fedf     Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
fec0-fedf     AHCI SATA low-level driver
fef0-feff     Intel Corporation 82Q35 Express PT IDER Controller (rev 02) (prog-if 85 [Master SecO PriO])
fef0-feff     ata_generic
ff00-ff1f     Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
ff00-ff1f     uhci_hcd
ff20-ff3f     Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
ff20-ff3f     uhci_hcd
ff40-ff5f     Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
ff40-ff5f     uhci_hcd
ff60-ff7f     Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
ff60-ff7f     uhci_hcd
ff80-ff9f     Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
ff80-ff9f     uhci_hcd
Memory
00000000-00000fff     reserved
00001000-0009e3ff     System RAM
0009e400-0009ffff     RAM buffer
000a0000-000bffff     PCI Bus 0000:00
000a0000-000bffff     Video RAM area
000c0000-000effff     PCI Bus 0000:00
000c0000-000c7fff     Video ROM
000d3000-000d3fff     Adapter ROM
000f0000-000fffff     PCI Bus 0000:00
000f0000-000fffff     reserved
000f0000-000fffff     System ROM
00100000-bedff7ff     System RAM
01000000-01635ee3     Kernel code
01635ee4-01971f7f     Kernel data
01a55000-01b37fff     Kernel bss
bedff800-bee53bff     ACPI Non-volatile Storage
bee53c00-bee55bff     ACPI Tables
bee55c00-dfffffff     reserved
bef00000-dfffffff     PCI Bus 0000:00
c0000000-d1ffffff     PCI Bus 0000:01
c0000000-cfffffff     NVIDIA Corporation GT218 [GeForce 210] (rev a2) (prog-if 00 [VGA controller])
d0000000-d1ffffff     NVIDIA Corporation GT218 [GeForce 210] (rev a2) (prog-if 00 [VGA controller])
e0000000-efffffff     PCI MMCONFIG 0000 [bus 00-ff]
e0000000-efffffff     reserved
f0000000-fed003ff     reserved
f0000000-fec00000     PCI Bus 0000:00
f0000000-f01fffff     PCI Bus 0000:02
f0200000-f02007ff     Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
f0200000-f02007ff     AHCI SATA low-level driver
f0200800-f020080f     Intel Corporation 82Q35 Express MEI Controller (rev 02)
f0200800-f020080f     Intel(R) Management Engine Interface
fcf00000-fcffffff     PCI Bus 0000:02
fd000000-feafffff     PCI Bus 0000:01
fd000000-fdffffff     NVIDIA Corporation GT218 [GeForce 210] (rev a2) (prog-if 00 [VGA controller])
fd000000-fdffffff     nvidia
fe9fc000-fe9fffff     NVIDIA Corporation High Definition Audio Controller (rev a1)
fe9fc000-fe9fffff     ICH HD audio
fea00000-fea7ffff     NVIDIA Corporation GT218 [GeForce 210] (rev a2) (prog-if 00 [VGA controller])
febddb00-febddbff     Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
febddc00-febddfff     Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
febddc00-febddfff     ehci_hcd
febde000-febdefff     Intel Corporation 82Q35 Express Serial KT Controller (rev 02) (prog-if 02 [16550])
febdf000-febdffff     Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
febdf000-febdffff     Intel(R) PRO/1000 Network Driver
febe0000-febfffff     Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
febe0000-febfffff     Intel(R) PRO/1000 Network Driver
fed00000-fed003ff     HPET 0
fed20000-fed9ffff     reserved
fed20000-fed9ffff     PCI Bus 0000:00
fedab410-fedab414     iTCO_wdt
fedad800-fedadfff     PCI Bus 0000:00
fee00000-feefffff     reserved
fee00000-fee00fff     Local APIC
ff97c000-ff97ffff     PCI Bus 0000:00
ff980800-ff980bff     PCI Bus 0000:00
ff980800-ff980bff     Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
ff980800-ff980bff     ehci_hcd
ffb00000-ffffffff     reserved
DMA
4     cascade
Network

Interfaces
Network Interfaces
lo     0.04MiB     0.04MiB     127.0.0.1
eth0     0.06MiB     0.04MiB     192.168.1.46
IP Connections
Connections
    0.0.0.0:*     udp
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
            
::1:123         :::*     udp6
            udp6
            udp6
            udp6
            
Routing Table
IP routing table
0.0.0.0 / 192.168.1.1     0.0.0.0     UG     eth0
192.168.1.0 / 0.0.0.0     255.255.255.0     U     eth0
ARP Table
ARP Table
192.168.1.1     fc:f5:28:15:e0:83     eth0
DNS Servers
Name servers
127.0.1.1     
Statistics
IP
636     Total packets received
0     Incoming packets discarded
0     Incoming packets discarded
634     Incoming packets delivered
657     Requests sent out
80     Outgoing packets dropped
ICMP
160     ICMP messages received
0     ICMP messages failed
168     ICMP messages sent
0     ICMP messages failed
ICMPMSG
TCP
11     Active connections openings
2     Passive connection openings
3     Failed connection attempts
1     Connection resets received
5     Connections established
95     Segments received
110     Segments send out
0     Bad segments received.
0     Bad segments received.
7     Resets sent
UDP
230     Packets received
168     Packets to unknown port received.
0     Packet receive errors
400     Packets sent
UDPLITE
TCPEXT
1     Connections reset due to early user close
4     Delayed acks sent
38     Packet headers predicted
17     Acknowledgments not containing data payload received
5     Predicted acknowledgements
1     Connections reset due to early user close
1     Connections reset due to early user close
1     Connections reset due to early user close
IPEXT
Shared Directories
SAMBA
NFS
Benchmarks

CPU Blowfish
CPU Blowfish
This Machine     2667 MHz     6.300
Intel(R) Celeron(R) M processor 1.50GHz     (null)     26.1876862
PowerPC 740/750 (280.00MHz)     (null)     172.816713
CPU CryptoHash
CPU CryptoHash
This Machine     2667 MHz     207.468
CPU Fibonacci
CPU Fibonacci
This Machine     2667 MHz     3.362
Intel(R) Celeron(R) M processor 1.50GHz     (null)     8.1375674
PowerPC 740/750 (280.00MHz)     (null)     58.07682
CPU N-Queens
CPU N-Queens
This Machine     2667 MHz     7.339
FPU FFT
FPU FFT
This Machine     2667 MHz     2.991
FPU Raytracing
FPU Raytracing
This Machine     2667 MHz     29.950
Intel(R) Celeron(R) M processor 1.50GHz     (null)     40.8816714
PowerPC 740/750 (280.00MHz)     (null)     161.312647
```

---

