---
title: "DRI and ATI -&gt; black screen"
date: 2007-01-12
forum: General Help
---

### Post by mjs on 2007-01-12
Hi,

I have a problem with DRI and my ATI RADEON. When I actived the module in xorg.conf the X doesn't start and the screen stay black, I already read read read very much docs in the internet, but none fix it. ](*,) 

Can someone help me? :rolleyes: 

Some informations:

My modules:
```

marcos@zeus:~$ lsmod
Module                  Size  Used by
binfmt_misc            11784  1
rfcomm                 38936  0
hidp                   32000  2
l2cap                  23300  10 rfcomm,hidp
bluetooth              48996  5 rfcomm,hidp,l2cap
video                  16644  0
tc1100_wmi              7428  0
sony_acpi               5516  0
sbs                    15776  0
pcc_acpi               13184  0
i2c_ec                  5376  1 sbs
hotkey                 10660  0
dev_acpi               11140  0
container               4736  0
button                  7056  0
battery                10756  0
asus_acpi              16792  0
ac                      5892  0
af_packet              21768  0
ntfs                  108148  1
nls_utf8                2304  2
nls_cp437               6016  1
vfat                   13440  1
fat                    54556  1 vfat
ext3                  138632  1
jbd                    55700  1 ext3
dm_mod                 60088  8
md_mod                 78740  0
**radeon                117920  1**
drm                    72468  2 radeon
lp                     11972  0
snd_seq_dummy           4100  0
snd_seq_oss            34304  0
snd_seq_midi            9088  0
snd_seq_midi_event      7808  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ipv6                  257632  24
tsdev                   8256  0
usbhid                 42464  0
snd_via82xx            28696  0
gameport               15368  1 snd_via82xx
usblp                  14336  0
spca5xx               635984  0
psmouse                40072  0
snd_mpu401_uart         8704  1 snd_via82xx
videodev                9728  1 spca5xx
via_rhine              23940  0
serio_raw               7300  0
snd_via82xx_modem      15496  0
snd_ac97_codec         96672  2 snd_via82xx,snd_via82xx_modem
snd_ac97_bus            2432  1 snd_ac97_codec
snd_rawmidi            25600  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8972  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
evdev                  10496  1
parport_pc             36132  1
parport                37320  2 lp,parport_pc
pcspkr                  3072  0
floppy                 60676  0
rtc                    12596  0
i2c_viapro              8980  0
snd_pcm_oss            46080  0
snd_mixer_oss          18560  1 snd_pcm_oss
snd_pcm                80520  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  2 snd_seq,snd_pcm
8139cp                 22528  0
8139too                27136  0
mii                     6016  3 via_rhine,8139cp,8139too
i2c_core               22288  2 i2c_ec,i2c_viapro
snd                    55428  12 snd_seq_oss,snd_seq,snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_ac97_codec,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
shpchp                 40856  0
pci_hotplug            31284  1 shpchp
snd_page_alloc         10504  3 snd_via82xx,snd_via82xx_modem,snd_pcm
amd64_agp              12228  1
**agpgart                33456  2 drm,amd64_agp**
xfs                   605556  2
ehci_hcd               32520  0
uhci_hcd               23176  0
usbcore               130304  6 usbhid,usblp,spca5xx,ehci_hcd,uhci_hcd
ide_generic             1536  0
ide_cd                 32416  0
cdrom                  37792  1 ide_cd
ide_disk               17664  8
via82cxxx               9604  0 [permanent]
generic                 5252  0
sata_via                9604  0
libata                 73228  1 sata_via
scsi_mod              141320  1 libata
thermal                14600  0
processor              26028  1 thermal
fan                     5124  0
fbcon                  40480  0
tileblit                2944  1 fbcon
font                    8448  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2432  1 bitblit
vesafb                  8348  0
capability              5000  0
commoncap               7808  1 capability

```

