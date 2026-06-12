---
title: "Sound card priority"
date: 2006-12-15
forum: General Help
---

### Post by lift28 on 2006-12-15
Have 1 last problem to resolve:) I have a htpc i switch over to Ubuntu, this includes a dvb card. I believe that the sound modules for the dvb card is the problem. 

When booting up either the Conexant CX8801 (believed to be the dvb sound modules) or my turtle beach sound card can become the default sound card. The CX8801 wins most of the time. I see both in kmix.

I did find the  /etc/modprobe.d/alsa-base , but have been unable to get the cx8801 line right.

Here is info that might help- if you need more just ask:)

cheri@cheri:~$ cat /proc/asound/devices
  2:        : timer
  3: [ 0- 0]: digital audio capture
  4: [ 0]   : control
  5: [ 1- 2]: digital audio playback
  6: [ 1- 2]: digital audio capture
  7: [ 1- 1]: digital audio playback
  8: [ 1- 0]: digital audio playback
  9: [ 1- 0]: digital audio capture
 10: [ 1- 0]: hardware dependent
 11: [ 1]   : control

cheri@cheri:~$ cat /proc/asound/cards
 0 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xfc000000
 1 [CMI8738MC6     ]: CMI8738-MC6 - C-Media PCI CMI8738-MC6
                      C-Media PCI CMI8738-MC6 (model 55) at 0xb800, irq 169


cheri@cheri:~$ lsmod
Module                  Size  Used by
joydev                 11200  0
rfcomm                 42260  0
nfsd                  234276  13
exportfs                7296  1 nfsd
xt_limit                3840  3
xt_tcpudp               4480  30
iptable_mangle          3968  0
ipt_LOG                 8320  0
ipt_MASQUERADE          4864  0
ip_nat                 19884  1 ipt_MASQUERADE
ipt_TOS                 3456  0
ipt_REJECT              6784  1
ip_conntrack_irc        7920  0
ip_conntrack_ftp        8816  0
xt_state                3328  6
ip_conntrack           53216  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,xt_state
nfnetlink               8216  2 ip_nat,ip_conntrack
iptable_filter          4224  1
ip_tables              15204  2 iptable_mangle,iptable_filter
x_tables               16132  8 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,ip_tables
autofs4                23300  0
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
hidp                   34176  4
l2cap                  27136  18 rfcomm,hidp
lp                     12964  0
cx88_blackbird         21916  0
wm8775                  7180  0
ipv6                  272288  20
nfs                   250316  1
lockd                  67976  3 nfsd,nfs
sunrpc                165948  10 nfsd,nfs,lockd
usbhid                 45152  0
cx25840                24720  0
tsdev                   9152  0
cx88_alsa              15112  1
tda9887                18448  0
snd_cmipci             38304  5
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
nvidia               4717492  22
tuner                  54828  0
cx88_dvb               14596  1
cx8802                 13572  2 cx88_blackbird,cx88_dvb
cx88_vp3054_i2c         5376  1 cx88_dvb
mt352                   7940  1 cx88_dvb
or51132                11396  1 cx88_dvb
video_buf_dvb           7684  1 cx88_dvb
dvb_core               83368  1 video_buf_dvb
gameport               17160  1 snd_cmipci
nxt200x                15364  1 cx88_dvb
zl10353                 6532  1 cx88_dvb
snd_opl3_lib           12288  1 snd_cmipci
snd_hwdep              10756  1 snd_opl3_lib
snd_mpu401_uart        10240  1 snd_cmipci
cx24123                15112  1 cx88_dvb
lgdt330x                9500  1 cx88_dvb
cx22702                 7812  1 cx88_dvb
snd_pcm                84612  4 cx88_alsa,snd_cmipci,snd_pcm_oss
snd_rawmidi            27264  1 snd_mpu401_uart
snd_seq_device          9868  2 snd_opl3_lib,snd_rawmidi
cx8800                 35212  1 cx88_blackbird
cx88xx                 63908  5 cx88_blackbird,cx88_alsa,cx88_dvb,cx8802,cx8800
ivtv                  199184  0
snd_timer              25348  4 snd_opl3_lib,snd_pcm
ir_common              28548  1 cx88xx
dvb_pll                13700  4 cx88_dvb,or51132,nxt200x,cx22702
ati_remote             12680  0
e1000                 128452  0
psmouse                41352  0
v4l2_common            17280  3 cx88_blackbird,tuner,cx8800
compat_ioctl32          2432  1 cx8800
hci_usb                18068  3
i2c_algo_bit           10376  3 cx88_vp3054_i2c,cx88xx,ivtv
bluetooth              53476  6 rfcomm,hidp,l2cap,hci_usb
evdev                  11392  2
snd                    58372  20 cx88_alsa,snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_pcm,snd_rawmidi,snd_seq_device,snd_timer
snd_page_alloc         11400  1 snd_pcm
video_buf              27652  7 cx88_blackbird,cx88_alsa,cx88_dvb,cx8802,video_buf_dvb,cx8800,cx88xx
btcx_risc               6280  4 cx88_alsa,cx8802,cx8800,cx88xx
v4l1_compat            15108  2 cx8800,ivtv
tveeprom               16144  2 cx88xx,ivtv
videodev               10752  4 cx88_blackbird,cx8800,cx88xx,ivtv
soundcore              11232  1 snd
serio_raw               8452  0
parport_pc             37796  1
parport                39496  2 lp,parport_pc
i2c_core               23424  18 i2c_ec,wm8775,cx25840,tda9887,nvidia,tuner,cx88_dvb,mt352,or51132,nxt200x,zl10353,cx24123,lgdt330x,cx22702,cx88xx,ivtv,i2c_algo_bit,tveeprom
floppy                 63044  0
hw_random               7320  0
pcspkr                  4352  0
intel_agp              26012  1
agpgart                34888  2 nvidia,intel_agp
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
ext3                  142728  2
jbd                    62228  1 ext3
ehci_hcd               34696  0
uhci_hcd               24968  0
usbcore               134912  6 usbhid,ati_remote,hci_usb,ehci_hcd,uhci_hcd
ide_generic             2432  0
ata_piix               11780  0
libata                 74892  1 ata_piix
scsi_mod              144648  1 libata
ide_cd                 33696  0
cdrom                  38944  1 ide_cd
ide_disk               18560  5
piix                   11780  1
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
cheri@cheri:~$                                                      


