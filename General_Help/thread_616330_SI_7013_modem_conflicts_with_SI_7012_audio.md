---
title: "SI 7013 modem conflicts with SI 7012 audio"
date: 2007-11-18
forum: General Help
---

### Post by inoxllor on 2007-11-18
I am having some issues with SOUND on 7.10.

I've notice If I boot to windows XP the sound works perfectly, as It does if I then reboot to Ubuntu. But if I boot to Ubuntu first I usualy get no sound.

If noticed that Ubuntu chooses sometimes the modem speaker as the default soundcard (?)
This may be the source of the problem. 

**lspci** returns this:
> 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 14)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:09.0 CardBus bridge: ENE Technology Inc CB1420 Cardbus Controller (rev 01)
00:09.1 CardBus bridge: ENE Technology Inc CB1420 Cardbus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV18M [GeForce4 488 Go] (rev a2)
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)


**lsmod** returns this:
> 
Module                  Size  Used by
ipv6                  273892  10 
wlan_tkip              13696  1 
wlan_ccmp               9600  1 
af_packet              24840  4 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0 
battery                11012  0 
sbs                    19592  0 
button                  8976  0 
ac                      6148  0 
video                  18060  0 
dock                   10656  0 
container               5504  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_intel8x0m          19084  1 
snd_intel8x0           35484  0 
snd_ac97_codec        101156  2 snd_intel8x0m,snd_intel8x0
ac97_bus                3456  1 snd_ac97_codec
snd_pcm_oss            44800  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                81028  4 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4996  0 
wlan_scan_sta          15104  1 
snd_seq_oss            35328  0 
ath_rate_sample        14208  1 
snd_seq_midi            9728  0 
ath_pci                98336  0 
wlan                  206660  6 wlan_tkip,wlan_ccmp,wlan_scan_sta,ath_rate_sample,ath_pci
snd_rawmidi            26112  1 snd_seq_midi
joydev                 11328  0 
ath_hal               192720  3 ath_rate_sample,ath_pci
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54256  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
irda                  202300  0 
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wbsd                   18056  0 
mmc_core               28420  1 wbsd
crc_ccitt               3072  1 irda
pcmcia                 41388  0 
nvidia               4716468  32 
pcspkr                  4224  0 
snd                    56452  14 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
psmouse                39952  0 
serio_raw               8068  0 
snd_page_alloc         11272  3 snd_intel8x0m,snd_intel8x0,snd_pcm
i2c_sis96x              6404  0 
yenta_socket           27532  3 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
sis_agp                10116  1 
agpgart                35016  2 nvidia,sis_agp
i2c_core               26112  2 nvidia,i2c_sis96x
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  4 
ata_generic             8452  0 
floppy                 60004  0 
pata_sis               15236  3 
libata                125168  2 ata_generic,pata_sis
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
sis900                 24960  0 
mii                     6528  1 sis900
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  4 usbhid,ehci_hcd,ohci_hcd
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

[B]
Is there any way to disable permanently the onboard modem?
[/B] (I cannot do it in the BIOS because there is no option for it)

---

### Post by inoxllor on 2007-11-18
**lshw -C sound** returns:
> 
*-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: AC'97 Sound Controller
       vendor: Silicon Integrated Systems [SiS]
       physical id: 2.7
       bus info: pci@0000:00:02.7
       version: a0
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=173 maxlatency=11 mingnt=52


Does "Unclaimed" mean ubuntu isn't using it as the default soundcard?
Can anyone help?

---

