---
title: "Mouse hanging up"
date: 2008-01-29
forum: General Help
---

### Post by tszanon on 2008-01-29
It's a rare problem, but it's kind of annoying. Out of nothing, my USB mouse stops working. The pointer is still there, where it was, but I can't move it with the mouse. I have to unplug and re-plug the mouse for it to work again.

I was thinking: is there any way to "restart" the mouse? Something that would work like unmounting/remounting an USB flash drive. It would help a lot, since the mouse is plugged in a usb port in the back of the computer, which is under the table. :)

---

### Post by tszanon on 2008-01-30
24h bump...[SIZE="1"]well, not exactly 24h, but close[/SIZE]. Anyone?

---

### Post by tszanon on 2008-01-31
48h (and last) bump. Does anyone know how to restart the mouse? I was thinking about restarting whatever is related to the mouse, but I don't even know what is related...

---

### Post by kesman on 2008-01-31
keep bumping :D

No seriously, when you have your mouse plugged, check out lsmod to see what module is used by the mouse. Then when your mouse stops working, restart that module somehow, I cannot remember the command for that right now since I'm at work with some ***ng windows station :F

---

### Post by happyhamster on 2008-01-31
[edit: sorry wrong thread !?!]

---

### Post by happyhamster on 2008-01-31
Ok, can you show the output of this command:

lspci

I once had a similar problem (on a pc with a VIA chipset). It went away when booting with the "irqpoll" option. What you could also check is if the mouse still locks when disabling stuff like screensavers, powersaving features, etc. Do you also use an usb keyboard BTW?

---

### Post by tszanon on 2008-01-31
> **kesman said:**
> keep bumping :D

No seriously, when you have your mouse plugged, check out lsmod to see what module is used by the mouse. Then when your mouse stops working, restart that module somehow, I cannot remember the command for that right now since I'm at work with some ***ng windows station :F
Thanks. I'll check it later at home.

> **happyhamster said:**
> Ok, can you show the output of this command:

lspci

I once had a similar problem (on a pc with a VIA chipset). It went away when booting with the "irqpoll" option. What you could also check is if the mouse still locks when disabling stuff like screensavers, powersaving features, etc. Do you also use an usb keyboard BTW?
If I recall correctly, my motherboard uses a VIA chipset...
I guess it only happens after the screensaver goes active, but I'm not sure. And no, my keyboard isn't an USB one.

I'll check both lsmod and lspci when I get home. Thanks!

---

### Post by tszanon on 2008-01-31
Ok, let's see:
lsmod:
```
Module                  Size  Used by
vmnet                  45216  5 
vmmon                 149676  8 
binfmt_misc            14604  1 
rfcomm                 45352  0 
l2cap                  28160  5 rfcomm
bluetooth              62468  4 rfcomm,l2cap
ppdev                  11272  0 
powernow_k8            16480  1 
cpufreq_ondemand       10640  1 
cpufreq_powersave       3072  0 
cpufreq_userspace       6176  0 
cpufreq_conservative     9736  0 
cpufreq_stats           8416  0 
freq_table              6336  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
dev_acpi               17028  0 
tc1100_wmi              9224  0 
pcc_acpi               15616  0 
sony_acpi               7064  0 
container               6144  0 
ac                      6920  0 
battery                12040  0 
dock                   11992  0 
button                 10016  0 
video                  19080  0 
sbs                    17856  0 
i2c_ec                  6912  1 sbs
asus_acpi              19756  0 
backlight               8448  1 asus_acpi
nls_iso8859_1           6528  3 
nls_cp437               8192  3 
vfat                   16256  3 
fat                    58800  1 vfat
nls_utf8                3456  2 
ntfs                  101960  2 
reiserfs              248576  1 
sbp2                   26628  0 
lp                     15048  0 
snd_intel8x0           39080  1 
snd_ac97_codec        117848  1 snd_intel8x0
ac97_bus                3968  1 snd_ac97_codec
snd_pcm_oss            49408  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
nvidia               5659736  32 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               9092  0 
pcspkr                  4736  0 
xpad                   11272  0 
**[COLOR="Red"]psmouse                43536  0 [/COLOR]**
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
parport_pc             40104  1 
parport                43404  3 ppdev,lp,parport_pc
snd                    68904  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         11792  2 snd_intel8x0,snd_pcm
i2c_nforce2             7680  0 
k8temp                  7552  0 
i2c_core               26496  3 i2c_ec,nvidia,i2c_nforce2
ipv6                  307584  81 
tsdev                  10112  0 
evdev                  13056  3 
ext3                  143760  3 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sg                     40616  0 
sd_mod                 25092  19 
ide_cd                 35104  1 
cdrom                  40744  1 ide_cd
ata_generic            10628  0 
usbhid                 29088  1 
hid                    34048  1 usbhid
sata_nv                24196  12 
libata                137000  2 ata_generic,sata_nv
usb_storage            80448  2 
scsi_mod              166968  5 sbp2,sg,sd_mod,libata,usb_storage
libusual               22184  1 usb_storage
floppy                 67944  0 
forcedeth              48776  0 
ohci1394               38088  0 
ohci_hcd               24196  0 
ieee1394              369784  2 sbp2,ohci1394
generic                 6532  0 [permanent]
amd74xx                16944  0 [permanent]
ehci_hcd               37004  0 
usbcore               154416  8 xpad,usbhid,usb_storage,libusual,ohci_hcd,ehci_hcd
raid0                   9600  3 
md_mod                 85148  5 raid0
thermal                16912  0 
processor              34952  2 powernow_k8,thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability
```

lspci:```

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
```

It seems that lsmod just gave me a hint (psmouse) and lspci just didn't help much.
Ok, now I think the module is that "psmouse" (shouldn't it be usbmouse? :))
Does anyone know how do I restart a module (assuming it's possible)?

---

