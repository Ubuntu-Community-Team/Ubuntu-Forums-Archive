---
title: "No Progress Bars in Gnome"
date: 2006-11-13
forum: General Help
---

### Post by thatkidandy on 2006-11-13
After installing edgy on my old comp I noticed that none of the usual orange progress bars were displayed during an apt install, etc. Instead there is nothing, except when the progress exceededs over 50% where the text would be 'covered' by the bar, it becomes transparent-ish.

Although everything else seems to work fine, this is a minor annoyance that I was wondering if there where any quick fixes/known bugs.

Let me know if you need any additional information, thanks :-D

---

### Post by horace on 2006-11-17
I have the same issue here - it looks as though the progress bar is grey on grey instead of the expected orange. I have one or two other visual peculiarities since going to Edgy, such as flashing orange/red/yellow blobs on screen during boot and shutdown sequences, so guess it may be a graphics card problem. Would be pleased to hear if anyone has this and has fixed it too!

---

### Post by dmglouis on 2006-11-22
I have the exact same problem. Also, whenever I click on the Power button on the top, the default wallpaper turns into some weird shades, and it looks almost like 256 bit graphics. And after the progress bar passes 50%, i have no idea how much time is left, since it gets covered up.

---

### Post by Belfast on 2006-11-25
same here.

lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
00:04.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:04.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:04.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:04.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:06.0 SCSI storage controller: Adaptec AHA-2940U2/U2W / 7890/7891
00:09.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
00:0b.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
00:0c.0 Mass storage controller: Promise Technology, Inc. PDC20268 (Ultra100 TX2) (rev 02)
01:00.0 VGA compatible controller: S3 Inc. 86c368 [Trio 3D/2X] (rev 02)
lsmod
Module                  Size  Used by
nfsd                  234276  13 
exportfs                7296  1 nfsd
lockd                  67848  2 nfsd
sunrpc                165948  8 nfsd,lockd
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
vmnet                  41900  13 
vmmon                 118636  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
af_packet              24584  0 
ext2                   71432  0 
lp                     12964  0 
ipv6                  272288  28 
rt73usb                37888  0 
80211                 175880  1 rt73usb
tsdev                   9152  0 
snd_ens1371            28704  1 
gameport               17160  1 snd_ens1371
snd_ac97_codec         97696  1 snd_ens1371
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_pcm                84612  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          19584  1 snd_pcm_oss
crc_itu_t               3200  1 rt73usb
snd_seq_dummy           4996  0 
sg                     37404  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_rawmidi            27264  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
evdev                  11392  1 
snd_timer              25348  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8452  0 
pcspkr                  4352  0 
psmouse                41352  0 
floppy                 63044  0 
i2c_piix4              10000  0 
snd                    58372  12 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  1 snd
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
3c59x                  47912  0 
mii                     6912  1 3c59x
snd_page_alloc         11400  1 snd_pcm
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
intel_agp              26012  1 
agpgart                34888  1 intel_agp
i2c_core               23424  1 i2c_piix4
ext3                  142728  9 
jbd                    62228  1 ext3
sd_mod                 22656  7 
uhci_hcd               24968  0 
usbcore               134912  3 rt73usb,uhci_hcd
ide_generic             2432  0 
pdc202xx_new           10368  1 
aic7xxx               186324  4 
scsi_transport_spi     27136  1 aic7xxx
scsi_mod              144648  4 sg,sd_mod,aic7xxx,scsi_transport_spi
ide_disk               18560  12 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
piix                   11780  1 
generic                 5764  0 
processor              31560  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

cat /etc/X11/xorg.conf 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "S3 Inc. 86c368 [Trio 3D/2X]"
        Driver          "s3virge"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. 86c368 [Trio 3D/2X]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by JebusWankel on 2006-11-25
I have the same problem. I can't find the thread but I think somebody recognized the problem as not having 24-bit color. I have an i810 intel graphics chip and so did this forum-goer. Anyway, here are my screenshots. This problem doesn't exist in other themes but it does in the default human theme.

---

### Post by markba on 2006-11-26
I just upgraded a system with a Intel 82810 graphical chipset from Dapper to Edgy. In Dapper there was no problem with disappearing progress bars at all while in Edgy there is a problem indeed. 

Also, I have strange artefacts when a configure my toolbar as (partly) transparant. As the toolbars themselves are no part of the theme, the workaround to choose another theme like 'Human' is not applicable.

It looks like this is a generic graphical driver problem in conjunction with Edgy; in Dapper there's no problem.

---

### Post by horace on 2006-11-26
> **markba said:**
> Also, I have strange artefacts when a configure my toolbar as (partly) transparant. As the toolbars themselves are no part of the theme, the workaround to choose another theme like 'Human' is not applicable.

It looks like this is a generic graphical driver problem in conjunction with Edgy; in Dapper there's no problem.

I also had this issue with the transparent panels - but, interestingly, they ***do*** seem to be ok with a different theme. So are both the progress bar and panel displays just a theme problem?

---

### Post by markba on 2006-11-27
> **horace said:**
> ... - but, interestingly, they (panel transparancy and progress bars) ***do*** seem to be ok with a different theme.

Not in my case (see attachment). See artefacts in the bottom panel.

---

### Post by bapoumba on 2006-11-27
There is an unconfirmed bug that looks similar to your problems. You might want to comment in it :
 [https://launchpad.net/distros/ubuntu/+source/human-gtk-theme/+bug/70168]("https://launchpad.net/distros/ubuntu/+source/human-gtk-theme/+bug/70168")

One workaround suggested it to drop to 16 bit high colour (nvidia here, I cannot test, sorry).

---

### Post by DougieFresh4U on 2006-11-27
markba-I have that same graphics card Intel82810 and it is crap and to find driver update is like impossible.

---

### Post by horace on 2006-11-27
> **markba said:**
> Not in my case (see attachment). See artefacts in the bottom panel.
I must have been lucky - the first alternative theme I chose managed the transparent panels ok, but most of them do not. Smoothmilktango and Resilience work for me ......

---

### Post by markba on 2006-11-27
> **bapoumba said:**
> There is an unconfirmed bug that looks similar to your problems. You might want to comment in it :
 [https://launchpad.net/distros/ubuntu/+source/human-gtk-theme/+bug/70168]("https://launchpad.net/distros/ubuntu/+source/human-gtk-theme/+bug/70168")

One workaround suggested it to drop to 16 bit high colour (nvidia here, I cannot test, sorry).

This worked! I changed the DefaultDepth from 24 to 16 in /etc/X11/xorg.conf in the "Screen" section, and a restart of GDM was all that was needed. 
Both the transparancy problem in the panel and the disappearing progress bar is solved.

Note. As horace already pointed out: the transparancy problem is indeed related to theming, some themes have this problem and some don't. In my case, I guess was unlucky in my choice by taking IndustrialTango as the theme of choice.

---

### Post by horace on 2006-11-27
Thanks to bapoumba and markba - reducing the default depth in xorg.conf screen from 24 to 16 does indeed solve both these problems with i810 (transparent panels and progress bars).

---

### Post by gtr225 on 2007-05-14
Changing the depth from 24 to 16 worked for me as well. But is ubuntu planning on fixing this cause now I'm left with 16-bit color where I would preffer full 24-bit color.

---

