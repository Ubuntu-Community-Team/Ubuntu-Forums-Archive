---
title: "Had sound, now don't"
date: 2005-10-21
forum: General Help
---

### Post by coldsalmon on 2005-10-21
Hi,

First off, kudos on a great distro.  That said, I'm having a bizarre problem.  I'm on an Averatec 3700 laptop with an integrated VIA motherboard.  When I first installed Breezy, the sound worked perfectly, but since I mainly use my laptop at school, I kept it muted for about two weeks.  Today, I wanted to use the sound, and it doesn't work!  The volume is not muted, and I tried a variety of media, and nothing has worked.  Here's aplay -l

*** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

here's lsmod

Module                  Size  Used by
vfat                   13440  1
fat                    52668  1 vfat
isofs                  35960  0
nls_utf8                2016  1
udf                    90820  0
rfcomm                 38460  0
l2cap                  24740  5 rfcomm
bluetooth              48356  4 rfcomm,l2cap
powernow_k8            12360  0
cpufreq_powersave       1696  0
cpufreq_stats           5252  0
cpufreq_userspace       4316  1
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
freq_table              4388  2 powernow_k8,cpufreq_stats
pcmcia                 26568  2
tc1100_wmi              6692  0
video                  15748  0
battery                 9348  0
container               4384  0
i2c_acpi_ec             5472  0
button                  6480  0
pcc_acpi               11104  0
sony_acpi               5324  0
ac                      4708  0
dev_acpi               11108  0
hotkey                  9284  0
ipv6                  251200  6
af_packet              21768  4
pcspkr                  3396  0
rtc                    12344  0
snd_via82xx_modem      15492  1
snd_seq_dummy           3620  0
snd_seq_oss            33600  0
snd_seq_midi            9088  0
snd_seq_midi_event      6848  2 snd_seq_oss,snd_seq_midi
snd_seq                50736  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            28576  1
gameport               14824  1 snd_via82xx
snd_ac97_codec         83932  2 snd_via82xx_modem,snd_via82xx
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  4 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  2 snd_seq,snd_pcm
snd_page_alloc         10600  3 snd_via82xx_modem,snd_via82xx,snd_pcm
snd_mpu401_uart         7296  1 snd_via82xx
snd_rawmidi            24704  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8460  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    54884  16 snd_via82xx_modem,snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9600  1 snd
i2c_viapro              7920  0
i2c_core               21200  2 i2c_acpi_ec,i2c_viapro
via_ircc               30292  0
irda                  187612  1 via_ircc
crc_ccitt               1984  1 irda
ohci1394               34356  0
yenta_socket           25292  1
rsrc_nonstatic         13376  1 yenta_socket
pcmcia_core            49348  3 pcmcia,yenta_socket,rsrc_nonstatic
rt2500                175492  1
shpchp                 96996  0
pci_hotplug            27508  1 shpchp
amd64_agp              12232  1
agpgart                34792  1 amd64_agp
nls_cp437               5664  2
ntfs                  108144  1
tsdev                   7776  0
dm_mod                 57692  1
evdev                   9664  0
sr_mod                 17028  0
sbp2                   22952  0
ieee1394              100792  2 ohci1394,sbp2
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  0
lp                     12292  0
parport                35912  2 parport_pc,lp
sd_mod                 19120  2
md                     45584  0
reiserfs              262320  2
thermal                13000  0
processor              22812  2 powernow_k8,thermal
fan                     4484  0
usbhid                 35264  0
usb_storage            74112  2
scsi_mod              135688  4 sr_mod,sbp2,sd_mod,usb_storage
via_rhine              22564  0
mii                     5696  1 via_rhine
ehci_hcd               34248  0
uhci_hcd               31184  0
usbcore               117884  5 usbhid,usb_storage,ehci_hcd,uhci_hcd
ide_cd                 41572  0
cdrom                  39616  2 sr_mod,ide_cd
ide_disk               18464  5
ide_generic             1376  0
via82cxxx              13436  1
ide_core              138772  5 usb_storage,ide_cd,ide_disk,ide_generic,via82cxxx
unix                   26896  405
vesafb                  7992  0
capability              4712  0
commoncap               6816  1 capability
vga16fb                12584  1
vgastate                9664  1 vga16fb
softcursor              2272  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3872  2 vesafb,vga16fb
cfbcopyarea             4608  2 vesafb,vga16fb
fbcon                  38496  72
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon



Thanks guys,

--C

---

### Post by thomax on 2005-10-22
Maybe this works 

sudo kuser

double click on your username > groups > list everything but root (espessialy sound)

ok > ok and you have sound ;)

---

### Post by coldsalmon on 2005-10-24
I blacklisted snd_via82xx_modem, and when I rebooted the sound was working.  After I hibernated, though, it had gone back to just being some low static.  The sound now does not work even if I reboot, just like before.  I have no idea what causes this problem.  The only thing I can do to affect it at all is to toggle the "External Amplifier" switch on the mixer.  When the toggle is on, there is low static at a constant volume level no matter what I do with the rest of the mixer settings.  When the toggle is off, there is silence.

---

### Post by jonjpeterson on 2006-05-15
I am having a similar problem. I had sound and now it's gone. I am new to linux and wonder if you have found any kind of solution. I don't even mind if I have to do some quick terminal code at each reboot. Thanks for any assistance that you may have.

