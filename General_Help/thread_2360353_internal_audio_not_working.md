---
title: "internal audio not working"
date: 2017-05-03
forum: General Help
---

### Post by rob141 on 2017-05-03
Hello all ;)

here is the thing, my audio does not work anymore from the internal default audio. It does work if i connect it on HDMI but since i have removed my laptop from this connection bevause i dont need that anymore. I do still need the audio from the laptop though.

I have tried to re-install alsa-base but it says that it it already install.

here is what i have:

```

*****@******:~$ aplay -l && arecord -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of CAPTURE Hardware Devices ****
```



```

****@*****:~$ lsmod
Module                  Size  Used by
btrfs                 987136  0
xor                    24576  1 btrfs
raid6_pq              102400  1 btrfs
ufs                    73728  0
qnx4                   16384  0
hfsplus               106496  0
hfs                    57344  0
minix                  36864  0
ntfs                   98304  0
msdos                  20480  0
jfs                   180224  0
xfs                   970752  0
libcrc32c              16384  1 xfs
cpuid                  16384  0
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  3
ccm                    20480  3
snd_hda_intel          40960  2
arc4                   16384  2
ath9k                 147456  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
uvcvideo               90112  0
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              737280  1 ath9k
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
intel_powerclamp       16384  0
media                  24576  2 uvcvideo,videodev
coretemp               16384  0
kvm_intel             172032  0
kvm                   544768  1 kvm_intel
irqbypass              16384  1 kvm
shpchp                 36864  0
mei_me                 36864  0
joydev                 20480  0
mei                    98304  1 mei_me
lpc_ich                24576  0
input_leds             16384  0
serio_raw              16384  0
mac_hid                16384  0
binfmt_misc            20480  1
snd_hda_codec_hdmi     53248  1
snd_hda_codec         135168  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hda_core           73728  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_timer              32768  1 snd_pcm
snd                    81920  10 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec,snd_hda_intel
soundcore              16384  1 snd
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
uas                    24576  0
usb_storage            69632  2 uas
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  10
i2c_algo_bit           16384  1 radeon
broadcom               20480  0
ttm                    94208  1 radeon
bcm_phy_lib            16384  1 broadcom
drm_kms_helper        155648  1 radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
psmouse               131072  0
drm                   364544  7 ttm,drm_kms_helper,radeon
tg3                   163840  1
ahci                   36864  3
ptp                    20480  1 tg3
libahci                32768  1 ahci
pps_core               20480  1 ptp
wmi                    20480  1 acer_wmi
fjes                   28672  0
video                  40960  1 acer_wmi
```




i think i am missing the default audio device.

how can i have it working again please ?

---

### Post by rob141 on 2017-05-04
Maybe this can help you help me ;)


```

*****@****:~$ pacmd list-sinks
1 sink(s) available.
  * index: 0
	name: <alsa_output.pci-0000_02_00.1.hdmi-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9050
	volume: front-left: 99957 / 153% / 11.00 dB,   front-right: 99957 / 153% / 11.00 dB
	        balance 0.00
	base volume: 65536 / 100% / 0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max request: 0 KiB
	max rewind: 0 KiB
	monitor source: 0
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
	card: 0 <alsa_card.pci-0000_02_00.1>
	module: 6
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "HDMI 0"
		alsa.id = "HDMI 0"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "3"
		alsa.card = "0"
		alsa.card_name = "HDA ATI HDMI"
		alsa.long_card_name = "HDA ATI HDMI at 0xcfedc000 irq 29"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:02:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:02:00.1/sound/card0"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
		device.product.id = "aa60"
		device.product.name = "Redwood HDMI Audio [Radeon HD 5000 Series] (Mobility Radeon HD 5650)"
		device.string = "hdmi:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "hdmi-stereo"
		device.profile.description = "Digital Stereo (HDMI)"
		device.description = "Redwood HDMI Audio [Radeon HD 5000 Series] (Mobility Radeon HD 5650) Digital Stereo (HDMI)"
		alsa.mixer_name = "ATI R6xx HDMI"
		alsa.components = "HDA:1002aa01,00aa0100,00100200"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "video-display"
	active port: <hdmi-output-0>
```

---

### Post by Yellow Pasque on 2017-05-04
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by rob141 on 2017-05-05
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Fri May  5 16:37:48 UTC 2017


!!Linux Distribution
!!------------------

