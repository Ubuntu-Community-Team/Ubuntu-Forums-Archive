---
title: "Speakers/Headphones play at the same time"
date: 2014-02-07
forum: General Help
---

### Post by Psil0cybin on 2014-02-07
Just installed Xubuntu 12.04, on Lenovo G700 laptop...works flawlessly, after upgrading kernels ( 3.2.0-58-generic-pae )

my biggest issue at the moment is the fact that when I plug in a  headphones I notice that the speakers on the laptop keep playing. 
Here is some information I thought would be useful, as I went through a few steps in order to diagnose and fix this issue. 

[http://www.alsa-project.org/db/?f=9b5adea61317b7afca21e6ca46055515b848c02a](http://www.alsa-project.org/db/?f=9b5adea61317b7afca21e6ca46055515b848c02a) (Information about my system) 

**ALSA Information Script output as suggested, by individuals on IRC - in order to list detailed information about my system**
> wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh

also referenced to here: [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/197600](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/197600)

```
 
!!################################
!!ALSA Information Script v 0.4.62
!!################################

!!Script ran on: Thu Feb  6 16:25:47 UTC 2014


!!Linux Distribution
!!------------------

Ubuntu 12.04.4 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu  12.04.4 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu  precise (12.04.4 LTS)"


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      20251
Product Version:   Lenovo G700
Firmware Version:  7ACN28WW


!!Kernel Information
!!------------------

Kernel release:    3.2.0-58-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.25
Utilities version:  1.0.25


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

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xc0610000 irq 44


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:1e20 (rev 04)
    Subsystem: 17aa:3977


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=lenovo


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
    align_buffer_size : Y
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id :  (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model :  lenovo-g700,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch :  (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 1
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : Y


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: IDT ID 7695
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x111d7695
Subsystem Id: 0x17aa500b
Revision Id: 0x100101
No Modem Function Group found
Default PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=4, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x0a [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x0221101f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x0b [Pin Complex] wcaps 0x400483: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00011724: IN EAPD Detect
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0x02a1102e: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0xe
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
Node 0x0c [Pin Complex] wcaps 0x400483: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x03 0x03]
  Pincap 0x00011724: IN EAPD Detect
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0xd9a30120: [Both] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
Node 0x0d [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00010050: OUT EAPD Balanced
  EAPD 0x2: EAPD
  Pin Default 0xd9130110: [Both] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x0e [Pin Complex] wcaps 0x400403: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
Node 0x0f [Pin Complex] wcaps 0x400403: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
Node 0x10 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Master Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="HDA Generic", type="Audio", device=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x54 0x54]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x11 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x12 [Audio Input] wcaps 0x1d0541: Stereo
  Device: name="HDA Generic", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x14
  Processing caps: benign=0, ncoeff=0
Node 0x13 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x15
  Processing caps: benign=0, ncoeff=0
Node 0x14 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-Out vals:  [0x1e 0x1e]
  Power: setting=D0, actual=D0
  Connection: 5
     0x16* 0x10 0x11 0x0e 0x0f
Node 0x15 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-Out vals:  [0x90 0x90]
  Power: setting=D0, actual=D0
  Connection: 5
     0x16* 0x10 0x11 0x0e 0x0f
Node 0x16 [Audio Selector] wcaps 0x300501: Stereo
  Power: setting=D0, actual=D0
  Connection: 2
     0x0c* 0x0b
Node 0x17 [Audio Output] wcaps 0x4061d: Stereo Digital Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power: setting=D0, actual=D0
  Delay: 4 samples
Node 0x18 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x17
Node 0x19 [Beep Generator Widget] wcaps 0x70040c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
  Power: setting=D0, actual=D0
Node 0x1a [Vendor Defined Widget] wcaps 0xf00001: Stereo
Codec: Intel PantherPoint HDMI
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x80862806
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x80]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x58560010: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x02
Node 0x06 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x80]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x58560020: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x03
Node 0x07 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560030: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x04
Node 0x08 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---T  1 root audio 116,  7 Feb  6 11:12 /dev/snd/controlC0
crw-rw---T  1 root audio 116,  6 Feb  6 11:12 /dev/snd/hwC0D0
crw-rw---T  1 root audio 116,  5 Feb  6 11:12 /dev/snd/hwC0D3
crw-rw---T  1 root audio 116,  4 Feb  6 11:13 /dev/snd/pcmC0D0c
crw-rw---T  1 root audio 116,  3 Feb  6 11:13 /dev/snd/pcmC0D0p
crw-rw---T  1 root audio 116,  2 Feb  6 11:13 /dev/snd/pcmC0D3p
crw-rw---T  1 root audio 116,  1 Feb  6 11:12 /dev/snd/seq
crw-rw---T  1 root audio 116, 33 Feb  6 11:12 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Feb  6 11:12 .
drwxr-xr-x 3 root root 220 Feb  6 11:12 ..
lrwxrwxrwx 1 root root  12 Feb  6 11:12 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [PCH]

Card hw:0 'PCH'/'HDA Intel PCH at 0xc0610000 irq 44'
  Mixer name    : 'Intel PantherPoint HDMI'
  Components    : 'HDA:111d7695,17aa500b,00100101 HDA:80862806,80860101,00100000'
  Controls      : 9
  Simple ctrls  : 3
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 84 [66%] [-32.25dB] [on]
  Front Right: Playback 84 [66%] [-32.25dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 254 [100%] [0.20dB]
  Front Right: Playback 254 [100%] [0.20dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!--------------

--startcollapse--
state.PCH {
    control.1 {
        iface MIXER
        name 'Master Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.2 {
        iface MIXER
        name 'Master Playback Volume'
        value.0 84
        value.1 84
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 127'
            dbmin -9525
            dbmax 0
            dbvalue.0 -3225
            dbvalue.1 -3225
        }
    }
    control.3 {
        iface CARD
        name 'HDMI/DP,pcm=3 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value  '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.5 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value  '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.6 {
        iface MIXER
        name 'IEC958 Playback Default'
        value  '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.7 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.8 {
        iface PCM
        device 3
        name ELD
        value ''
        comment {
            access read
            type BYTES
            count 0
        }
    }
    control.9 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 254
        value.1 254
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 255'
            tlv '0000000100000008ffffec1400000014'
            dbmin -5100
            dbmax 0
            dbvalue.0 -20
            dbvalue.1 -20
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
dm_crypt
joydev
snd_hda_codec_hdmi
snd_hda_codec_idt
ideapad_laptop
sparse_keymap
arc4
rfcomm
parport_pc
ath9k
ppdev
mac80211
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
psmouse
ath9k_common
mac_hid
ath9k_hw
serio_raw
ath
uvcvideo
videodev
snd
cfg80211
soundcore
snd_page_alloc
bnep
mei
bluetooth
lp
parport
usb_storage
wmi
i915
drm_kms_helper
drm
i2c_algo_bit
video


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x0a 0x0221101f
0x0b 0x02a1102e
0x0c 0xd9a30120
0x0d 0xd9130110
0x0e 0x400000f0
0x0f 0x400000f0
0x18 0x400000f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:

/sys/class/sound/hwC0D3/init_pin_configs:
0x05 0x58560010
0x06 0x58560020
0x07 0x18560030

/sys/class/sound/hwC0D3/driver_pin_configs:

/sys/class/sound/hwC0D3/user_pin_configs:

/sys/class/sound/hwC0D3/init_verbs:

/sys/class/sound/hwC0D3/hints:


!!ALSA/HDA dmesg
!!--------------

[   18.528269] USB Video Class driver (1.1.1)
[   18.562348] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.562422] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   18.562446] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   18.571536] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
--
[   19.126421] init: alsa-restore main process (995) terminated with status 19
[   19.158262] HDMI status: Codec=3 Pin=7 Presence_Detect=0 ELD_Valid=0
[   19.158392] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   19.309247] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400



```


I was wondering if perhaps someone had some suggestions that I could do. 

I have attempted to look at alsamixer, but it only gives me a few  settings[MASTER/PCM/S/PDIF which affect both headphones and speakers at  all times. (system thinks speakers and headphones are one unit, will not  mute one or ther other) 


What can I do...I am using  Xubuntu and do not want to download Gnome packages in order to diagnose  this issue, nor use unsupported PPA's, what would be my next step in order to diagnose this problem?
Thanks in advance.

---

### Post by theDaveTheRave on 2014-02-07
I think this may also depend on your media player.

I had a similar problem when I was preparing the music for a party on my laptop, I was on the train at the time and didn't even realise that the music was coming out of the main speakers and the headphones !

I remember a long time ago showing off an install of 6.06 (dapper).

I had a film running in VLC, with english coming out of the built in speakers, and french out of the headphones (very usefull if you have a multilingual family). Even more impressive was running 2 films at once, with the sound output to a different device for each film.

I would love to be able to get that functionality back again, but I think it was all related to having separate hardware for speakers and headphones.

Sorry I'm not much help, but would be intersted if you had the above functionality, which I thought was rather cool. Admitedly I was able to turn off the internal speakers if I wanted to when I was litening through headphones.

David.

---

### Post by tgalati4 on 2014-02-07
Open a terminal and post the output of:

```
modinfo snd-hda-intel | grep parm
```

Typically, there is a switch in the headphone jack that detects when a headphone is plugged into it and mutes the speakers.  If this switch is broken, bent, or not set correctly in the driver, then you could get sound out of both.

Run *alsamixer* in a terminal and see if you have independent control for headphones and speakers.  You might have to manually control them if the autodetect is not working.

---

### Post by Psil0cybin on 2014-02-11
Thank you for your quick reply. I have only tried to play music from  Youtube, as of right now and I know that it plays the sound from the  speaker, and the headset at the same time.  Running the command

> 
                                                         Run alsamixer in a terminal and see if you have independent control  for headphones and speakers. You might have to manually control them if  the autodetect is not working.                      
     
 

I do not have a independent control for headphones and speakers, it  seems that the controles affect both the head phones and speakers at all  times.   If i was able to control both seperatly, I would be able to work around this issue, but that is not the case. Running alsamixer shows only MASTER/PCM/S/PDIF > these settings affect both speakers and headphones at same time. Muting one, mutes all, lowering the sound in one, lowers the sound in both (headphones / speakers)

Here is the output of  [B]
modinfo snd-hda-intel | grep parm[/B]

```
parm:           index:Index value for Intel HD audio interface. (array of int)
parm:           id:ID string for Intel HD audio interface. (array of charp)
parm:           enable:Enable Intel HD audio interface. (array of bool)
parm:           model:Use the given board model. (array of charp)
parm:           position_fix:DMA pointer read method.(0 = auto, 1 = LPIB, 2 = POSBUF, 3 = VIACOMBO). (array of int)
parm:           bdl_pos_adj:BDL position adjustment offset. (array of int)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (array of int)
parm:           probe_only:Only probing and no codec initialization. (array of int)
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           enable_msi:Enable Message Signaled Interrupt (MSI) (int)
parm:           patch:Patch file for Intel HD audio interface. (array of charp)
parm:           beep_mode:Select HDA Beep registration mode (0=off, 1=on, 2=mute switch on/off) (default=1). (array of int)
parm:           power_save:Automatic power-saving timeout (in second, 0 = disable). (int)
parm:           power_save_controller:Reset controller in power save mode. (bool)
parm:           align_buffer_size:Force buffer and period sizes to be multiple of 128 bytes. (bool)
parm:           snoop:Enable/disable snooping (bool)


```


> I think this may also depend on your media player.

I had a similar problem when I was preparing the music for a party on my  laptop, I was on the train at the time and didn't even realise that the  music was coming out of the main speakers and the headphones !

I remember a long time ago showing off an install of 6.06 (dapper).

I had a film running in VLC, with english coming out of the built in  speakers, and french out of the headphones (very usefull if you have a  multilingual family). Even more impressive was running 2 films at once,  with the sound output to a different device for each film.

I would love to be able to get that functionality back again, but I  think it was all related to having separate hardware for speakers and  headphones.

Sorry I'm not much help, but would be intersted if you had the above  functionality, which I thought was rather cool. Admitedly I was able to  turn off the internal speakers if I wanted to when I was litening  through headphones.

David.

If it had to do with my media player, would I not be able to alter settings via the setting panel? 
Sorry just confused, I do not think I am able to play two different sounds as it is coming from one sound card.

**Computer Specs:  **If this helps in any way, perhaps maybe you can gather more information from here.
[http://shop.lenovo.com/ca/en/laptops/essential/g-series/g700/#techspecs](http://shop.lenovo.com/ca/en/laptops/essential/g-series/g700/#techspecs)

It seems like this may affect multiple people on the Lenovo G700 laptop, what would be my next step? *filling out a bug report*?
If this cannot be fixed, I want to perhaps make this known so I can do something in order to have a resolution?
If I would fill out a bug report, what files would I need to provide/more information than I already have?

**Forgot to note: **The headphone jack in my laptop, is a mic and headphone jack in one, although putting a samsung headset from my cellphone does not change anything, thus I do not think it is a hardware issue.

Thanks again in advance,
Psil0

---

### Post by remy5 on 2014-08-26
I had the same issue and solved it with the following:

Read the page:
  [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

From the website:
  [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages) ,
download the latest DMKS package approriate for your system, for instance:
  oem-audio-hda-daily-dkms_0201408250917~ubuntu12.04.1_all.deb
         
Install it:
  sudo dpkg -i oem-audio-hda-daily-dkms_0.201408250917~ubuntu12.04.1_all.deb

Reboot.

Good luck!

---

