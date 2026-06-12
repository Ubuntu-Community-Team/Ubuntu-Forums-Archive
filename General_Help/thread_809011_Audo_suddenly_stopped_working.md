---
title: "Audo suddenly stopped working"
date: 2008-05-27
forum: General Help
---

### Post by bpont on 2008-05-27
My audio was working fine for a long time and suddenly stopped working.  I rebooted several times, went through the ubuntu audio troubleshooting guide, ubuntu irc and even this forum on a previous post that didn't turn up anything.  I am trying to avoid a reinstall for multiple reasons.  I don't really think this should be an unsolvable problem for the ubuntu community, however, I'm stumped.

One thing I remember is that ktorrent was running when the audio disappeared.  Ktorrent blocked my audio in the past, but was resolved by shutting down ktorrent or, at worst, rebooted.  I'm not sure if ktorrent is the culprit here, but thought I should mention it.

Here is the output of lsmod

```
Module                  Size  Used by
snd_opl3_synth         14852  0 
snd_seq_midi_emul       7552  1 snd_opl3_synth
nls_cp437               6656  1 
isofs                  36388  1 
udf                    88612  0 
r128                   41344  2 
drm                    82580  3 r128
binfmt_misc            12808  1 
af_packet              23812  2 
ppdev                  10372  0 
ipv6                  267780  12 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
container               5632  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
snd_cmipci             38528  2 
gameport               16008  1 snd_cmipci
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  2 snd_pcm_oss
snd_pcm                78596  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           12928  2 snd_opl3_synth,snd_cmipci
snd_hwdep              10500  1 snd_opl3_lib
snd_mpu401_uart         9728  1 snd_cmipci
snd_seq_dummy           4868  0 
evdev                  13056  3 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
psmouse                40336  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  8 snd_opl3_synth,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9612  7 snd_opl3_synth,snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
snd                    56996  16 snd_opl3_synth,snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  2 snd
pcspkr                  4224  0 
i2c_piix4               9612  0 
i2c_core               24832  1 i2c_piix4
intel_agp              25492  1 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 drm,intel_agp
ext3                  136712  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
usbhid                 31872  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
hid                    38784  1 usbhid
sd_mod                 30720  6 
pata_acpi               8320  0 
ata_generic             8324  0 
ata_piix               19588  1 
pata_pdc2027x          12676  5 
uhci_hcd               27024  0 
libata                159344  4 pata_acpi,ata_generic,ata_piix,pata_pdc2027x
8139cp                 24704  0 
8139too                27520  0 
mii                     6400  2 8139cp,8139too
usbcore               146028  3 usbhid,uhci_hcd
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
dm_mirror              24832  0 
dm_snapshot            19620  0 
dm_mod                 62660  5 dm_mirror,dm_snapshot
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```

Hope someone can help...

---

### Post by kesman on 2008-05-27
Are you sure that none audio channel is muted? Open up alsamixer in terminal, use TAB to set all channels visible and browse trough them and use M to mute/unmute a channel. My PCM was suddenly muted once and I spent hours searching for the reason for not getting sound at all :P

---

### Post by bpont on 2008-05-27
> **kesman said:**
> Are you sure that none audio channel is muted? Open up alsamixer in terminal, use TAB to set all channels visible and browse trough them and use M to mute/unmute a channel. My PCM was suddenly muted once and I spent hours searching for the reason for not getting sound at all :P

Absolutely nothing is muted.

---

