---
title: "bluetooth keybord"
date: 2007-07-24
forum: General Help
---

### Post by Neo Tom Bombadil on 2007-07-24
HI I have had a logitech MX5000 bluetooth keyboard for some time. when i restart my computer my keyboard dose not type so I have to plug and unplug the USB dongle every time my computer starts up.

After I plug and unplug it everything works fine. Some Gnu/Linux distros I've tried don't have this problem, like slackware. 

I'm using 64bit kubuntu, ubuntu has the same problem. Was wondering if anyone knows the solution off hand. Thanks.:guitar:

---

### Post by bettlebrox on 2007-07-24
sounds like the modules (drivers) for the keyboard or bluetooth aren't being loaded at boot. Can you give the output of  "lsmod"?

---

### Post by Neo Tom Bombadil on 2007-07-24
Module                  Size  Used by
i915                   29056  2
drm                   103464  3 i915
hci_usb                20636  0
rfcomm                 45352  0
l2cap                  28160  5 rfcomm
bluetooth              62468  5 hci_usb,rfcomm,l2cap
ppdev                  11272  0
cpufreq_conservative     9736  0
cpufreq_userspace       6176  0
cpufreq_powersave       3072  0
cpufreq_ondemand       10640  0
cpufreq_stats           8416  0
freq_table              6336  2 cpufreq_ondemand,cpufreq_stats
dev_acpi               17028  0
sony_acpi               7064  0
pcc_acpi               15616  0
tc1100_wmi              9224  0
video                  19080  0
battery                12040  0
ac                      6920  0
dock                   11992  0
button                 10016  0
container               6144  0
sbs                    17856  0
i2c_ec                  6912  1 sbs
asus_acpi              19756  0
backlight               8448  1 asus_acpi
ipv6                  307456  14
lp                     15048  0
fuse                   51888  0
wm8775                  8076  0
cx25840                28176  0
tuner                  67368  0
snd_hda_intel          24224  1
snd_hda_codec         262528  1 snd_hda_intel
snd_pcm_oss            49536  0
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0
xpad                   11272  0
snd_seq_oss            36608  0
snd_seq_midi           11008  0
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             40104  1
parport                43404  3 ppdev,lp,parport_pc
iTCO_wdt               13648  0
iTCO_vendor_support     5636  1 iTCO_wdt
ivtv                  143696  0
psmouse                43536  0
serio_raw               9092  0
i2c_algo_bit            9608  1 ivtv
cx2341x                13828  1 ivtv
tveeprom               19216  1 ivtv
i2c_core               26496  7 i2c_ec,wm8775,cx25840,tuner,ivtv,i2c_algo_bit,tveeprom
shpchp                 37404  0
pci_hotplug            36228  1 shpchp
snd                    68904  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm
af_packet              27020  2
videodev               29824  1 ivtv
v4l2_common            28800  5 cx25840,tuner,ivtv,cx2341x,videodev
v4l1_compat            14980  2 ivtv,videodev
intel_agp              29504  1
pcspkr                  4736  0
evdev                  13056  5
tsdev                  10112  0
joydev                 12928  0
ext3                  143760  1
jbd                    68208  1 ext3
mbcache                11400  1 ext3
usbhid                 29088  0
hid                    34048  1 usbhid
sg                     40616  0
sr_mod                 18980  0
cdrom                  40744  1 sr_mod
sd_mod                 25092  3
generic                 6532  0 [permanent]
ata_piix               18308  2
e1000                 133696  0
floppy                 67944  0
ehci_hcd               37004  0
ata_generic            10628  0
libata                137000  2 ata_piix,ata_generic
scsi_mod              166968  4 sg,sr_mod,sd_mod,libata
uhci_hcd               28320  0
usbcore               154416  6 hci_usb,xpad,usbhid,ehci_hcd,uhci_hcd
thermal                16912  0
processor              34952  1 thermal
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

---

### Post by Neo Tom Bombadil on 2007-07-24
i've tried looking at this thred [http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057) and try the "hcitool scan" command they suggested but that comes up with nothing, also I have looked in the bluetooth button in network connectivity and nothing shows up in there either. :confused: 
kinfo center displays this 

Logitech BT Mini-Receiver

Manufacturer: Logitech
Serial #: 00076142A65B

the vender id class, ect ect.

EDIT: (I'm subscribed to this thread so if anyone has any questions answers or whatever. Please feel free to post because I will get the message)

---

### Post by fiatguy85 on 2007-08-25
I'm having the same issue with a dell bluetooth keyboard and mouse which registers the same Logitech BT Mini-Reciever under lsusb.  Let me know if you have found a solution.

---

### Post by z0mbie on 2007-08-26
**1. Back up the /etc/default/bluetooth file:**
```
sudo cp /etc/default/bluetooth /etc/default/bluetooth.backup
```


**2. Edt the so bluetooth pairs the device at startup:** /etc/default/bluetooth
```
gksudo gedit /etc/default/bluetooth
```


**3. Find this section:**
```
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=0
HIDD_OPTIONS="--master --server"

```

Change **HIDD_ENABLED=0** to **HIDD_ENABLED=1** :

```
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
HIDD_OPTIONS="--master --server"

```

Save and close gedit.


**4. Pair the device:**

```
sudo hidd --search
```

Press the red connect button on your mouse/keyboard (should be located in the back). 

Give it some time, it should say something like "Connected/Connecting" then the MAC address of the device. 

Once you see that, you've paired the device. You can repeat the paring if you have more bluetooth devices.

---

### Post by fiatguy85 on 2007-08-26
Thanks!

---

