---
title: "menu items are showing behind the application (in Beryl)"
date: 2007-01-06
forum: General Help
---

### Post by mdew on 2007-01-06
Is this a known bug? Because up till now, Beryl has worked fine. (using a Nvidia 5900), the only "fix" I know is using metacity :(

[[IMG]http://img517.imageshack.us/img517/9605/pic1aw6.th.jpg[/IMG]](http://img517.imageshack.us/my.php?image=pic1aw6.jpg)
[[IMG]http://img524.imageshack.us/img524/6388/pic2nx2.th.jpg[/IMG]](http://img524.imageshack.us/my.php?image=pic2nx2.jpg)
[[IMG]http://img514.imageshack.us/img514/7803/pic3fj8.th.jpg[/IMG]](http://img514.imageshack.us/my.php?image=pic3fj8.jpg)
[[IMG]http://img512.imageshack.us/img512/7752/pic4rb4.th.jpg[/IMG]](http://img512.imageshack.us/my.php?image=pic4rb4.jpg)
and even in wine (using filezilla 2.x)
[[IMG]http://img360.imageshack.us/img360/6117/pic6mq5.th.jpg[/IMG]](http://img360.imageshack.us/my.php?image=pic6mq5.jpg)

```

dpkg --list | grep "beryl"
ii  beryl                                      0.1.4~0beryl1                        Compositing window manager, decorator and th
ii  beryl-core                                 0.1.4~0beryl1                        Compositing window manager - Beryl Project
ii  beryl-manager                              0.1.4~0beryl1                        Tray application launcher tool - Beryl Proje
ii  beryl-plugins                              0.1.4~0beryl1                        Collection of plugins for Beryl
ii  beryl-plugins-data                         0.1.4~0beryl1                        Plugins data - Beryl Project
ii  beryl-settings                             0.1.4~0beryl1                        Plugin and configuration tool - Beryl Projec
ii  emerald                                    0.1.4~0beryl1                        Decorator for beryl
ii  emerald-themes                             0.1.4~0beryl1                        Package of themes for Emerald
ii  libberylsettings0                          0.1.4~0beryl1                        Settings library for plugins - Beryl Project
ii  libemeraldengine0                          0.1.4~0beryl1                        Decoration engines for beryl

```
```

Linux mdew-desktop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

Module                  Size  Used by
nls_cp437               6912  1 
isofs                  38076  1 
udf                    89348  0 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
ipv6                  272288  8 
speedstep_lib           5764  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
ext2                   71432  1 
fuse                   43912  0 
lp                     12964  0 
tsdev                   9152  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
bt878                  12472  0 
analog                 12960  0 
af_packet              24584  4 
nvidia               4554836  20 
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
usbhid                 45152  0 
psmouse                41352  0 
serio_raw               8452  0 
gameport               17160  1 analog
tuner                  54828  0 
tvaudio                26012  0 
bttv                  176116  1 bt878
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
evdev                  11392  2 
r1000                  17792  0 
r8169                  32136  0 
i2c_sis96x              6660  0 
floppy                 63044  0 
video_buf              27652  1 bttv
ir_common              28548  1 bttv
compat_ioctl32          2432  1 bttv
i2c_algo_bit           10376  1 bttv
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
v4l2_common            17280  2 tuner,bttv
btcx_risc               6280  1 bttv
sis900                 25856  0 
pcspkr                  4352  0 
tveeprom               16144  1 bttv
sis_agp                 9860  1 
agpgart                34888  2 nvidia,sis_agp
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
mii                     6912  1 sis900
videodev               10752  1 bttv
i2c_core               23424  8 i2c_ec,nvidia,tuner,tvaudio,bttv,i2c_sis96x,i2c_algo_bit,tveeprom
xfs                   621272  1 
ehci_hcd               34696  0 
ohci_hcd               22532  0 
usbcore               134912  4 usbhid,ehci_hcd,ohci_hcd
ide_generic             2432  0 
ide_cd                 33696  1 
cdrom                  38944  1 ide_cd
ide_disk               18560  4 
sis5513                15368  1 
generic                 6276  0 
thermal                15624  0 
processor              31560  1 thermal
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

---

