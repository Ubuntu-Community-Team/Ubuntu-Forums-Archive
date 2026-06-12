---
title: "I'm only able to use gphoto2 as root in XUbuntu"
date: 2008-06-25
forum: General Help
---

### Post by luisito on 2008-06-25
In my old laptop I have XUbuntu Hardy. When I connect my Cannon SD550 digital camera this is what happens.

If I do lsusb I get
Bus 001 Device 005: ID 04a9:3116 Canon, Inc. Digital IXUS 750 (PTP mode)
Bus 001 Device 001: ID 0000:0000  

Not quite the same but it looks fine. If I try gphoto2 --auto-detect I get
Model                  Port
----------------------------------------------------------
Canon Digital IXUS 750 (PTP mode) usb:  

So far so good. But when I try gphoto2 -P an error shows up
*** Error ***              
An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.
*** Error (-53: 'Could not claim the USB device') ***       

On the other hand, if I try sudo gphoto -P, it works fine. So it seems that there might be a permissions problem. I looked around the forums and I found some suggestions to similar issues involving editing the file "/etc/udev/rules.d/45-libgphoto2.rules" or adding myself to the camera group. So I looked at that in my computer and I found that no such file exists, and there is no camera group.

Before adding that file and/or that group manually and messing up the configuration of my laptop I chose to come here for some advise. gphoto2, libgphoto2-2 and libgphoto2-port0 are installed from the repos. I assume those packages would create any necessary file and/or group. What should I do?

---

### Post by unutbu on 2008-06-25
Please run 

```
groups
```

and post the output. Does 'plugdev' show up in the output? I think that is the group [X?]Ubuntu uses to grant users access to external plugin devices.

---

### Post by luisito on 2008-06-25
Thanks for your reply. If I run groups I get
luis adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev sambashare

plugdev is there indeed. If I try "sudo addgroup luis plugdev" I get
The user `luis' is already a member of `plugdev'.

So I was already there.

---

### Post by unutbu on 2008-06-25
This probably won't work, but just so we don't kick ourselves later, would you please try
```
/usr/bin/gphoto2 --port usb: --get-all-files
```

---

### Post by luisito on 2008-06-25
> **unutbu said:**
> This probably won't work, but just so we don't kick ourselves later, would you please try
```
/usr/bin/gphoto2 --port usb: --get-all-files
```

I get exactly the same result as with gphoto2 -P

---

### Post by unutbu on 2008-06-25
Please post

```
lsmod
```

Take a look at [http://gphoto.sourceforge.net/doc/manual/FAQ.html#FAQ-could-not-claim-USB](http://gphoto.sourceforge.net/doc/manual/FAQ.html#FAQ-could-not-claim-USB)
which has some info about the "Could not claim the USB device" error.

---

### Post by luisito on 2008-06-25
lsmod gives me
```
Module                  Size  Used by
af_packet              24840  2 
r128                   41088  2 
drm                    83348  3 r128
rfcomm                 42136  2 
l2cap                  26112  13 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
ipv6                  273892  10 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
container               5504  0 
button                  8976  0 
sbs                    19592  0 
dock                   10656  0 
battery                11012  0 
video                  18060  0 
iptable_filter          3968  0 
ip_tables              13924  1 iptable_filter
x_tables               16260  1 ip_tables
ac                      6148  0 
lp                     12580  0 
joydev                 11328  0 
snd_maestro3           26628  3 
snd_ac97_codec        100644  1 snd_maestro3
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
pcmcia                 41388  0 
snd_seq_dummy           4740  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
irda                  202300  0 
crc_ccitt               3072  1 irda
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
pcspkr                  4224  0 
psmouse                39952  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw               8068  0 
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  14 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4               9740  0 
soundcore               8800  1 snd
i2c_core               26112  1 i2c_piix4
yenta_socket           27532  2 
rsrc_nonstatic         14080  1 yenta_socket
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  2 drm,intel_agp
pcmcia_core            41108  3 pcmcia,yenta_socket,rsrc_nonstatic
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_generic             8452  0 
floppy                 60004  0 
e100                   37644  0 
mii                     6528  1 e100
uhci_hcd               26640  0 
usbcore               138632  2 uhci_hcd
ata_piix               17540  2 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

I'll check that website now.

---

### Post by dnile on 2008-06-26
hey check out this thread.

[http://ubuntuforums.org/showthread.php?t=784864]("http://ubuntuforums.org/showthread.php?t=784864")

Appears to have a solution for your issue.  Which is also the same issue I am having, just waiting to get on that computer. :cool:

---

### Post by luisito on 2008-06-26
Good call dnile!!! =D> 

The solution from that thread worked. Hopefully it will for you too.

---