---

### Post by muadib on 2006-05-18
I have sound working perfectly but I am unable to record. I am using Ubuntu Dapper. Please let me know what information you might need to help diagnose your problem.

My lsmod:
[mathieu@ubuntu]~$ lsmod
Module                  Size  Used by
visor                  20108  2
usbserial              33448  5 visor
smbfs                  71736  3
usbhid                 41312  0
isofs                  39232  1
udf                    95876  0
binfmt_misc            13192  1
rfcomm                 44244  0
l2cap                  29184  5 rfcomm
bluetooth              54244  4 rfcomm,l2cap
via                    41344  1
drm                    77972  2 via
ppdev                  10116  0
parport_pc             38340  0
lp                     12612  0
parport                39560  3 ppdev,parport_pc,lp
powernow_k8            14560  0
cpufreq_userspace       6816  1
cpufreq_stats           6912  0
freq_table              5152  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2240  0
cpufreq_ondemand        8104  0
cpufreq_conservative     9256  0
video                  16644  0
tc1100_wmi              7172  0
sony_acpi               5836  0
pcc_acpi               12736  0
hotkey                 11812  0
dev_acpi               11652  0
container               4928  0
button                  6992  0
acpi_sbs               20556  0
battery                10308  1 acpi_sbs
ac                      5508  1 acpi_sbs
i2c_acpi_ec             5440  1 acpi_sbs
ipv6                  287456  34
dm_mod                 63640  1
md_mod                 76244  0
af_packet              25224  2
snd_seq_dummy           4164  0
snd_seq_oss            37696  0
snd_seq_midi            9888  0
snd_seq_midi_event      8064  2 snd_seq_oss,snd_seq_midi
snd_seq                58832  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tsdev                   8320  0
psmouse                40196  0
serio_raw               8132  0
pcmcia                 42108  0
snd_via82xx            31192  3
snd_via82xx_modem      16648  0
gameport               17032  1 snd_via82xx
snd_ac97_codec         98912  2 snd_via82xx,snd_via82xx_modem
snd_ac97_bus            2688  1 snd_ac97_codec
i2c_viapro              9364  0
snd_pcm_oss            56352  0
snd_mixer_oss          20800  1 snd_pcm_oss
i2c_core               23168  2 i2c_acpi_ec,i2c_viapro
via_rhine              25988  0
rtc                    14388  0
via_ircc               32660  0
pcspkr                  2564  0
mii                     6528  1 via_rhine
sdhci                  16320  0
mmc_core               32008  1 sdhci
snd_pcm                96772  5 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart         8896  1 snd_via82xx
irda                  217916  1 via_ircc
snd_timer              27204  2 snd_seq,snd_pcm
yenta_socket           29516  1
rsrc_nonstatic         14784  1 yenta_socket
snd_rawmidi            27552  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9548  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
pcmcia_core            45528  3 pcmcia,yenta_socket,rsrc_nonstatic
crc_ccitt               2496  1 irda
snd                    60068  17 snd_seq_oss,snd_seq,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_timer,snd_rawmidi,snd_seq_device
snd_page_alloc         11592  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              11040  1 snd
rt2500                189348  1
ohci1394               37684  0
ieee1394              307160  1 ohci1394
shpchp                 49376  0
pci_hotplug            30916  1 shpchp
amd64_agp              13252  1
agpgart                37072  2 drm,amd64_agp
evdev                  10432  1
ext3                  148296  1
jbd                    65684  1 ext3
ide_generic             1792  0
ehci_hcd               33800  0
uhci_hcd               35472  0
usbcore               137476  6 visor,usbserial,usbhid,ehci_hcd,uhci_hcd
ide_cd                 36228  1
cdrom                  41504  1 ide_cd
ide_disk               19584  2
via82cxxx               9988  0 [permanent]
generic                 5444  0
thermal                14088  0
processor              26696  2 powernow_k8,thermal
fan                     5124  0
capability              5256  0
commoncap               7616  1 capability
vga16fb                14088  1
vgastate               10304  1 vga16fb
fbcon                  44640  72
tileblit                3072  1 fbcon
font                    8640  1 fbcon
bitblit                 6592  1 fbcon
softcursor              2752  1 bitblit


My kernel:
[mathieu@ubuntu]~$ uname -r
2.6.15-22-k7

Mathieu

---

### Post by [S|G] on 2006-05-19
You could try to reset read/write permissions  to your audio device (should be /dev/dsp or something like that, like /dev/dsp1):
```

sudo chmod g+rw /dev/dsp

```

However, since you're now able to hear sounds, you should check your volume settings using alsamixer (go into  a terminal and type alsamixer). Press [tab] to change to Capture view and make sure your mic or line-in is selected (press space) and turn up its volume (press arrow up).

---

### Post by muadib on 2006-05-19
Hi,
Thank you very much.
I have the sound working now on my Averatec 3700, input and output.
For the recording to work, I had to turn run alsamixer, hit tab, and unmute turn on the capture channel by hitting the space bar.
Mathieu

---

### Post by yurtboy on 2006-06-17
Seems I have to reboot in to windows fully (As noted in another post)
and then reboot back to linux to make it work again.
Funny but 6 years ago on a fujitso laptop same problem.
Maybe this would be good to talk to the developers of the via about?

---

