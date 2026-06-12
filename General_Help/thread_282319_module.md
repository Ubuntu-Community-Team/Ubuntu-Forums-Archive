---
title: "module"
date: 2006-10-22
forum: General Help
---

### Post by petervdv on 2006-10-22
Hello all 

lspci says:
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)

this is lsmod:
```
Module                  Size  Used by
binfmt_misc            11784  1 
rfcomm                 38936  0 
hidp                   32000  2 
l2cap                  23300  10 rfcomm,hidp
bluetooth              48996  5 rfcomm,hidp,l2cap
powernow_k8            10888  0 
cpufreq_userspace       4372  0 
cpufreq_stats           5892  0 
freq_table              4996  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2048  0 
cpufreq_ondemand        6944  1 
cpufreq_conservative     7200  0 
video                  16644  0 
tc1100_wmi              7428  0 
sbs                    15776  0 
sony_acpi               5516  0 
pcc_acpi               13184  0 
i2c_ec                  5376  1 sbs
hotkey                 10660  0 
dev_acpi               11140  0 
button                  7056  0 
battery                10756  0 
container               4736  0 
ac                      5892  0 
asus_acpi              16792  0 
nls_utf8                2304  1 
ntfs                  108148  1 
ipv6                  257632  8 
dm_mod                 60088  15 
md_mod                 78740  0 
sr_mod                 17060  0 
sbp2                   23304  0 
lp                     11972  0 
af_packet              21768  2 
snd_ens1371            26272  0 
gameport               15368  1 snd_ens1371
snd_rawmidi            25600  1 snd_ens1371
snd_seq_device          8972  1 snd_rawmidi
snd_ac97_codec         96672  1 snd_ens1371
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm_oss            46080  0 
snd_mixer_oss          18560  1 snd_pcm_oss
snd_pcm                80520  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
tsdev                   8256  0 
snd                    55428  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
pcspkr                  3072  0 
snd_page_alloc         10504  1 snd_pcm
evdev                  10496  1 
parport_pc             36132  1 
parport                37320  2 lp,parport_pc
psmouse                40072  0 
serio_raw               7300  0 
amd64_agp              12228  1 
agpgart                33456  1 amd64_agp
shpchp                 40856  0 
rtc                    12596  0 
floppy                 60676  0 
i2c_nforce2             7296  0 
i2c_core               22288  2 i2c_ec,i2c_nforce2
pci_hotplug            31284  1 shpchp
ext3                  138632  11 
jbd                    55700  1 ext3
ohci1394               35248  0 
ieee1394              302904  2 sbp2,ohci1394
forcedeth              30220  0 
ehci_hcd               32520  0 
ohci_hcd               20740  0 
usbcore               130304  3 ehci_hcd,ohci_hcd
ide_generic             1536  0 
ide_cd                 32416  0 
cdrom                  37792  2 sr_mod,ide_cd
ide_disk               17664  14 
generic                 4868  0 
amd74xx                14364  0 [permanent]
sata_nv                10116  0 
libata                 73228  1 sata_nv
scsi_mod              141320  3 sr_mod,sbp2,libata
thermal                14600  0 
processor              26028  2 powernow_k8,thermal
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

Can someone please tell me what driver am I using for my networkcard?

---

### Post by petervdv on 2006-10-24
anyone please?....

I do have internet, but I'm trying to find out how that's possible without any driver for the onboard nvidia...

---

### Post by po0f on 2006-10-24
petervdv,

It's most likely the **forcedeth** module.

---

