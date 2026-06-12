---
title: "Sound problems after regular updates 12.04.1LTS"
date: 2013-01-21
forum: General Help
---

### Post by Sxynerd on 2013-01-21
I'm on a Hp laptop and I've been running Ubuntu for several months without a single sound issue.  After a regular update notice popped up, I updated the 20 or so things.

Now whenever the PC locks the screen from being idle too long I loose sound from my headphone jack (into my external speakers) and onboard speakers when I unplug the externals.  All sound gets defaulted to run through my HDMI and through a second monitor.

Under SOUND it still shows my two options of HDMI/Displayport and HEADPHONES but only the HDMI has sound.

Also there is a "mute" hotkey on one of my F-keys that has a light indicator the is RED.  Previously it was always White.


I have re-installed LTS 3 times now and all sound works normal until I do all the general updates.  One I installed 12.10, did all the updates and everything works but 12.10 but I need .04LTS.

I can't seem to find the audio troubleshooting thread and searching returned no helpful results so far.

Any help would be great

---

### Post by Sxynerd on 2013-01-21
Here is the link from a trouble shooting link I found. 

[http://www.alsa-project.org/db/?f=e17316e196c9970d6534ab5e6afff7b1a8c060c9](http://www.alsa-project.org/db/?f=e17316e196c9970d6534ab5e6afff7b1a8c060c9)



Here is the output from this [bash alsa-info.sh --stdout] command.
```
Kernel release:    3.2.0-36-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
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
                      HDA Intel PCH at 0xc7500000 irq 52


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:1c20 (rev 05)
	Subsystem: 103c:1659


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


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
	align_buffer_size : Y
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N
	snoop : Y


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: IDT 92HD81B1X5
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x111d7605
Subsystem Id: 0x103c1659
Revision Id: 0x100105
No Modem Function Group found
Default PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=3, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Power-Map: 0x00
Node 0x0a [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x0001173c: IN OUT HP EAPD Detect
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 3
     0x13* 0x14 0x1c
Node 0x0b [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Front Headphone Jack", index=0, device=0
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x0221101f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Power: setting=D0, actual=D0
  Connection: 3
     0x13* 0x14 0x1c
Node 0x0c [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Control: name="Mic Jack Mode", index=0, device=0
    ControlAmp: chs=0, dir=In, idx=0, ofs=0
  Control: name="Mic Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Jack", index=0, device=0
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00011734: IN OUT EAPD Detect
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0x02a11020: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Power: setting=D0, actual=D0
  Connection: 3
     0x13* 0x14 0x1c
Node 0x0d [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00010050: OUT EAPD Balanced
  EAPD 0x2: EAPD
  Pin Default 0x92170110: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
  Connection: 3
     0x13* 0x14 0x1c
Node 0x0e [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 3
     0x13* 0x14 0x1c
Node 0x0f [Pin Complex] wcaps 0x400583: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x92170110: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 3
     0x13 0x14* 0x1c
Node 0x10 [Pin Complex] wcaps 0x400500: Mono
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
  Connection: 1
     0x1a
Node 0x11 [Pin Complex] wcaps 0x400483: Stereo Amp-In
  Control: name="Internal Mic Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: N/A
  Amp-In vals:  [0x01 0x01]
  Pincap 0x00000024: IN Detect
  Pin Default 0xd5a30130: [Both] Mic at Int Top
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
Node 0x12 [Vendor Defined Widget] wcaps 0xf00503: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Power: setting=D0, actual=D0
  Connection: 1
     0x20
Node 0x13 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=63
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="STAC92xx Analog", type="Audio", device=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x14 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Speaker Playback Volume", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=63
  Control: name="Speaker Playback Switch", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x15 [Audio Input] wcaps 0x1d0541: Stereo
  Device: name="STAC92xx Analog", type="Audio", device=0
  Converter: stream=4, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x17
  Processing caps: benign=0, ncoeff=0
Node 0x16 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x18
  Processing caps: benign=0, ncoeff=0
Node 0x17 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x00 0x00]
  Power: setting=D0, actual=D0
  Connection: 7
     0x0c 0x0e 0x0f 0x1b 0x11* 0x12 0x0a
Node 0x18 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Power: setting=D0, actual=D0
  Connection: 7
     0x0c* 0x0e 0x0f 0x1b 0x11 0x12 0x0a
Node 0x19 [Audio Selector] wcaps 0x300501: Stereo
  Power: setting=D0, actual=D0
  Connection: 3
     0x13* 0x14 0x1c
Node 0x1a [Audio Mixer] wcaps 0x200500: Mono
  Power: setting=D0, actual=D0
  Connection: 1
     0x19
Node 0x1b [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Power: setting=D0, actual=D0
  Connection: 6
     0x0c 0x0e 0x0f 0x13 0x14 0x0a
Node 0x1c [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x9f 0x9f]
  Power: setting=D0, actual=D0
  Connection: 1
     0x1b
Node 0x1d [Audio Output] wcaps 0x4061d: Stereo Digital Amp-Out
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
Node 0x1e [Audio Output] wcaps 0x4061d: Stereo Digital Amp-Out
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
Node 0x1f [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x1d
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x1e
Node 0x21 [Beep Generator Widget] wcaps 0x70040c: Mono Amp-Out
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
  Power: setting=D0, actual=D0
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono
Codec: Intel CougarPoint HDMI
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x80862805
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
  Converter: stream=8, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
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
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
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
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x80]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x58560030: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x04
Node 0x08 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---T+ 1 root audio 116,  7 Jan 21 20:29 /dev/snd/controlC0
crw-rw---T+ 1 root audio 116,  6 Jan 21 20:29 /dev/snd/hwC0D0
crw-rw---T+ 1 root audio 116,  5 Jan 21 20:29 /dev/snd/hwC0D3
crw-rw---T+ 1 root audio 116,  4 Jan 21 20:34 /dev/snd/pcmC0D0c
crw-rw---T+ 1 root audio 116,  3 Jan 21 20:34 /dev/snd/pcmC0D0p
crw-rw---T+ 1 root audio 116,  2 Jan 21 20:34 /dev/snd/pcmC0D3p
crw-rw---T+ 1 root audio 116,  1 Jan 21 20:29 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 Jan 21 20:29 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jan 21 20:29 .
drwxr-xr-x 3 root root 220 Jan 21 20:29 ..
lrwxrwxrwx 1 root root  12 Jan 21 20:29 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [PCH]

Card hw:0 'PCH'/'HDA Intel PCH at 0xc7500000 irq 52'
  Mixer name	: 'Intel CougarPoint HDMI'
  Components	: 'HDA:111d7605,103c1659,00100105 HDA:80862805,80860101,00100000'
  Controls      : 23
  Simple ctrls  : 11
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-48.00dB] [off]
  Front Right: Playback 0 [0%] [-48.00dB] [off]
Simple mixer control 'Speaker',1
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [off]
  Front Right: Playback 64 [100%] [0.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 1 [33%] [-12.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Internal Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 1 [33%] [10.00dB]
  Front Right: Capture 1 [33%] [10.00dB]


!!Alsactl output
!!--------------

--startcollapse--
state.PCH {
	control.1 {
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -4800
			dbmax 0
			dbvalue.0 -4800
			dbvalue.1 -4800
		}
	}
	control.2 {
		iface MIXER
		name 'Speaker Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.3 {
		iface MIXER
		name 'Speaker Playback Volume'
		index 1
		value.0 64
		value.1 64
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -4800
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.4 {
		iface MIXER
		name 'Speaker Playback Switch'
		index 1
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.5 {
		iface MIXER
		name 'Mic Jack Mode'
		value 'Mic In'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'Mic In'
			item.1 'Line In'
		}
	}
	control.6 {
		iface MIXER
		name 'Beep Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.7 {
		iface MIXER
		name 'Beep Playback Volume'
		value 1
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 3'
			dbmin -1800
			dbmax 0
			dbvalue.0 -1200
		}
	}
	control.8 {
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 15'
			dbmin 0
			dbmax 2250
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.9 {
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.10 {
		iface MIXER
		name 'Mic Capture Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.11 {
		iface MIXER
		name 'Internal Mic Capture Volume'
		value.0 1
		value.1 1
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 1000
			dbvalue.1 1000
		}
	}
	control.12 {
		iface MIXER
		name 'Master Playback Volume'
		value 64
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 64'
			dbmin -9999999
			dbmax 0
			dbvalue.0 0
		}
	}
	control.13 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.14 {
		iface CARD
		name 'Front Headphone Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.15 {
		iface CARD
		name 'Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.16 {
		iface CARD
		name 'HDMI/DP,pcm=3 Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.17 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.18 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.19 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.20 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.21 {
		iface PCM
		device 3
		name ELD
		value '1000080068126a01000000000000000022f0a926485020773232303709070700000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type BYTES
			count 83
		}
	}
	control.22 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 255'
			tlv '0000000100000008ffffec1400000014'
			dbmin -5100
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.23 {
		iface MIXER
		name 'Digital Capture Volume'
		value.0 60
		value.1 60
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 120'
			tlv '0000000100000008fffff44800000032'
			dbmin -3000
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_iso8859_1
nls_cp437
vfat
fat
snd_hda_codec_hdmi
snd_hda_codec_idt
rfcomm
parport_pc
ppdev
bnep
bluetooth
arc4
hp_wmi
sparse_keymap
joydev
uvcvideo
videodev
v4l2_compat_ioctl32
usbhid
hid
iwlwifi
mac80211
cfg80211
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
i915
psmouse
serio_raw
snd_seq
video
snd_timer
snd_seq_device
mac_hid
hp_accel
lis3lv02d
input_polldev
wmi
radeon
ttm
drm_kms_helper
snd
drm
i2c_algo_bit
rts_pstor
soundcore
snd_page_alloc
mei
lp
parport
r8169


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x0a 0x40f000f0
0x0b 0x0221101f
0x0c 0x02a11020
0x0d 0x40f000f0
0x0e 0x40f000f0
0x0f 0x92170110
0x10 0x40f000f0
0x11 0xd5a30130
0x1f 0x40f000f0
0x20 0x40f000f0

/sys/class/sound/hwC0D0/driver_pin_configs:
0x0a 0x40f000f0
0x0b 0x0221101f
0x0c 0x02a11020
0x0d 0x92170110
0x0e 0x40f000f0
0x0f 0x92170110
0x10 0x40f000f0
0x11 0xd5a30130
0x1f 0x40f000f0
0x20 0x40f000f0

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D3/init_pin_configs:
0x05 0x18560010
0x06 0x58560020
0x07 0x58560030

/sys/class/sound/hwC0D3/driver_pin_configs:

/sys/class/sound/hwC0D3/user_pin_configs:

/sys/class/sound/hwC0D3/init_verbs:


!!ALSA/HDA dmesg
!!--------------

[   15.100889] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 1
[   15.104006] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.104078] snd_hda_intel 0000:00:1b.0: irq 52 for MSI/MSI-X
[   15.104113] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   15.684054] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[   15.684111] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[   15.684157] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[   15.691072] HDMI: detected monitor HP w2207 at connection type HDMI
[   15.691075] HDMI: available speakers: FL/FR
[   15.691078] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
[   15.691190] HDMI: detected monitor HP w2207 at connection type HDMI
[   15.691193] HDMI: available speakers: FL/FR
[   15.691196] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
[   15.691202] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[   15.691219] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   15.691257] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[   15.691320] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   15.691382] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   15.694750] HDMI: detected monitor HP w2207 at connection type HDMI
[   15.694754] HDMI: available speakers: FL/FR
[   15.694758] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
[   15.772489] [drm] Changing LVDS panel from (-hsync, -vsync) to (-hsync, +vsync)
--
[   15.792970] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   15.998428] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=1
[   15.998492] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   16.187676] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[   16.187723] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[   16.487339] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[   16.490879] HDMI: detected monitor HP w2207 at connection type HDMI
[   16.490881] HDMI: available speakers: FL/FR
[   16.490884] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
[   18.794929] [drm] Changing LVDS panel from (-hsync, +vsync) to (-hsync, -vsync)
[   19.021086] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=1
[   19.021145] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   19.210045] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[   19.210091] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[   19.509704] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[   19.513249] HDMI: detected monitor HP w2207 at connection type HDMI
[   19.513251] HDMI: available speakers: FL/FR
[   19.513254] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
[   24.575158] eth0: no IPv6 routers present
[   25.942463] wlan0: no IPv6 routers present
[  231.882653] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=1
[  231.882710] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[  232.349718] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[  232.349776] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[  232.353550] HDMI: detected monitor HP w2207 at connection type HDMI
[  232.353561] HDMI: available speakers: FL/FR
[  232.353574] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24

```

---

### Post by Sxynerd on 2013-01-21
cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; aplay -l; sudo alsa force-reload; sudo lshw -C sound

```
wolvee@wolvee-dv7:~$ cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; aplay -l; sudo alsa force-reload; sudo lshw -C sound
Advanced Linux Sound Architecture Driver Version 1.0.24.
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xc7500000 irq 51
  1:        : sequencer
  2: [ 0- 3]: digital audio playback
  3: [ 0- 0]: digital audio playback
  4: [ 0- 0]: digital audio capture
  5: [ 0- 3]: hardware dependent
  6: [ 0- 0]: hardware dependent
  7: [ 0]   : control
 33:        : timer
00-03: HDA Codec 3
00-00: HDA Codec 0
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 1
00-03: HDMI 0 : HDMI 0 : playback 1
Client info
  cur  clients : 1
  peak clients : 1
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
[sudo] password for wolvee: 
rm: cannot remove `/etc/asound.conf': No such file or directory
rm: cannot remove `/home/wolvee/.asound*': No such file or directory
Ign http://security.ubuntu.com precise-security InRelease
Ign http://us.archive.ubuntu.com precise InRelease                                                                                                     
Ign http://us.archive.ubuntu.com precise-updates InRelease                                                                                             
Ign http://us.archive.ubuntu.com precise-backports InRelease                                                                                           
Hit http://security.ubuntu.com precise-security Release.gpg                                                                                            
Hit http://us.archive.ubuntu.com precise Release.gpg                                                                                                   
Hit http://security.ubuntu.com precise-security Release                                                          
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                                                     
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                                                    
Ign http://extras.ubuntu.com precise InRelease                                                                    
Hit http://us.archive.ubuntu.com precise Release                                            
Ign http://ppa.launchpad.net precise InRelease                                              
Ign http://dl.google.com stable InRelease                                                   
Hit http://us.archive.ubuntu.com precise-updates Release                                    
Hit http://us.archive.ubuntu.com precise-backports Release                                                                              
Hit http://security.ubuntu.com precise-security/main Sources                                                                            
Hit http://extras.ubuntu.com precise Release.gpg                                                                                        
Hit http://us.archive.ubuntu.com precise/main Sources                                                                                   
Hit http://us.archive.ubuntu.com precise/restricted Sources                                                      
Hit http://us.archive.ubuntu.com precise/universe Sources                                  
Hit http://us.archive.ubuntu.com precise/multiverse Sources                                
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                               
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages                         
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages                                                 
Hit http://ppa.launchpad.net precise Release.gpg                                                                 
Hit http://security.ubuntu.com precise-security/restricted Sources                                               
Hit http://security.ubuntu.com precise-security/universe Sources                                                 
Hit http://security.ubuntu.com precise-security/multiverse Sources                                               
Hit http://security.ubuntu.com precise-security/main amd64 Packages                                              
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages                                        
Hit http://security.ubuntu.com precise-security/universe amd64 Packages                    
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages                  
Hit http://security.ubuntu.com precise-security/main i386 Packages                                               
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                                         
Hit http://security.ubuntu.com precise-security/universe i386 Packages                                           
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages                                               
Hit http://us.archive.ubuntu.com precise/main i386 Packages                                
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages                          
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                                                  
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages                                                
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                                                   
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex                                             
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex                                             
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                                         
Hit http://dl.google.com stable Release.gpg                                                                      
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex                                               
Hit http://us.archive.ubuntu.com precise-updates/main Sources                              
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                            
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources                                              
Hit http://us.archive.ubuntu.com precise-updates/universe Sources                                                
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources                                              
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages                                             
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages                                       
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                      
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                      
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                        
Hit http://extras.ubuntu.com precise Release                                                                     
Hit http://us.archive.ubuntu.com precise-updates/universe amd64 Packages                                         
Hit http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages                  
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages                         
Hit http://ppa.launchpad.net precise Release                                                                      
Hit http://security.ubuntu.com precise-security/main Translation-en                                               
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                  
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages                                        
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                        
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages                    
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages                                        
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex                                           
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex                                     
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex                                     
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex                                       
Hit http://security.ubuntu.com precise-security/universe Translation-en                                          
Hit http://us.archive.ubuntu.com precise-backports/main Sources                                                  
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources                      
Hit http://us.archive.ubuntu.com precise-backports/universe Sources                        
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources                      
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages                     
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages               
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages                 
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages               
Hit http://dl.google.com stable Release                                                    
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages                       
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages                
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages                  
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages                
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex                   
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex             
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://extras.ubuntu.com precise/main Sources                                          
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex               
Hit http://us.archive.ubuntu.com precise/main Translation-en                               
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                         
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                         
Hit http://us.archive.ubuntu.com precise/universe Translation-en                           
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en                       
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                 
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en                 
Hit http://ppa.launchpad.net precise/main Sources                                          
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en                   
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en               
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en               
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en                 
Hit http://dl.google.com stable/main amd64 Packages                                        
Hit http://extras.ubuntu.com precise/main amd64 Packages             
Hit http://extras.ubuntu.com precise/main i386 Packages
Hit http://ppa.launchpad.net precise/main amd64 Packages             
Hit http://ppa.launchpad.net precise/main i386 Packages              
Ign http://ppa.launchpad.net precise/main TranslationIndex           
Ign http://extras.ubuntu.com precise/main TranslationIndex           
Hit http://dl.google.com stable/main i386 Packages
Ign http://dl.google.com stable/main TranslationIndex                
Ign http://ppa.launchpad.net precise/main Translation-en_US          
Ign http://extras.ubuntu.com precise/main Translation-en_US          
Ign http://extras.ubuntu.com precise/main Translation-en
Ign http://dl.google.com stable/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://dl.google.com stable/main Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3 libept1.4.12 libio-string-perl libparse-debianchangelog-perl libsub-name-perl
  libtimedate-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev libhtml-parser-perl libhtml-template-perl libxml-simple-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3 libept1.4.12 libio-string-perl libparse-debianchangelog-perl libsub-name-perl
  libtimedate-perl
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,091 kB of archives.
After this operation, 9,613 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main libboost-iostreams1.46.1 amd64 1.46.1-7ubuntu3 [39.2 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main libcwidget3 amd64 0.5.16-3.1ubuntu1 [406 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main libept1.4.12 amd64 1.0.6~exp1ubuntu1 [129 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main aptitude amd64 0.6.6-1ubuntu1.1 [2,373 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise/main libsub-name-perl amd64 0.05-1build2 [9,656 B]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise/main libclass-accessor-perl all 0.34-1 [26.0 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise/main libio-string-perl all 1.08-2 [12.0 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise/main libtimedate-perl all 1.2000-1 [41.6 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise/main libparse-debianchangelog-perl all 1.2.0-1ubuntu1 [54.0 kB]
Fetched 3,091 kB in 1s (1,718 kB/s)                     
Selecting previously unselected package libboost-iostreams1.46.1.
(Reading database ... 168370 files and directories currently installed.)
Unpacking libboost-iostreams1.46.1 (from .../libboost-iostreams1.46.1_1.46.1-7ubuntu3_amd64.deb) ...
Selecting previously unselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3.1ubuntu1_amd64.deb) ...
Selecting previously unselected package libept1.4.12.
Unpacking libept1.4.12 (from .../libept1.4.12_1.0.6~exp1ubuntu1_amd64.deb) ...
Selecting previously unselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.6-1ubuntu1.1_amd64.deb) ...
Selecting previously unselected package libsub-name-perl.
Unpacking libsub-name-perl (from .../libsub-name-perl_0.05-1build2_amd64.deb) ...
Selecting previously unselected package libclass-accessor-perl.
Unpacking libclass-accessor-perl (from .../libclass-accessor-perl_0.34-1_all.deb) ...
Selecting previously unselected package libio-string-perl.
Unpacking libio-string-perl (from .../libio-string-perl_1.08-2_all.deb) ...
Selecting previously unselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.2000-1_all.deb) ...
Selecting previously unselected package libparse-debianchangelog-perl.
Unpacking libparse-debianchangelog-perl (from .../libparse-debianchangelog-perl_1.2.0-1ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up libboost-iostreams1.46.1 (1.46.1-7ubuntu3) ...
Setting up libcwidget3 (0.5.16-3.1ubuntu1) ...
Setting up libept1.4.12 (1.0.6~exp1ubuntu1) ...
Setting up aptitude (0.6.6-1ubuntu1.1) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
Setting up libsub-name-perl (0.05-1build2) ...
Setting up libclass-accessor-perl (0.34-1) ...
Setting up libio-string-perl (1.08-2) ...
Setting up libtimedate-perl (1.2000-1) ...
Setting up libparse-debianchangelog-perl (1.2.0-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
No candidate version found for padevchooser
No candidate version found for libsdl1.2debian-pulseaudio
No candidate version found for padevchooser
No candidate version found for libsdl1.2debian-pulseaudio
The following NEW packages will be installed:
  gnome-alsamixer libbonobo2-0{a} libbonobo2-common{a} libbonoboui2-0{a} libbonoboui2-common{a} libglademm-2.4-1c2a{a} libgnome2-0{a} 
  libgnome2-bin{a} libgnomecanvas2-0{a} libgnomecanvas2-common{a} libgnomeui-0{a} libgnomeui-common{a} libgnomevfs2-0{a} libgnomevfs2-common{a} 
  libgtkmm-2.4-1c2a{a} paman pavucontrol{a} pavumeter{a} 
0 packages upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,691 kB of archives. After unpacking 13.4 MB will be used.
Do you want to continue? [Y/n/?] y
Get: 1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libbonobo2-common all 2.32.1-0ubuntu1.1 [37.4 kB]
Get: 2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libbonobo2-0 amd64 2.32.1-0ubuntu1.1 [285 kB]
Get: 3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgnomevfs2-common amd64 1:2.24.4-1ubuntu2.1 [24.6 kB]
Get: 4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgnomevfs2-0 amd64 1:2.24.4-1ubuntu2.1 [275 kB]
Get: 5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgnome2-bin amd64 2.32.1-2ubuntu1.1 [15.9 kB]
Get: 6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgnome2-0 amd64 2.32.1-2ubuntu1.1 [53.4 kB]
Get: 7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgnomecanvas2-common all 2.30.3-1ubuntu1.1 [9,120 B]
Get: 8 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgnomecanvas2-0 amd64 2.30.3-1ubuntu1.1 [101 kB]
Get: 9 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libbonoboui2-common all 2.24.5-0ubuntu1.1 [11.7 kB]
Get: 10 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libbonoboui2-0 amd64 2.24.5-0ubuntu1.1 [189 kB]
Get: 11 http://us.archive.ubuntu.com/ubuntu/ precise/main libgnomeui-common all 2.24.5-2ubuntu2 [16.5 kB]
Get: 12 http://us.archive.ubuntu.com/ubuntu/ precise/main libgnomeui-0 amd64 2.24.5-2ubuntu2 [257 kB]
Get: 13 http://us.archive.ubuntu.com/ubuntu/ precise/main libgtkmm-2.4-1c2a amd64 1:2.24.2-1ubuntu1 [1,073 kB]
Get: 14 http://us.archive.ubuntu.com/ubuntu/ precise/universe gnome-alsamixer amd64 0.9.7~cvs.20060916.ds.1-3 [51.4 kB]
Get: 15 http://us.archive.ubuntu.com/ubuntu/ precise/universe libglademm-2.4-1c2a amd64 2.6.7-2build1 [22.2 kB]
Get: 16 http://us.archive.ubuntu.com/ubuntu/ precise/universe paman amd64 0.9.4-1ubuntu3 [94.3 kB]
Get: 17 http://us.archive.ubuntu.com/ubuntu/ precise/universe pavucontrol amd64 0.99.2-1build1 [145 kB]
Get: 18 http://us.archive.ubuntu.com/ubuntu/ precise/universe pavumeter amd64 0.9.3-1ubuntu2 [28.4 kB]
Fetched 2,691 kB in 1s (1,990 kB/s)   
Selecting previously unselected package libbonobo2-common.
(Reading database ... 168609 files and directories currently installed.)
Unpacking libbonobo2-common (from .../libbonobo2-common_2.32.1-0ubuntu1.1_all.deb) ...
Selecting previously unselected package libbonobo2-0.
Unpacking libbonobo2-0 (from .../libbonobo2-0_2.32.1-0ubuntu1.1_amd64.deb) ...
Selecting previously unselected package libgnomevfs2-common.
Unpacking libgnomevfs2-common (from .../libgnomevfs2-common_1%3a2.24.4-1ubuntu2.1_amd64.deb) ...
Selecting previously unselected package libgnomevfs2-0.
Unpacking libgnomevfs2-0 (from .../libgnomevfs2-0_1%3a2.24.4-1ubuntu2.1_amd64.deb) ...
Selecting previously unselected package libgnome2-bin.
Unpacking libgnome2-bin (from .../libgnome2-bin_2.32.1-2ubuntu1.1_amd64.deb) ...
Selecting previously unselected package libgnome2-0.
Unpacking libgnome2-0 (from .../libgnome2-0_2.32.1-2ubuntu1.1_amd64.deb) ...
Selecting previously unselected package libgnomecanvas2-common.
Unpacking libgnomecanvas2-common (from .../libgnomecanvas2-common_2.30.3-1ubuntu1.1_all.deb) ...
Selecting previously unselected package libgnomecanvas2-0.
Unpacking libgnomecanvas2-0 (from .../libgnomecanvas2-0_2.30.3-1ubuntu1.1_amd64.deb) ...
Selecting previously unselected package libbonoboui2-common.
Unpacking libbonoboui2-common (from .../libbonoboui2-common_2.24.5-0ubuntu1.1_all.deb) ...
Selecting previously unselected package libbonoboui2-0.
Unpacking libbonoboui2-0 (from .../libbonoboui2-0_2.24.5-0ubuntu1.1_amd64.deb) ...
Selecting previously unselected package libgnomeui-common.
Unpacking libgnomeui-common (from .../libgnomeui-common_2.24.5-2ubuntu2_all.deb) ...
Selecting previously unselected package libgnomeui-0.
Unpacking libgnomeui-0 (from .../libgnomeui-0_2.24.5-2ubuntu2_amd64.deb) ...
Selecting previously unselected package libgtkmm-2.4-1c2a.
Unpacking libgtkmm-2.4-1c2a (from .../libgtkmm-2.4-1c2a_1%3a2.24.2-1ubuntu1_amd64.deb) ...
Selecting previously unselected package gnome-alsamixer.
Unpacking gnome-alsamixer (from .../gnome-alsamixer_0.9.7~cvs.20060916.ds.1-3_amd64.deb) ...
Selecting previously unselected package libglademm-2.4-1c2a.
Unpacking libglademm-2.4-1c2a (from .../libglademm-2.4-1c2a_2.6.7-2build1_amd64.deb) ...
Selecting previously unselected package paman.
Unpacking paman (from .../paman_0.9.4-1ubuntu3_amd64.deb) ...
Selecting previously unselected package pavucontrol.
Unpacking pavucontrol (from .../pavucontrol_0.99.2-1build1_amd64.deb) ...
Selecting previously unselected package pavumeter.
Unpacking pavumeter (from .../pavumeter_0.9.3-1ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up libbonobo2-common (2.32.1-0ubuntu1.1) ...
Setting up libbonobo2-0 (2.32.1-0ubuntu1.1) ...
Setting up libgnomevfs2-common (1:2.24.4-1ubuntu2.1) ...
Setting up libgnomevfs2-0 (1:2.24.4-1ubuntu2.1) ...
Setting up libgnomecanvas2-common (2.30.3-1ubuntu1.1) ...
Setting up libgnomecanvas2-0 (2.30.3-1ubuntu1.1) ...
Setting up libbonoboui2-common (2.24.5-0ubuntu1.1) ...
Setting up libgnomeui-common (2.24.5-2ubuntu2) ...
Setting up libgtkmm-2.4-1c2a (1:2.24.2-1ubuntu1) ...
Setting up libglademm-2.4-1c2a (2.6.7-2build1) ...
Setting up paman (0.9.4-1ubuntu3) ...
Setting up pavucontrol (0.99.2-1build1) ...
Setting up pavumeter (0.9.3-1ubuntu2) ...
Setting up libgnome2-bin (2.32.1-2ubuntu1.1) ...
Setting up libgnome2-0 (2.32.1-2ubuntu1.1) ...
Setting up libbonoboui2-0 (2.24.5-0ubuntu1.1) ...
Setting up libgnomeui-0 (2.24.5-2ubuntu2) ...
Setting up gnome-alsamixer (0.9.7~cvs.20060916.ds.1-3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
H/W path               Device      Class          Description
=============================================================
                                   system         HP Pavilion dv7 Notebook PC (LW174UA#ABA)
/0                                 bus            1659
/0/0                               memory         1MiB BIOS
/0/11                              memory         8GiB System Memory
/0/11/0                            memory         4GiB SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
/0/11/1                            memory         4GiB SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
/0/1b                              processor      Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
/0/1b/1d                           memory         32KiB L1 cache
/0/1b/1e                           memory         256KiB L2 cache
/0/1b/1f                           memory         3MiB L3 cache
/0/1c                              memory         32KiB L1 cache
/0/100                             bridge         2nd Generation Core Processor Family DRAM Controller
/0/100/1                           bridge         Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
/0/100/1/0                         display        Seymour [Radeon HD 6400M Series]
/0/100/2                           display        2nd Generation Core Processor Family Integrated Graphics Controller
/0/100/16                          communication  6 Series/C200 Series Chipset Family MEI Controller #1
/0/100/1a                          bus            6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
/0/100/1b                          multimedia     6 Series/C200 Series Chipset Family High Definition Audio Controller
/0/100/1c                          bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 1
/0/100/1c/0            eth0        network        RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1c.1                        bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 2
/0/100/1c.1/0          wlan0       network        Centrino Wireless-N + WiMAX 6150
/0/100/1c.2                        bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 3
/0/100/1c.2/0          scsi6       generic        RTS5116 PCI Express Card Reader
/0/100/1c.2/0/0.0.0    /dev/sdb    disk           3959MB SCSI Disk
/0/100/1c.2/0/0.0.0/1  /dev/sdb1   volume         3775MiB Windows FAT volume
/0/100/1c.3                        bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 4
/0/100/1c.3/0                      bus            uPD720200 USB 3.0 Host Controller
/0/100/1d                          bus            6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
/0/100/1f                          bridge         HM65 Express Chipset Family LPC Controller
/0/100/1f.2            scsi0       storage        6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
/0/100/1f.2/0          /dev/sda    disk           750GB TOSHIBA MK7559GS
/0/100/1f.2/0/1        /dev/sda1   volume         690GiB EXT4 volume
/0/100/1f.2/0/2        /dev/sda2   volume         8138MiB Extended partition
/0/100/1f.2/0/2/5      /dev/sda5   volume         8138MiB Linux swap / Solaris partition
/0/100/1f.2/1          /dev/cdrom  disk           DVD A  DS8A5LH
/0/100/1f.3                        bus            6 Series/C200 Series Chipset Family SMBus Controller
/1                                 power          MU09100
total 0
crw-rw---T+  1 root audio 116, 33 Jan 21 21:51 timer
crw-rw---T+  1 root audio 116,  1 Jan 21 21:51 seq
crw-rw---T+  1 root audio 116,  5 Jan 21 21:51 hwC0D3
crw-rw---T+  1 root audio 116,  6 Jan 21 21:51 hwC0D0
crw-rw---T+  1 root audio 116,  7 Jan 21 21:51 controlC0
drwxr-xr-x   2 root root       60 Jan 21 21:51 by-path
drwxr-xr-x   3 root root      220 Jan 21 21:51 .
crw-rw---T+  1 root audio 116,  3 Jan 21 21:51 pcmC0D0p
crw-rw---T+  1 root audio 116,  4 Jan 21 21:52 pcmC0D0c
crw-rw---T+  1 root audio 116,  2 Jan 21 21:53 pcmC0D3p
drwxr-xr-x  17 root root     4360 Jan 21 21:59 ..
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5)
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b5)
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series] [1002:6760]
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
0d:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0886] (rev 67)
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)
19:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 004: ID 5986:02ac Acer, Inc 
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 004: ID 8087:07d7 Intel Corp. 
/sbin/alsactl
Specified filename /dev/dsp does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  wolvee     1687 F.... pulseaudio
dpkg-query: no path found matching pattern *bin/slmodemd*.
[    0.000000] No AGP bridge found
[    0.000000] found SMP MP-table at [ffff8800000fe1b0] fe1b0
[    0.000000] No NUMA configuration found
[    0.000000] No AGP bridge found
[    0.600110] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.700464] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.700466] HEST: Table not found.
[    0.765494] pnp: PnP ACPI: found 13 devices
[    0.818509] audit: initializing netlink socket (disabled)
[    0.818516] type=2000 audit(1358823075.656:1): initialized
[    0.861164] ERST: Table is not found!
[    1.103014] Fixed MDIO Bus: probed
[    1.121986] hub 1-0:1.0: USB hub found
[    1.141961] hub 2-0:1.0: USB hub found
[    1.142616] hub 3-0:1.0: USB hub found
[    1.145807] hub 4-0:1.0: USB hub found
[    1.201486] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.566282] hub 1-1:1.0: USB hub found
[    1.810123] hub 2-1:1.0: USB hub found
[   11.505462] lp: driver loaded but no devices found
[   11.515694] uvcvideo: Found UVC 1.00 device HP TrueVision HD (5986:02ac)
[   11.517307] type=1400 audit(1358823086.816:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=480 comm="apparmor_parser"
[   11.517652] type=1400 audit(1358823086.816:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=480 comm="apparmor_parser"
[   11.517865] type=1400 audit(1358823086.816:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=480 comm="apparmor_parser"
[   11.532833] hp_accel: hardware type DV7 found
[   11.716829] iwlwifi 0000:0d:00.0: loaded firmware version 41.28.5.1 build 33926
[   12.102507] lis3lv02d: 8 bits 3DC sensor found
[   12.505982] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   12.686247] type=1400 audit(1358823087.984:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=871 comm="apparmor_parser"
[   12.688345] type=1400 audit(1358823087.988:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=871 comm="apparmor_parser"
[   12.697812] type=1400 audit(1358823087.996:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=894 comm="apparmor_parser"
[   12.699315] type=1400 audit(1358823087.996:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=895 comm="apparmor_parser"
[   12.699608] type=1400 audit(1358823087.996:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=895 comm="apparmor_parser"
[   12.699774] type=1400 audit(1358823087.996:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=895 comm="apparmor_parser"
[   12.700638] type=1400 audit(1358823088.000:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=901 comm="apparmor_parser"
[   12.719588] scsi6 : SCSI emulation for PCI-Express Mass Storage devices
[   12.762653] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.762734] snd_hda_intel 0000:00:1b.0: irq 51 for MSI/MSI-X
[   12.762767] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   12.884416] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   12.884545] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   12.884653] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   12.965063] init: alsa-restore main process (961) terminated with status 19
sudo: /etc/init.d/sl-modem-daemon: command not found
	Release Date: 04/25/2011
	Manufacturer: Hewlett-Packard
	Product Name: HP Pavilion dv7 Notebook PC
	Serial Number: 5CH12206HZ
	Manufacturer: Hewlett-Packard
	Product Name: 1659
	Serial Number: PBZBR01HT0G297
	Manufacturer: Hewlett-Packard
	Serial Number: Chassis Serial Number
	Manufacturer: 13-42
	SBDS Serial Number: E420
	SBDS Manufacture Date: 2011-05-14
	Manufacturer: ELPIDA
	Serial Number: 4D7C125A
	Manufacturer: ELPIDA
	Serial Number: 417C125F
	Manufacturer: Intel(R) Corporation
	Serial Number: Not Specified
snd_seq_dummy          12798  0 
snd_hda_codec_hdmi     36516  1 
snd_hda_codec_idt      70236  1 
snd_hda_intel          39382  3 
snd_hda_codec         140309  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usbhid                 47238  0 
hid                    99636  1 usbhid
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Unloading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-hdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-hdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
  *-multimedia            
       description: Audio device
       product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:51 memory:c7500000-c7503fff
wolvee@wolvee-dv7:~$ 

```

**After doing this, the problem is still there. The only change is that when I unplug the external speakers from the Headphone jack, I do get sound from the internal laptop speakers.   ....some progress, I guess.**

---

### Post by Sxynerd on 2013-01-21
I just noticed that while using "pavucontrol" I have the option of selecting Port: Speakers or Headphones

This is where it gets strange:

Under "Speakers" the built in Sub-woofer (Beats audio) underneath the laptop plays the sound. (Only that speaker)

Under "Headphones" the rest of the built in speakers work and the built in Subwoofer nose not.





Strange.


I should also say that Ubuntu has not been able to control All 5 speakers since, 11.04.  I just considered it a lost cause.

Here is a screenshot running Alsa, sound is currently only being played from the "Bass Speaker".
[http://i44.photobucket.com/albums/f33/wolvee123/Screenshot_zpsb4e0f675.png](http://i44.photobucket.com/albums/f33/wolvee123/Screenshot_zpsb4e0f675.png)
There is no option other sound cards.

---

### Post by Sxynerd on 2013-01-22
This sucks, all I did was an update, lol.  I think it's a sick attempt from Canonical make people go to 12.10. 

I had similar issues back when I was using 11.04, did some random updates and it broke packages forcing me into 12.04 and now they're doing it again, with a different Computer and a different problem.

---

### Post by Sxynerd on 2013-01-23
Can anyone advise me what to do?

Or at least tell me what update not to do and I'll reformat and reinstall 12.04.

---

### Post by Afro86 on 2013-01-23
Here is what I am doing to solve the issue (temporary fix). In a terminal, start up alsamixer

$  alsamixer

You will see a number of sound spectrum bars.   Using the arrow keys on your keyboard, scroll through each of the spectrum bars.  Your headset should be on speaker 1 (but this may be different on your laptop).  You can increase the sound setting by using the up/down arrows. 

If your headphone/speaker has been turned off by Ubuntu during standby/update, you should see a mute flag:   "MM".  While on the spectrum bar, press "M" on your keyboard to toggle this off/on.   Also check to see if the Master speaker spectrum bar also shows the mute flag. If so toggle this as well by pressing "M".

If on HP Pavilion dv7, then the little light on the F12 key should turn blue.  Exit alsamixer,

Enjoy the sound in your headphone. 

Cheers,

B

---

### Post by Sxynerd on 2013-01-26
So nothing has worked except Reinstalling 12.04 and NOT updating the Audio.  Here are a list of updates I did not install.  I don't have the patience to install one by one till the problem happens again.

---

### Post by Afro86 on 2013-01-26
Now have a permanent fix by doing this:

**$ sudo nano /usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones.conf**

   [COLOR="Orange"]# look for the following lines[/COLOR]
   [INDENT][Element Speaker]
   switch = off
   volume = off[/INDENT]

   [COLOR="Orange"]# change the above lines so that they look like this[/COLOR]
   [INDENT][Element Speaker]
   switch = mute
   volume = zero[/INDENT]

[COLOR="Orange"]# repeat the process for the second headphone configuration file[/COLOR]

**$ sudo nano /usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones-2.conf**

[COLOR="Orange"]# look for the following lines[/COLOR]
   [INDENT][Element Speaker]
   switch = off
   volume = off[/INDENT]

   [COLOR="Orange"]# change the above lines so that they look like this[/COLOR]
   [INDENT][Element Speaker]
   switch = mute
   volume = zero[/INDENT]

Reboot the machine -- and this should work.  NOTE:  I am on HP Pavilion dv7 - Ubuntu 12.04 LTS, 64 bit.  If the above does not do the trick on your machine, you may also have to enable the line for [Element Front] in the same manner as above (in both configuration files).

B.

---

### Post by Sxynerd on 2013-01-28
I can't believe that worked.  Thanks for the help.

Does your DV7 have Beats audio?

Have you gotten your built in Base speaker to work with the other onboard speakers?

):P

---

### Post by T_W on 2013-01-29
**[SIZE="4"]Hallelujah[/SIZE]**, the fix to analog-output-headphones.conf worked for me as well.  

How did you find this information and more importantly, does Canonical know about this bug?

Dear Canonical, 

I am **much** more likely to buy music from your music store or MP3's via your 'shopping lens' if my PC is **[SIZE="4"]actually able to play sounds[/SIZE]**.

It really has **all** been **downhill** for Ubuntu multimedia since PulseAudio was brought onboard *sigh*

---

### Post by Afro86 on 2013-02-06
[SOLVED] ... see below

> **Afro86 said:**
> Now have a permanent fix by doing this:

**$ sudo nano /usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones.conf**

   [COLOR=Orange]# look for the following lines[/COLOR][INDENT][Element Speaker]
   switch = off
   volume = off[/INDENT][COLOR=Orange]# change the above lines so that they look like this[/COLOR][INDENT][Element Speaker]
   switch = mute
   volume = zero[/INDENT][COLOR=Orange]# repeat the process for the second headphone configuration file[/COLOR]

**$ sudo nano /usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones-2.conf**

[COLOR=Orange]# look for the following lines[/COLOR][INDENT][Element Speaker]
   switch = off
   volume = off[/INDENT][COLOR=Orange]# change the above lines so that they look like this[/COLOR][INDENT][Element Speaker]
   switch = mute
   volume = zero[/INDENT]Reboot the machine -- and this should work.  NOTE:  I am on HP Pavilion dv7 - Ubuntu 12.04 LTS, 64 bit.  If the above does not do the trick on your machine, you may also have to enable the line for [Element Front] in the same manner as above (in both configuration files).

B.

---