Ubuntu 16.04.2 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 16.04.2 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/" UBUNTU_CODENAME=xenial


!!DMI Information
!!---------------

Manufacturer:      Gateway        
Product Name:      NV59                           
Product Version:   V1.26          
Firmware Version:  V1.26          
Board Vendor:      Gateway        
Board Name:        NV59                           


!!ACPI Device Status Information
!!---------------

/sys/bus/acpi/devices/ACPI0003:00/status   15
/sys/bus/acpi/devices/PNP0103:00/status   15
/sys/bus/acpi/devices/PNP0C09:00/status   15
/sys/bus/acpi/devices/PNP0C0A:00/status   31
/sys/bus/acpi/devices/PNP0C0F:00/status   9
/sys/bus/acpi/devices/PNP0C0F:01/status   9
/sys/bus/acpi/devices/PNP0C0F:02/status   9
/sys/bus/acpi/devices/PNP0C0F:03/status   9
/sys/bus/acpi/devices/PNP0C0F:04/status   9
/sys/bus/acpi/devices/PNP0C0F:05/status   9
/sys/bus/acpi/devices/PNP0C0F:06/status   9
/sys/bus/acpi/devices/PNP0C0F:07/status   9


!!Kernel Information
!!------------------

Kernel release:    4.4.0-75-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k4.4.0-75-generic
Library version:    1.1.0
Utilities version:  1.1.0


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xcfedc000 irq 29


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series]


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:3b56 (rev 05)
	Subsystem: 1025:033d
--
02:00.1 0403: 1002:aa60
	Subsystem: 1025:033d


!!Modprobe options (Sound related)
!!--------------------------------

snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_hda_intel: enable=0,1


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : -1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : N,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N
	snoop : -1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3
  Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Converter: stream=1, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x02
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  2 May  2 14:34 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 May  2 14:34 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  3 May  5 12:36 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  1 May  2 14:33 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 May  2 14:33 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 May  2 14:34 .
drwxr-xr-x 3 root root 160 May  2 14:34 ..
lrwxrwxrwx 1 root root  12 May  2 14:34 pci-0000:02:00.1 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [HDMI]

Card hw:0 'HDMI'/'HDA ATI HDMI at 0xcfedc000 irq 29'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100200'
  Controls      : 7
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!--------------

