---
title: "Sound issues"
date: 2006-11-29
forum: General Help
---

### Post by DougieFresh4U on 2006-11-29
The volume control up where the clock icon is does not respon It has no control with volume. Also question on which volume controls  in the 'open volume control' are the ones that should be working? (pcm, headphone, main, etc.)Also 2 icons appeared on destopscreen that I can not delete (computer & trash) If I right click on them, the move to trash is faded out so Ican't remove. How can I get rid of them?

---

### Post by taurus on 2006-11-29
Have you looked at the alsamixer?

```
alsamixer
```

---

### Post by strabes on 2006-11-29
make sure nothing is muted in alsamixer

---

### Post by DougieFresh4U on 2006-11-29
And what am I supposed to make out of that? Or what am I supposed to see?

---

### Post by taurus on 2006-11-29
You suppose to see the volume controls, my friend.  Use the up arrow key to increase the volume for each one while having music playing to see which one works...

---

### Post by DougieFresh4U on 2006-11-29
oops! some times I am such a dumb ^ss. The first 2 say master and do not do a thing, next 2 say headphone and one up and down works, next 3(3-D) do there thing and last row PCM works.Which one is SUPPOSED to control the volume control in the upper right corner next to clock? Because it is non-functioning

---

### Post by DougieFresh4U on 2006-11-30
14 hours, time to Bump

---

### Post by DougieFresh4U on 2006-11-30
dougie@DougiesToyBox:~$ lsmod
Module                  Size  Used by
binfmt_misc            11784  1 
rfcomm                 38936  0 
hidp                   32000  2 
l2cap                  23300  10 rfcomm,hidp
bluetooth              48996  5 rfcomm,hidp,l2cap
ipv6                  257632  8 
cpufreq_userspace       4372  0 
cpufreq_stats           5892  0 
freq_table              4996  1 cpufreq_stats
cpufreq_powersave       2048  0 
cpufreq_ondemand        6944  0 
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
dm_mod                 60088  3 
md_mod                 78740  0 
lp                     11972  0 
af_packet              21768  2 
tsdev                   8256  0 
snd_intel8x0           33436  1 
snd_ac97_codec         96672  1 snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
usbhid                 42464  0 
snd_pcm_oss            46080  0 
snd_pcm                80520  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          18560  1 snd_pcm_oss
snd_seq_dummy           4100  0 
snd_seq_oss            34304  0 
psmouse                40072  0 
serio_raw               7300  0 
snd_seq_midi            9088  0 
snd_rawmidi            25600  1 snd_seq_midi
pcspkr                  3072  0 
evdev                  10496  1 
snd_seq_midi_event      7808  2 snd_seq_oss,snd_seq_midi
e100                   36484  0 
mii                     6016  1 e100
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23172  2 snd_pcm,snd_seq
snd_seq_device          8972  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36132  1 
parport                37320  2 lp,parport_pc
snd                    55428  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9952  1 snd
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
intel_agp              25116  1 
agpgart                33456  2 intel_agp
shpchp                 40856  0 
pci_hotplug            31284  1 shpchp
i2c_i810                5380  0 
i2c_algo_bit            9480  1 i2c_i810
i2c_core               22288  2 i2c_ec,i2c_algo_bit
floppy                 60676  0 
rtc                    12596  0 
ext3                  138632  1 
jbd                    55700  1 ext3
uhci_hcd               23176  0 
usbcore               130304  3 usbhid,uhci_hcd
ide_generic             1536  0 
ide_cd                 32416  0 
cdrom                  37792  1 ide_cd
ide_disk               17664  3 
piix                   10628  1 
generic                 4868  0 
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
dougie@DougiesToyBox:~$dougie@DougiesToyBox:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
01:07.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
dougie@DougiesToyBox:~$

---

### Post by DougieFresh4U on 2006-12-01
Can I get some help please?

---

