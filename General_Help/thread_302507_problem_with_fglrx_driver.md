---
title: "problem with fglrx driver"
date: 2006-11-18
forum: General Help
---

### Post by crowquill on 2006-11-18
ive been trying to get the fglrx driver working, but my os refuses to load them. after going through the setup process several times i decided to manually edit xorg.conf. when i got to the driver section i found this:

> Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	VideoRam	256000
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"900U"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160

yet when i run fglrxinfo in console i get:
> greg@greg-desktop:/etc/X11$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


how can i get these drivers to load??? ](*,)

---

### Post by ndpete on 2006-11-18
I had a similar problem when i installed my driver. I followed the instructions i found from here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") 

You probably just need to add this to the end of your xorg.conf
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```

---

### Post by crowquill on 2006-11-18
ok i tried that, but it didnt seem to change anything. i still have the mesa driver : /

---

### Post by jocko on 2006-11-18
What do you get if you run this in a terminal?
```
cat /var/log/Xorg.0.log | grep EE
```

---

### Post by ouilsen on 2006-11-18
Is your kernel module loaded? Look for the "fglrx" module with "lsmod".

---

### Post by crowquill on 2006-11-18
> **jocko said:**
> What do you get if you run this in a terminal?
```
cat /var/log/Xorg.0.log | grep EE
```

greg@greg-desktop:~$ cat /var/log/Xorg.0.log | grep EE
Current Operating System: Linux greg-desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): Fail to initialize ASIC in kernel.
(EE) fglrx(0): DRIScreenInit failed!
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

---

### Post by crowquill on 2006-11-18
> **ouilsen said:**
> Is your kernel module loaded? Look for the "fglrx" module with "lsmod".

i checked in the package manager and enabled a few more things, but im not quite sure what you mean

---

### Post by Kushkah on 2006-11-18
I was having the same problem but this guide fixed everything for me:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

I needed the troubleshooting steps about the module not loading, and then did the kernel compile part again and it worked, good luck :)

---

### Post by ouilsen on 2006-11-18
Just type "lsmod" in your console. This will list all the kernel modules currently loaded. Check wether "fglrx" is listed. So we know if it is a problem with X or with the kernel module. If not, try to load it with "modprobe fglrx". Then restart X.

---

### Post by crowquill on 2006-11-18
ah, i ran the command and got this:
Module                  Size  Used by
nls_cp437               5888  1
isofs                  37688  1
udf                    88580  0
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
ipv6                  265728  6
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
lp                     11844  0
af_packet              22920  6
irtty_sir               8576  0
sir_dev                19628  1 irtty_sir
tsdev                   8000  0
irda                  187068  2 irtty_sir,sir_dev
crc_ccitt               2304  1 irda
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
floppy                 62148  0
snd_emu10k1_synth       7296  0
snd_emux_synth         37376  1 snd_emu10k1_synth
snd_seq_virmidi         7680  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51984  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
emu10k1_gp              3840  0
snd_emu10k1           117284  1 snd_emu10k1_synth
snd_rawmidi            25504  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
pcspkr                  2180  0
gameport               15496  2 emu10k1_gp
snd_hwdep               9376  2 snd_emux_synth,snd_emu10k1
r818x                  84620  0
ieee80211_rtl          83464  1 r818x
snd_intel8x0           33692  1
snd_ac97_codec         93216  2 snd_emu10k1,snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
psmouse                36100  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
skge                   38672  0
usbhid                 39904  0
serio_raw               7300  0
natsemi                28000  0
snd_pcm                89864  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  3 snd_seq,snd_emu10k1,snd_pcm
rtc                    13492  0
snd                    55268  16 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  3 snd_emu10k1,snd_intel8x0,snd_pcm
intel_agp              22940  1
hw_random               5652  0
agpgart                34888  1 intel_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
evdev                   9856  1
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
uhci_hcd               33808  0
usbcore               130820  4 usbhid,ehci_hcd,uhci_hcd
ata_piix               11012  0
libata                 78992  1 ata_piix
scsi_mod              139496  3 sr_mod,sbp2,libata
ide_cd                 33028  1
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  4
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

---

### Post by crowquill on 2006-11-18
so in otherwords its not there

---

### Post by ouilsen on 2006-11-18
:-) k... so open up the console again and load the module with "modprobe fglrx". If it works, restart X and check fglrxinfo. If not, give us the error message.

---

### Post by jocko on 2006-11-18
> **crowquill said:**
> i checked in the package manager and enabled a few more things, but im not quite sure what you mean


I guess what he means is to see if the fglrx module is in use. Run this in a terminal and see what output you get:
```
lsmod | grep fglrx
```

From these lines in your log it seems like fglrx is loaded but "fail to initialize asic in kernel", whatever that means:
> (EE) fglrx(0): Fail to initialize ASIC in kernel.
(EE) fglrx(0): DRIScreenInit failed!
Hopefully someone will understand these two errors and know how to fix them. The other errors (the missing wacom devices) are nothing to worry about.

---

### Post by crowquill on 2006-11-18
> **ouilsen said:**
> :-) k... so open up the console again and load the module with "modprobe fglrx". If it works, restart X and check fglrxinfo. If not, give us the error message.

FATAL: Module fglrx not found.

---

### Post by jocko on 2006-11-18
> **crowquill said:**
> FATAL: Module fglrx not found.

ok. let's start from the beginning.
Which method did you use to install the drivers?
From the repos?
From ATI/AMD:s website?

---

### Post by ouilsen on 2006-11-18
Have you built your own ati driver before? If not, this is strange.

Either way, method 2 in this guide will make it work [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) .

If this is too much for you, you may try to reinstall the restricted modules package through synaptic.

---

### Post by crowquill on 2006-11-18
well somehow i screwed something very important up and i wasnt able to boot anymore.. i reinstalled and im starting over.

---

### Post by crowquill on 2006-11-18
this sint my first time doing this, ive been switing between distros and i havent had this problem before... usually i get it working fine.

---