--startcollapse--
state.HDMI {
	control.1 {
  iface CARD
  name 'HDMI/DP,pcm=3 Jack'
  value false
  comment {
   access read
   type BOOLEAN
   count 1
  }
	}
	control.2 {
  iface MIXER
  name 'IEC958 Playback Con Mask'
  value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
  comment {
   access read
   type IEC958
   count 1
  }
	}
	control.3 {
  iface MIXER
  name 'IEC958 Playback Pro Mask'
  value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
  comment {
   access read
   type IEC958
   count 1
  }
	}
	control.4 {
  iface MIXER
  name 'IEC958 Playback Default'
  value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
  comment {
   access 'read write'
   type IEC958
   count 1
  }
	}
	control.5 {
  iface MIXER
  name 'IEC958 Playback Switch'
  value true
  comment {
   access 'read write'
   type BOOLEAN
   count 1
  }
	}
	control.6 {
  iface PCM
  device 3
  name ELD
  value ''
  comment {
   access 'read volatile'
   type BYTES
   count 0
  }
	}
	control.7 {
  iface PCM
  device 3
  name 'Playback Channel Map'
  value.0 0
  value.1 0
  value.2 0
  value.3 0
  value.4 0
  value.5 0
  value.6 0
  value.7 0
  comment {
   access 'read write'
   type INTEGER
   count 8
   range '0 - 36'
  }
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
btrfs
xor
raid6_pq
ufs
qnx4
hfsplus
hfs
minix
ntfs
msdos
jfs
xfs
libcrc32c
cpuid
drbg
ansi_cprng
ctr
ccm
snd_hda_intel
arc4
ath9k
ath9k_common
ath9k_hw
uvcvideo
ath
mac80211
videobuf2_vmalloc
videobuf2_memops
acer_wmi
sparse_keymap
videobuf2_v4l2
videobuf2_core
cfg80211
v4l2_common
videodev
intel_powerclamp
media
coretemp
kvm_intel
kvm
irqbypass
shpchp
mei_me
joydev
mei
lpc_ich
input_leds
serio_raw
mac_hid
binfmt_misc
snd_hda_codec_hdmi
snd_hda_codec
snd_hda_core
snd_hwdep
snd_pcm
snd_timer
snd
soundcore
parport_pc
ppdev
lp
parport
autofs4
hid_generic
usbhid
hid
uas
usb_storage
amdkfd
amd_iommu_v2
radeon
i2c_algo_bit
broadcom
ttm
bcm_phy_lib
drm_kms_helper
syscopyarea
sysfillrect
sysimgblt
fb_sys_fops
psmouse
drm
tg3
ahci
ptp
libahci
pps_core
wmi
fjes
video


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:


!!ALSA/HDA dmesg
!!--------------

[    2.382368] [drm] Connector 1:
[    2.382370] [drm]   HDMI-A-1
[    2.382372] [drm]   HPD1
--
[   43.719510] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[   48.234374] snd_hda_intel: probe of 0000:00:1b.0 failed with error -2
[   48.234597] snd_hda_intel 0000:02:00.1: Handle vga_switcheroo audio client
[   48.237945] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:02:00.1/sound/card0/input10
[12455.409087] wlp5s0: authenticate with 48:f8:b3:fe:32:32
```

---

### Post by Yellow Pasque on 2017-05-05
The cause is this line in /etc/modprobe.d/alsa-base.conf : 
```
snd_hda_intel: enable=0,1
```

I had you add that line in a previous thread. Remove the line and see if sound is back on next boot.
[https://ubuntuforums.org/showthread.php?t=2309373&p=13425377#post13425377](https://ubuntuforums.org/showthread.php?t=2309373&p=13425377#post13425377)

---

### Post by rob141 on 2017-05-05
loll yeah i just remembered you now [COLOR=#000000]Temujin loll  

i remember when you had me removed it because the audio was working on my laptop but not though the HDMI loll now it is the opposite. 

I will try what you just said later because i am at work now so i cant test the audio but i am pretty positive that it is going to work but i will absolutely let you know ;)

i do not care anymore about the sound through the HDMI on the laptop because i got myself a Raspberry pi 3 and it is what is not connected to my tv loll. Raspberry pi is awesome and it is build on debian like ubuntu so i am not too much lost and for most trouble shooting of the raspberry pi, i look through ubuntu forum ;)

Your definitely a GREAT HELP  ;)[/COLOR]

---

### Post by wildmanne39 on 2017-05-05
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by rob141 on 2017-05-06
I cant seem to find the line you said in alsa_base.conf ??   i renamed it as .txt to be able to attache it here but it really is not a .txt loll  just in case loll

I also looked in the hdmidefault.conf in /etc/modprobe.d  the file is blank 

still no sound after reboot !!!

---

### Post by rob141 on 2017-05-06
Sorry, i juste remembered that the line snd-hda-intel enable=0,1 is actually inside the file hdmidefault.conf and i have rename the file to hdmidefault.conf.old 

Could this be why it is still not working ? Do i have the delete that line ? It is the only line in this file so the file would be empty.   but that line does not seem to be in alsa-base.conf though ???

---

### Post by Yellow Pasque on 2017-05-06
> Sorry, i just remembered that the line snd-hda-intel enable=0,1 is actually inside the file hdmidefault.conf

Me too...

>  i have rename the file to hdmidefault.conf.old 
You can delete the file if you wish (unless you put something else in it other than the enable line). And then reboot and you should see the onboard audio listed in aplay (and hopefully be able to select it in the volume control and hear sound from it).

---

### Post by rob141 on 2017-05-07
yyyyyyyyeeeeeeeeeeessssssssssssss  it is finally working again  wwwwoooooohhhhhhooooooooooooo  loll  ;)

Once again Temujin you are THE GREATEST ;)   

I like when things are finally working but i also like to try to understant why!!   I am saying this because ( i am perfectly aware the linux is not windows but ) in windows whenever you rename a file as .old, it automatically become obsolete.  

The file hdmidefault.conf was empty because i had deleted the line as you advise me to be it was still not working and that is why i had renamed it as hdmi.conf.old thinking that it would be obsolete. 

so why is it only when i deleted it that the sound came back after setting it up also is pulse audio volume controle witch is normal. But how can the file be read if the file is empty and even worst, renamed as .old  ????

i would like to understand that cause this is weird to me even if it solve my problem.  ??  If you have a short version of why it is working only when deleted, i will appreciate it ;)

Still thank you so much for you great help Temujin, YOU THE BEST    ;)

---

