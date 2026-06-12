---
title: "LDCproc problems *PLEASE HELP*"
date: 2007-04-15
forum: General Help
---

### Post by JeepFreak on 2007-04-15
I've probably got a good 20 hours invested into searching alone.  These forums, linuxquestions, venky.ws, google, etc... and I just can not figure this thing out!

The most recent time I installed... I followed the directions [HERE](http://venky.ws/forums/viewtopic.php?t=279), to the letter.  I didn't get a single error (just the same warnings that are posted in that thread).

-The VFD is lit up (whenever there is power to the PSU)
-Running irw works just like it should.
-mode2 doesn't work.
-/dev/lcd0 and /dev/lirc exist and are chmod'd to 666 (after every reboot)
-echo "testing" > /dev/lcd0 returns no errors, but doesn't show anything on the VFD either.
-The whole package works perfectly in Windows 2000.

My lsusb output is this:
```

billy@ubuntu-mythtv:~$ lsusb
Bus 006 Device 002: ID 05e3:070e Genesys Logic, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 062a:0000 Creative Labs 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 001 Device 001: ID 0000:0000 

```

My lsmod output is this:
```

billy@ubuntu-mythtv:~$ lsmod
Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  2 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
xfs                   621272  1 
sbp2                   24584  0 
lp                     12964  0 
ipv6                  272288  21 
wm8775                  7180  0 
cx25840                24720  0 
tda9887                18448  0 
tuner                  54828  0 
v4l2_common            17280  1 tuner
af_packet              24584  2 
nvidia               4554836  12 
ivtv                  199056  0 
i2c_algo_bit           10376  1 ivtv
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
usb_storage            75072  0 
v4l1_compat            15108  1 ivtv
tveeprom               16144  1 ivtv
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
sg                     37404  0 
sr_mod                 18212  0 
i2c_core               23424  9 i2c_ec,wm8775,cx25840,tda9887,tuner,nvidia,ivtv,i2c_algo_bit,tveeprom
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
cdrom                  38944  1 sr_mod
videodev               10752  1 ivtv
libusual               17040  1 usb_storage
pata_marvell            7168  0 
snd_timer              25348  1 snd_pcm
tsdev                   9152  0 
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
usbhid                 45152  0 
lirc_imon              17796  0 
lirc_dev               16500  1 lirc_imon
psmouse                41352  0 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
e1000                 128452  0 
intel_agp              26012  1 
agpgart                34888  2 nvidia,intel_agp
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 42144  0 
serio_raw               8452  0 
hw_random               7320  0 
pci_hotplug            32828  1 shpchp
evdev                  11392  1 
pcspkr                  4352  0 
ext3                  142856  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  7 usb_storage,libusual,usbhid,lirc_imon,ehci_hcd,uhci_hcd
ide_generic             2432  0 
sd_mod                 22656  4 
generic                 6276  0 
ata_piix               11780  3 
libata                 74892  2 pata_marvell,ata_piix
scsi_mod              144648  6 sbp2,usb_storage,sg,sr_mod,sd_mod,libata
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

After running "echo "testing" > /dev/lcd0" my dmesg output is this: 
```

[17179830.764000] /home/billy/lirc/drivers/lirc_imon/lirc_imon.c: VFD port opened
[17179830.820000] /home/billy/lirc/drivers/lirc_imon/lirc_imon.c: VFD port closed

```

Running Ubuntu 6.10 / 2.6.17-11-generic

I would **greatly** appreciate any help!

Thank you!
Billy

---

