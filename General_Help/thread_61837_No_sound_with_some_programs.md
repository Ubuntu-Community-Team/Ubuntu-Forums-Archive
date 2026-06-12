---
title: "No sound with some programs"
date: 2005-09-02
forum: General Help
---

### Post by andlinux on 2005-09-02
When I start Ubuntu then I hear a sound (where you need to enter your user name and password) and in some programs (xine, xmms -> when the e-sound output is selected and when I hold the cursor on an mp3 file it starts to play music) i hear sounds and some not (frozen bubble, mplayer, etc.).

lsmod:
```
Module                  Size  Used by
ipv6                  257760  6
speedstep_centrino      7892  1
proc_intf               3908  0
freq_table              4004  1 speedstep_centrino
cpufreq_userspace       4348  1
cpufreq_ondemand        6140  0
cpufreq_powersave       1632  0
pcmcia                 22244  2
fglrx                 261064  7
video                  15972  0
sony_acpi               5928  0
pcc_acpi               11008  0
button                  6480  0
battery                 9988  0
container               4320  0
ac                      4676  0
acerhk                 29604  0
af_packet              21992  4
yenta_socket           21344  0
pcmcia_core            57984  2 pcmcia,yenta_socket
ipw2200               183688  0
firmware_class          9984  1 ipw2200
ieee80211              49604  1 ipw2200
ieee80211_crypt         6376  2 ipw2200,ieee80211
8139cp                 20416  0
8139too                25856  0
mii                     4896  2 8139cp,8139too
ohci1394               34596  0
snd_intel8x0           32352  2
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  1
snd_mixer_oss          19680  1 snd_pcm_oss
snd_pcm                94696  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  2 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm
i2c_i801                8364  0
i2c_core               22320  1 i2c_i801
ehci_hcd               32708  0
uhci_hcd               32816  0
usbcore               119000  3 ehci_hcd,uhci_hcd
shpchp                 99172  0
pci_hotplug            33488  1 shpchp
intel_agp              22140  1
agpgart                33608  2 intel_agp
pcspkr                  3496  0
rtc                    12472  0
md                     47440  0
dm_mod                 59420  1
evdev                   9344  1
joydev                  9664  0
tsdev                   7520  0
capability              4648  0
commoncap               7712  1 capability
sr_mod                 17188  0
sbp2                   23816  0
scsi_mod              127552  2 sr_mod,sbp2
ieee1394              108312  2 ohci1394,sbp2
psmouse                21320  0
mousedev               11288  1
parport_pc             37252  1
lp                     11144  0
parport                36744  2 parport_pc,lp
ide_cd                 41700  0
cdrom                  40220  2 sr_mod,ide_cd
ext3                  137256  1
jbd                    60536  1 ext3
mbcache                 8356  1 ext3
ide_generic             1312  0
piix                   10340  1
ide_disk               20416  3
ide_core              129356  4 ide_cd,ide_generic,piix,ide_disk
unix                   28276  659
thermal                13320  0
processor              22452  2 speedstep_centrino,thermal
fan                     4388  0
fbcon                  37504  71
font                    8192  1 fbcon
bitblit                 5472  1 fbcon
vesafb                  6724  1
cfbcopyarea             3808  1 vesafb
cfbimgblt               2912  1 vesafb
cfbfillrect             3488  1 vesafb
``` 

In the volume control all sliders are at max and nothing is muted.
When I choose file I can change a device (?) in 
Realtek ALC250 rev 2 (OSS Mixer) or
Intel 82801DB-ICH4 (Alsa Mixer)

I have chosen for the ALSA mixer and I tried the OSS mixer also but it is the same.

What can I do so that I hear in all my progs a sound ?

---

### Post by Knyven on 2005-09-02
[QUOTE=andlinux]When I start Ubuntu then I hear a sound (where you need to enter your user name and password) and in some programs (xine, xmms -> when the e-sound output is selected and when I hold the cursor on an mp3 file it starts to play music) i hear sounds and some not (frozen bubble, mplayer, etc.).

