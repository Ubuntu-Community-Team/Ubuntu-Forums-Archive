---
title: "How to bring esd to work?"
date: 2005-08-03
forum: General Help
---

### Post by fresco on 2005-08-03
Hey guys! 
I did changes to my sound system according to [this](http://www.ubuntuforums.org/showthread.php?t=44753&highlight=happy+sound)  HOWTO. But it didn't work for me so i decided to roll back all the changes by doing this:
rm /etc/asound.conf
rm /etc/alsa/asound.conf
rm /home/yourusername/.asoundrc
apt-get install libesd0

But nothing works. I had to disable sound server startup because applications like totem and xine didn't give any output before I run *killall esd* . Otherwise, apps like Sound Recorder require esd to run. Also I was able to run multiple outputs on esd, now it has problem. Tricky, i must say...  :grin: 

Thank you!

---

### Post by cutOff on 2005-08-03
[QUOTE=fresco]Hey guys! 
I did changes to my sound system according to [this](http://www.ubuntuforums.org/showthread.php?t=44753&highlight=happy+sound)  HOWTO. But it didn't work for me so i decided to roll back all the changes by doing this:
rm /etc/asound.conf
rm /etc/alsa/asound.conf
rm /home/yourusername/.asoundrc
apt-get install libesd0

But nothing works. I had to disable sound server startup because applications like totem and xine didn't give any output before I run *killall esd* . Otherwise, apps like Sound Recorder require esd to run. Also I was able to run multiple outputs on esd, now it has problem. Tricky, i must say...  :grin: 

Thank you![/QUOTE]
Could you tell us what soundcard do you have? and could you paste the output of this commands??

$ lspci
$ lsmod

thanks

---

### Post by fresco on 2005-08-04
Hi there! Thank you for your reply!

Here's lspci output:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:0a.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

Here's lsmod output:

Module                  Size  Used by
isofs                  33720  1
udf                    77060  0
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
snd_via82xx            25248  0
snd_ac97_codec         64608  1 snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xx
af_packet              20744  2
uhci_hcd               30224  0
usbcore               107384  2 uhci_hcd
i2c_viapro              7436  0
i2c_core               21264  1 i2c_viapro
via_ircc               24340  0
irda                  168000  1 via_ircc
crc_ccitt               2176  1 irda
8139cp                 19200  0
8139too                24320  0
mii                     4736  2 8139cp,8139too
snd_ens1370            17888  1
snd_rawmidi            22944  2 snd_mpu401_uart,snd_ens1370
snd_seq_device          8332  1 snd_rawmidi
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  4 snd_via82xx,snd_ac97_codec,snd_ens1370,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  3 snd_via82xx,snd_ens1370,snd_pcm
snd_ak4531_codec        7680  1 snd_ens1370
snd                    50276  11 snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_ens1370,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ak4531_codec
soundcore               9824  2 snd
pci_hotplug            30512  0
via_agp                 9216  1
analog                 10784  0
gameport                4608  3 snd_via82xx,snd_ens1370,analog
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
nls_cp1251              4992  1
nls_cp437               5888  2
vfat                   12928  1
fat                    37792  1 vfat
nls_utf8                2176  1
ntfs                   97136  1
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
evdev                   9088  0
tsdev                   7488  0
nvidia               3923388  12
agpgart                31784  2 via_agp,nvidia
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  1
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
via82cxxx              12956  1
ide_disk               18176  5
ide_core              118988  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   26164  807
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

---

### Post by fresco on 2005-08-05
UP!   
 :grin:

---

### Post by intangible on 2005-08-05
Under **System->Preferences->Multimedia Systems Selctor** does any of those give you sound?  Does any of them work with ESD?

---

### Post by fresco on 2005-08-06
I hear test sound only using either ALSA or OSS. Both ESD and Artsd give "Failed to construct pipeline" messages. Same thing with input.

Here's my /etc/esound/esd.conf

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

By the way, where can I read information about setting parameters to this file?
Don't like when I don't understand what I'm doing.

Thank you,
peace.


------------------------------
Just now checked "Sound server startup" box, launched Totem and it gave me "The device is busy. Is some other process using it?". Ran *killall esd* and playback started without errors.

Don't know what to do...

---

