---
title: "more sound prob's"
date: 2007-03-02
forum: General Help
---

### Post by skywalker___ on 2007-03-02
hey guys the I have got in irc and in the forum is great  but I'm still having sound issues maybe my on-board sound isn't supported I looked around and it is supported well why isn't it working don't know so I did 
lsmod and I thought I'll post the info here so you guys can look at it and tell me what I have messed up I used linux before redhat and mandrake sndconfig but I am new to deb and I like it alot  soo here it is

t:~$ lsmod
Module                  Size  Used by
binfmt_misc            13448  1 
vboxdrv                34692  0 
apm                    23280  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
ipv6                  272288  8 
lp                     12964  0 
af_packet              24584  2 
tsdev                   9152  0 
snd_opl3_lib           12288  0 
snd_hwdep              10756  1 snd_opl3_lib
snd_cs4231_lib         27520  0 
snd_mpu401_uart        10240  0 
ns558                   6016  0 
snd_cs46xx             89448  0 
snd_ac97_codec         97696  1 snd_cs46xx
snd_ac97_bus            3456  1 snd_ac97_codec
snd_rawmidi            27264  2 snd_mpu401_uart,snd_cs46xx
snd_seq_device          9868  2 snd_opl3_lib,snd_rawmidi
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  4 snd_cs4231_lib,snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
gameport               17160  3 ns558,snd_cs46xx
hostap_pci             59152  0 
hostap                123012  1 hostap_pci
ieee80211_crypt         7552  1 hostap
pcspkr                  4352  0 
floppy                 63044  0 
prism2_pci             74752  0 
evdev                  11392  1 
psmouse                41352  0 
serio_raw               8452  0 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
snd                    58372  12 snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_mpu401_uart,snd_cs46xx,snd_ac97_codec,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
orinoco_pci             8320  0 
orinoco                45076  1 orinoco_pci
hermes                  9472  2 orinoco_pci,orinoco
intel_agp              26012  1 
snd_page_alloc         11400  3 snd_cs4231_lib,snd_cs46xx,snd_pcm
agpgart                34888  1 intel_agp
i2c_piix4              10000  0 
i2c_core               23424  1 i2c_piix4
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142728  1 
jbd                    62228  1 ext3
uhci_hcd               24968  0 
ide_generic             2432  0 
usbcore               134912  2 uhci_hcd
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
piix                   11780  1 
generic                 6276  0 
processor              31560  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

---

### Post by skywalker___ on 2007-03-02
1 when I try to play a audio CD it says this
Error playing CD.
Reason: Could not open resource for writing.

2 when I click on the speaker icon it says's this
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu
Iam very frustrated I never had a problem with sound in Linux before I got it going good for me just no sound Iam not helpless Iam still doing checks in the forum and some tourls

---

### Post by skywalker___ on 2007-03-03
Hey skywalker___ your sound card is not supported:guitar: :guitar: :guitar: :guitar: :guitar:

---