lsmod:
```
Module                  Size  Used by
ipv6                  257760  6
speedstep_centrino      7892  1
proc_intf               3908  0
freq_table              4004  1 speedstep_centrino
cpufreq_userspace       4348  1
cpufreq_ondemand        6140  0
cpufreq_powersave       1632  0
pcmcia                 22244  2
fglrx                 261064  7
video                  15972  0
sony_acpi               5928  0
pcc_acpi               11008  0
button                  6480  0
battery                 9988  0
container               4320  0
ac                      4676  0
acerhk                 29604  0
af_packet              21992  4
yenta_socket           21344  0
pcmcia_core            57984  2 pcmcia,yenta_socket
ipw2200               183688  0
firmware_class          9984  1 ipw2200
ieee80211              49604  1 ipw2200
ieee80211_crypt         6376  2 ipw2200,ieee80211
8139cp                 20416  0
8139too                25856  0
mii                     4896  2 8139cp,8139too
ohci1394               34596  0
snd_intel8x0           32352  2
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  1
snd_mixer_oss          19680  1 snd_pcm_oss
snd_pcm                94696  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  2 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm
i2c_i801                8364  0
i2c_core               22320  1 i2c_i801
ehci_hcd               32708  0
uhci_hcd               32816  0
usbcore               119000  3 ehci_hcd,uhci_hcd
shpchp                 99172  0
pci_hotplug            33488  1 shpchp
intel_agp              22140  1
agpgart                33608  2 intel_agp
pcspkr                  3496  0
rtc                    12472  0
md                     47440  0
dm_mod                 59420  1
evdev                   9344  1
joydev                  9664  0
tsdev                   7520  0
capability              4648  0
commoncap               7712  1 capability
sr_mod                 17188  0
sbp2                   23816  0
scsi_mod              127552  2 sr_mod,sbp2
ieee1394              108312  2 ohci1394,sbp2
psmouse                21320  0
mousedev               11288  1
parport_pc             37252  1
lp                     11144  0
parport                36744  2 parport_pc,lp
ide_cd                 41700  0
cdrom                  40220  2 sr_mod,ide_cd
ext3                  137256  1
jbd                    60536  1 ext3
mbcache                 8356  1 ext3
ide_generic             1312  0
piix                   10340  1
ide_disk               20416  3
ide_core              129356  4 ide_cd,ide_generic,piix,ide_disk
unix                   28276  659
thermal                13320  0
processor              22452  2 speedstep_centrino,thermal
fan                     4388  0
fbcon                  37504  71
font                    8192  1 fbcon
bitblit                 5472  1 fbcon
vesafb                  6724  1
cfbcopyarea             3808  1 vesafb
cfbimgblt               2912  1 vesafb
cfbfillrect             3488  1 vesafb
``` 

In the volume control all sliders are at max and nothing is muted.
When I choose file I can change a device (?) in 
Realtek ALC250 rev 2 (OSS Mixer) or
Intel 82801DB-ICH4 (Alsa Mixer)

I have chosen for the ALSA mixer and I tried the OSS mixer also but it is the same.

What can I do so that I hear in all my progs a sound ?[/QUOTE]
 Have you tried disabling/unchecking the sound server at startup?

System>Preferences>Sounds

When i disable it, my XMMS plays mp3 well (usually it freezes) and Games running cedega sound works.

---

### Post by Havoc on 2005-09-02
[QUOTE=Knyven]Have you tried disabling/unchecking the sound server at startup?

System>Preferences>Sounds

When i disable it, my XMMS plays mp3 well (usually it freezes) and Games running cedega sound works.[/QUOTE]
 If your XMMS freezes, then it's because it's using ALSA.Go to preferences and switch to OSS.And yes, you are right.

---

### Post by andlinux on 2005-09-03
[QUOTE=Knyven]Have you tried disabling/unchecking the sound server at startup?

System>Preferences>Sounds

When i disable it, my XMMS plays mp3 well (usually it freezes) and Games running cedega sound works.[/QUOTE]
Thanks, it's working now, I diabled it. :)

I can now use Alsa and OSS with xmms and with Mplayer too, i think all my programs.

---

