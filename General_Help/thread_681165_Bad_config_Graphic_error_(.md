---
title: "Bad config? Graphic error :("
date: 2008-01-28
forum: General Help
---

### Post by Palyh on 2008-01-28
Hi:
I have Ubuntu 7.10, and my pc is: AMD 1600+ 256 RAM and ATI Radeon 7000.
My problem is this:

[http://img168.imageshack.us/img168/8918/pantallazovj6.png](http://img168.imageshack.us/img168/8918/pantallazovj6.png)

That apear between 5-15 minutes since starts ubuntu :(

Anyone can help me? Thanks

---

### Post by Mikecore on 2008-01-28
please post the output of 

```

sudo lspci

```

and also the output of 
```

sudo lsmod

```

you enter these command in a terminal window.

---

### Post by ~LoKe on 2008-01-28
Does this only happen in Ubuntu?  I had a problem like this which was caused by bad video memory on my video card itself.

---

### Post by Palyh on 2008-01-29
That's happen in windows in a few games with openGL, but it's happens rarely times. (sorry for my english :( )

the output of lspci:
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:07.0 Communication controller: ESS Technology ES2838/2839 SuperLink Modem (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]


The output of lsmod:

Module                  Size  Used by
ipv6                  273892  8 
af_packet              24840  2 
radeon                125472  2 
drm                    83348  3 radeon
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
dock                   10656  0 
ac                      6148  0 
video                  18060  0 
button                  8976  0 
container               5504  0 
sbs                    19592  0 
battery                11012  0 
lp                     12580  0 
snd_via82xx            29336  1 
gameport               16776  1 snd_via82xx
snd_ac97_codec        100644  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9600  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                39952  0 
pcspkr                  4224  0 
serio_raw               8068  0 
i2c_viapro             10004  0 
i2c_core               26112  1 i2c_viapro
snd                    54660  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
via_agp                11264  1 
agpgart                35016  2 drm,via_agp
evdev                  11136  4 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  4 
floppy                 60004  0 
via_rhine              25992  0 
mii                     6528  1 via_rhine
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  3 ehci_hcd,uhci_hcd
via82cxxx              10372  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,via82cxxx
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  1 libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor



Thanks for all.

---