My xorg.conf
```

 17 Section "Files"
 18         FontPath        "/usr/share/X11/fonts/misc"
 19         FontPath        "/usr/share/X11/fonts/cyrillic"
 20         FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
 21         FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
 22         FontPath        "/usr/share/X11/fonts/Type1"
 23         FontPath        "/usr/share/X11/fonts/100dpi"
 24         FontPath        "/usr/share/X11/fonts/75dpi"
 25         FontPath        "/usr/share/fonts/X11/misc"
 26         # path to defoma fonts
 27         FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 28 EndSection
 29
 30 Section "Module"
 31         Load    "bitmap"
 32         Load    "ddc"
 33         Load    "extmod"
 34         Load    "freetype"
 35         Load    "glx"
 36         Load    "dri" # Habilitado para o AIGLX
 37         Load    "dbe" # Habilitado para o AIGLX
 38         Load    "int10"
 39         Load    "type1"
 40         Load    "vbe"
 41 EndSection
 42
 43 Section "InputDevice"
 44         Identifier      "Generic Keyboard"
 45         Driver          "kbd"
 46         Option          "CoreKeyboard"
 47         Option          "XkbRules"      "xorg"
 48         Option          "XkbModel"      "pc104"
 49         Option          "XkbLayout"     "us-intl"
 50 EndSection
 51
 52 Section "InputDevice"
 53         Identifier      "Configured Mouse"
 54         Driver          "mouse"
 55         Option          "CorePointer"
 56         Option          "Device"                "/dev/input/mice"
 57         Option          "Protocol"              "ExplorerPS/2"
 58         Option          "ZAxisMapping"          "4 5"
 59 EndSection
 60
 61 Section "InputDevice"
 62   Driver        "wacom"
 63   Identifier    "stylus"
 64   Option        "Device"        "/dev/wacom"          # Change to
 65                                                       # /dev/input/event
 66                                                       # for USB
 67   Option        "Type"          "stylus"
 68   Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
 69 EndSection
 70
 71 Section "InputDevice"
 72   Driver        "wacom"
 73   Identifier    "eraser"
 74   Option        "Device"        "/dev/wacom"          # Change to
 75                                                       # /dev/input/event
 76                                                       # for USB
 77   Option        "Type"          "eraser"
 78   Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
 79 EndSection
 80
 81 Section "InputDevice"
 82   Driver        "wacom"
 83   Identifier    "cursor"
 84   Option        "Device"        "/dev/wacom"          # Change to
 85                                                       # /dev/input/event
 86                                                       # for USB
 87   Option        "Type"          "cursor"
 88   Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
 89 EndSection
 90
 91 Section "Device"
 92         Identifier      "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
 93         Driver          "ati"
 94         # É obrigatório explicitar o BusID de todas as placas. Para
 95         # obtê-los, use "lspci | grep VGA". Cuidado com os valores,
 96         # pois o endereço fornecido pelo lspci é em base hexadecimal
 97         # e o XOrg espera um valor decimal.  Para a conversão use
 98         # "echo $((0xVALOR_HEXADECIMAL))".
 99         BusID           "PCI:1:0:0"
100         #Option         "UseFBDev"              "true"
101         Option          "XAANoOffscreenPixmaps"
102         Option          "AccelMethod" "EXA"
103         Option          "AGPMode"               "4"
104         VideoRam        64000
105 EndSection
106
107 Section "Monitor"
108         Identifier      "SyncMaster"
109         Option          "DPMS"
110         HorizSync       30-68
111         VertRefresh     50-85
112 EndSection
113
114 Section "Screen"
115         Identifier      "Default Screen"
116         Device          "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
117         Monitor         "SyncMaster"
118         DefaultDepth    24
119         SubSection "Display"
120                 Depth           1
121                 Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
122         EndSubSection
123         SubSection "Display"
124                 Depth           4
125                 Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
126         EndSubSection
127         SubSection "Display"
128                 Depth           8
129                 Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
130         EndSubSection
131         SubSection "Display"
132                 Depth           15
133                 Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
134         EndSubSection
135         SubSection "Display"
136                 Depth           16
137                 Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
138         EndSubSection
139         SubSection "Display"
140                 Depth           24
141                 Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
142         EndSubSection
143 EndSection
144
145 Section "ServerLayout"
146         Identifier      "Default Layout"
147         Screen          "Default Screen"
148         InputDevice     "Generic Keyboard"
149         InputDevice     "Configured Mouse"
150         InputDevice     "stylus" "SendCoreEvents"
151         InputDevice     "cursor" "SendCoreEvents"
152         InputDevice     "eraser" "SendCoreEvents"
153         Option          "AIGLX"         "true"
154 EndSection
155
156 Section "DRI"
157         Mode    0666
158 EndSection
159
160 Section "Extensions"
161         Option "Composite" "Enable"
162 EndSection


```

X.org.log:

```

(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 209
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xf3fff000 is: 0xf3fff000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xec7fec00
(**) RADEON(0): GRPH_BUFFER_CNTL from 20095c5c to 20195c5c
(II) RADEON(0): Direct rendering enabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration enabled for R100 type cards.
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 160
(**) RADEON(0): EngineRestore (32/32)

```

---

### Post by mjs on 2007-01-13
Please,  anybody?

I found this bug [https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/16873](https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/16873).

The xserver-xorg-video-ati and xserver-xorg are in the last versions ( edgy ), early the drapper have the same problem.

I know that my english is too bad, however I want to solve this problem for that I can use the 3D support of my graphic card.

Thanks

---

### Post by rebeldevel on 2007-01-21
I had a similar problem when I tried to install latest (8.33.something) drivers. 8.32 driver (installed manually) works fine. Follow these instructions:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_drivers_in_Ubuntu_Dapper_Manually)

---