cheri@cheri:~$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 0
2)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02
)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridg
e (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Cont                                 roller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Brid                                 ge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller                                  (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 0                                 2)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (re                                 v a1)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controll                                 er (LOM)
03:01.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio                                  Decoder (rev 05)
03:01.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decode                                 r [Audio Port] (rev 05)
03:01.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decode                                 r [MPEG Port] (rev 05)
03:03.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416)                                  MPEG-2 Encoder (rev 01)
03:04.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
cheri@cheri:~$             cheri@cheri:~$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 0
2)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02
)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridg
e (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Cont                                 roller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Brid                                 ge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller                                  (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 0                                 2)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (re                                 v a1)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controll                                 er (LOM)
03:01.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio                                  Decoder (rev 05)
03:01.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decode                                 r [Audio Port] (rev 05)
03:01.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decode                                 r [MPEG Port] (rev 05)
03:03.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416)                                  MPEG-2 Encoder (rev 01)
03:04.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
 

Thanks for any ideas

---

### Post by superm1 on 2006-12-15
The easiest way in my experience to get modules that fight for order like this to load the way I wanted was via /etc/modules.  So try putting these two modules in /etc/modules and reboot a few times.  (Hopefully) You should have the CMI card default each time around.
```

snd_cmpci
cx8800

```

---

### Post by lift28 on 2006-12-16
Thanks for the response- but that didnt solve it:(. this is a toughy cant remember a problem to stump me for so long in the past 4 yrs.

---

### Post by superm1 on 2006-12-16
> **lift28 said:**
> Thanks for the response- but that didnt solve it:(. this is a toughy cant remember a problem to stump me for so long in the past 4 yrs.
Well the other thing you can try is the root module for your card in /etc/modules instead of just the audio portion.  I'm not sure which is the first one loaded though...

---

### Post by rlx01 on 2006-12-16
If you are using ALSA I believe you can specify the default card in ~/.asoundrc.  I don't do this however since I use mplayer.  When my non-preferred card is not picked by default I explicitly select it with mplayer -ao alsa:device=hw=1,0

---

### Post by lift28 on 2006-12-16
> **superm1 said:**
> Well the other thing you can try is the root module for your card in /etc/modules instead of just the audio portion.  I'm not sure which is the first one loaded though...

The dvb module  is also in thier below the others.
cheri@cheri:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
snd_cmpci
lp
hidp
cx8800
cx88-dvb
ivtv


rlx01-- it is default in my ~/.asoundrc


thanks for the effort guys

---

### Post by hackeron on 2007-08-29
So what's the solution?

---

