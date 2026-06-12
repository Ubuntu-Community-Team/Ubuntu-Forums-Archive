---
title: "Sound not working properly in Ubuntu 14.04.5 LTS"
date: 2016-09-08
forum: General Help
---

### Post by twiskle on 2016-09-08
Hi,


This is my firstpost here on the forum, so please bear with me :)


I have been usingubuntu for several years now, but I have only been using it for dataprocessing. Thus, I didn't have much knowledge in the rest of linuxenvironment.


Lately I have movedto a new lab with a computer that has dual-boot: Windows and Linux.The sound works fine in the Windows system. However, the sounddoesn't play properly in the Linux environment. I can hear the sound,but it is very quiet even after turning the volume to maximum (triedwith pauvcontrol and alsamixer). I have been told that the previouslab member might have deleted some driver files by mistake whentrying to upgrade the OS from 12.04 to 14.04.5.


I have been tryingto fix this issue by searching online for solutions. I have triedreinstalling pulseaudio, pauvcontrol, playing around with alsamixer,and editing the alsa-base.conf by following this page([https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)),but so far nothing works.


I have found asimilar problem from another user([https://ubuntuforums.org/showthread.php?t=2248544](https://ubuntuforums.org/showthread.php?t=2248544)).I didn't type in the commands from this post because I don't knowwhat it means, and whether it applicable to my situation.


The following is theoutput of my system. Any input is much appreciated!


Motherboard:Alienware (Area-51 R2) 0XJKKD
OS: Ubuntu 14.04.5LTS


Audio Adapter:HDA-Intel-HDA Intel PCH


******************************outputof pulseaudio


E: [pulseaudio]pid.c: Daemon already running.
**E: [pulseaudio]main.c: pa_pid_file_create() failed.**


******************************outputof lspci -v


00:1b.0 Audiodevice: Intel Corporation C610/X99 series chipset HD Audio Controller(rev 05)
	Subsystem: DellDevice 064c
	Flags: bus master,fast devsel, latency 0, IRQ 38
	Memory at fb310000(64-bit, non-prefetchable) [size=16K]
	Capabilities:<access denied>
	Kernel driver inuse: snd_hda_intel


00:1f.2 RAID buscontroller: Intel Corporation SATA Controller [RAID mode] (rev 05)
	Subsystem: DellDevice 064c
	Flags: bus master,66MHz, medium devsel, latency 0, IRQ 34
	I/O ports at f070[size=8]
	I/O ports at f060[size=4]
	I/O ports at f050[size=8]
	I/O ports at f040[size=4]
	I/O ports at f000[size=32]
	Memory at fb316000(32-bit, non-prefetchable) [size=2K]
	Capabilities:<access denied>
	Kernel driver inuse: ahci


03:00.1 Audiodevice: NVIDIA Corporation GM204 High Definition Audio Controller(rev a1)
	Subsystem: NVIDIACorporation Device 1116
	Physical Slot: 6
	Flags: bus master,fast devsel, latency 0, IRQ 37
	Memory at fb080000(32-bit, non-prefetchable) [size=16K]
	Capabilities:<access denied>
	Kernel driver inuse: snd_hda_intel


******************************outputof aplay -l:




**** List ofPLAYBACK Hardware Devices ****
**card 0: PCH [HDAIntel PCH], device 0: CA0132 Analog [CA0132 Analog]**
  **Subdevices:0/1**
  **Subdevice #0:subdevice #0**
card 0: PCH [HDAIntel PCH], device 1: CA0132 Digital [CA0132 Digital]
  Subdevices: 1/1
  Subdevice #0:subdevice #0
card 1: NVidia [HDANVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0:subdevice #0
card 1: NVidia [HDANVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0:subdevice #0
card 1: NVidia [HDANVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0:subdevice #0
card 1: NVidia [HDANVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0:subdevice #0

---

### Post by twiskle on 2016-09-08
******************************ALSA-info (only a portion of it, since it is too long to post in here):


name=moji&type=33&description=/tmp/alsa-info.txt&expiry=&s=Submit+Post&content=
!!################################
!!ALSA Information Script v 0.4.64
!!################################
!!Script ran on: Thu Sep 8 14:47:42 UTC 2016
!!Linux Distribution
!!------------------
!!DMI Information
!!---------------
Manufacturer: Alienware
Product Name: Alienware Area-51 R2
Product Version:
Firmware Version: A01
!!Kernel Information
!!------------------
Kernel release: 4.4.0-36-generic
Operating System: GNU/Linux
Architecture: x86_64
Processor: x86_64
SMP Enabled: No
!!ALSA Version
!!------------
Driver version: k4.4.0-36-generic
Library version: 1.0.27.2
Utilities version: 1.0.27.2
!!Loaded ALSA modules
!!-------------------
snd_hda_intel
snd_hda_intel
!!Sound Servers on this system
!!----------------------------
!!Soundcards recognised by ALSA
!!-----------------------------
0 [PCH ]: HDA-Intel - HDA Intel PCH
HDA Intel PCH at 0xfb310000 irq 38
1 [NVidia ]: HDA-Intel - HDA NVidia
HDA NVidia at 0xfb080000 irq 37
!!Modprobe options (Sound related)
!!--------------------------------
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
snd_hda_intel: model=pch position_fix=1
snd_hda_intel: patch=hda-jack-retask.fw,hda-jack-retask.fw,hda-jack-retask.fw,hda-jack-retask.fw
!!Loaded sound module options
!!---------------------------
!!Module: snd_hda_intel
-ne
align_buffer_size : -1
-ne
bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne
beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
-ne
enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
-ne
enable_msi : -1
-ne
id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
-ne
index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne
jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
-ne
model : pch,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
-ne
patch : hda-jack-retask.fw,hda-jack-retask.fw,hda-jack-retask.fw,hda-jack-retask.fw,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
-ne
position_fix : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne
power_save : 0
-ne
power_save_controller : Y
-ne
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne
probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
-ne
single_cmd : N
-ne
snoop : -1
!!Module: snd_hda_intel
-ne
align_buffer_size : -1
-ne
bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne
beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
-ne
enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
-ne
enable_msi : -1
-ne
id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
-ne
index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne
jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
-ne
model : pch,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
-ne
patch : hda-jack-retask.fw,hda-jack-retask.fw,hda-jack-retask.fw,hda-jack-retask.fw,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
-ne
position_fix : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne
power_save : 0
-ne
power_save_controller : Y
-ne
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne
probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
-ne
single_cmd : N
-ne
snoop : -1
!!HDA-Intel Codec information
!!---------------------------
--startcollapse--
Codec: Creative CA0132
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x11020011
Subsystem Id: 0x1028064c
Revision Id: 0x100918
No Modem Function Group found
Default PCM:
rates [0x0]:
bits [0x0]:
formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
Power states: D0 D3 D3cold S3D3cold CLKSTOP EPSS
Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=1, wake=1
Node 0x02 [Audio Output] wcaps 0x49d: Stereo Amp-Out
Device: name="CA0132 Analog", type="Audio", device=0
Amp-Out caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
Amp-Out vals: [0x5e 0x5e]
Converter: stream=5, channel=0
PCM:
rates [0x5e4]: 16000 44100 48000 88200 96000 192000
bits [0x1f]: 8 16 20 24 32
formats [0x1]: PCM
Unsolicited: tag=00, enabled=0
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x49d: Stereo Amp-Out
Amp-Out caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
Amp-Out vals: [0x5a 0x5a]
Converter: stream=0, channel=0
PCM:
rates [0x5e4]: 16000 44100 48000 88200 96000 192000
bits [0x1f]: 8 16 20 24 32
formats [0x1]: PCM
Unsolicited: tag=00, enabled=0
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x49d: Stereo Amp-Out
Amp-Out caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
Amp-Out vals: [0x5a 0x5a]
Converter: stream=0, channel=0
PCM:
rates [0x5e4]: 16000 44100 48000 88200 96000 192000
bits [0x1f]: 8 16 20 24 32
formats [0x1]: PCM
Unsolicited: tag=00, enabled=0
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x691: Stereo Digital
Control: name="IEC958 Playback Con Mask", index=0, device=0
Control: name="IEC958 Playback Pro Mask", index=0, device=0
Control: name="IEC958 Playback Default", index=0, device=0
Control: name="IEC958 Playback Switch", index=0, device=0
Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
Device: name="CA0132 Digital", type="SPDIF", device=1
Converter: stream=0, channel=0
Digital: Non-Copyright
Digital category: 0x0
IEC Coding Type: 0x0
PCM:
rates [0x5e0]: 44100 48000 88200 96000 192000
bits [0x1e]: 16 20 24 32
formats [0x5]: PCM AC3
Unsolicited: tag=00, enabled=0
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x691: Stereo Digital
Converter: stream=0, channel=0
Digital:
Digital category: 0x0
IEC Coding Type: 0x0
PCM:
rates [0x5e0]: 44100 48000 88200 96000 192000
bits [0x1e]: 16 20 24 32
formats [0x5]: PCM AC3
Unsolicited: tag=00, enabled=0
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Node 0x07 [Audio Input] wcaps 0x10059b: Stereo Amp-In
Device: name="CA0132 Analog", type="Audio", device=0
Amp-In caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
Amp-In vals: [0xe2 0xe2]
Converter: stream=0, channel=0
SDI-Select: 0
PCM:
rates [0x1e4]: 16000 44100 48000 88200 96000
bits [0x1f]: 8 16 20 24 32
formats [0x1]: PCM
Unsolicited: tag=00, enabled=0
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x12
Node 0x08 [Audio Input] wcaps 0x10059b: Stereo Amp-In
Control: name="Analog-Mic2 Capture Volume", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Control: name="Analog-Mic2 Capture Switch", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Device: name="CA0132 Analog Mic-In2", type="Audio", device=2
Amp-In caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
Amp-In vals: [0x63 0x63]
Converter: stream=0, channel=0
SDI-Select: 0
PCM:
rates [0x1e4]: 16000 44100 48000 88200 96000
bits [0x1f]: 8 16 20 24 32
formats [0x1]: PCM
Unsolicited: tag=00, enabled=0
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x11
Node 0x09 [Audio Input] wcaps 0x100791: Stereo Digital
Control: name="IEC958 Capture Switch", index=0, device=0
Control: name="IEC958 Capture Default", index=0, device=0
Device: name="CA0132 Digital", type="SPDIF", device=1
Converter: stream=0, channel=0
SDI-Select: 0
Digital: Enabled
Digital category: 0x0
IEC Coding Type: 0x0
PCM:
rates [0x1f0]: 32000 44100 48000 88200 96000
bits [0x1a]: 16 24 32
formats [0x1]: PCM
Unsolicited: tag=00, enabled=0
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x0e
Node 0x0a [Audio Input] wcaps 0x10079b: Stereo Digital Amp-In
Control: name="What U Hear Capture Volume", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Control: name="What U Hear Capture Switch", index=0, device=0
ControlAmp: chs=3, dir=In, idx=0, ofs=0
Device: name="CA0132 What U Hear", type="Audio", device=4
Amp-In caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
Amp-In vals: [0x63 0x63]
Converter: stream=0, channel=0
SDI-Select: 0
Digital:
Digital category: 0x0
IEC Coding Type: 0x0
PCM:
rates [0x1ec]: 16000 22050 44100 48000 88200 96000
bits [0x1b]: 8 16 24 32
formats [0x1]: PCM
Unsolicited: tag=00, enabled=0
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x13
Node 0x0b [Pin Complex] wcaps 0x400581: Stereo
Pincap 0x00010014: OUT EAPD Detect
EAPD 0x2: EAPD
Pin Default 0x01014010: [Jack] Line Out at Ext Rear
Conn = 1/8, Color = Green
DefAssociation = 0x1, Sequence = 0x0
Pin-ctls: 0x40: OUT
Unsolicited: tag=05, enabled=1
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x02
Node 0x0c [Pin Complex] wcaps 0x400701: Stereo Digital
Pincap 0x00000010: OUT
Pin Default 0x014580f0: [Jack] SPDIF Out at Ext Rear
Conn = Optical, Color = Purple
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x40: OUT
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x05
Node 0x0d [Pin Complex] wcaps 0x400701: Stereo Digital
Pincap 0x00000010: OUT
Pin Default 0x014570f0: [Jack] SPDIF Out at Ext Rear
Conn = Optical, Color = Yellow
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x00:
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x06
Node 0x0e [Pin Complex] wcaps 0x400681: Stereo Digital
Pincap 0x00000020: IN
Pin Default 0x01c530f0: [Jack] SPDIF In at Ext Rear
Conn = Optical, Color = Blue
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=00, enabled=0
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Node 0x0f [Pin Complex] wcaps 0x400581: Stereo
Pincap 0x0000001c: OUT HP Detect
Pin Default 0x0221401f: [Jack] HP Out at Ext Front
Conn = 1/8, Color = Green
DefAssociation = 0x1, Sequence = 0xf
Pin-ctls: 0x00:
Unsolicited: tag=06, enabled=1
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x04
Node 0x10 [Pin Complex] wcaps 0x400581: Stereo
Pincap 0x0000001c: OUT HP Detect
Pin Default 0x02216011: [Jack] HP Out at Ext Front
Conn = 1/8, Color = Orange
DefAssociation = 0x1, Sequence = 0x1
Pin-ctls: 0x00:
Unsolicited: tag=01, enabled=1
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x03
Node 0x11 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Amp-In vals: [0x00 0x00]
Pincap 0x00003734: IN OUT Detect
Vref caps: HIZ 50 GRD 80 100
Pin Default 0x02012014: [Jack] Line Out at Ext Front
Conn = 1/8, Color = Grey
DefAssociation = 0x1, Sequence = 0x4
Pin-ctls: 0x24: IN VREF_80
Unsolicited: tag=04, enabled=1
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Node 0x12 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
Control: name="Mic1-Boost (30dB) Capture Switch", index=0, device=0
ControlAmp: chs=1, dir=In, idx=0, ofs=0
Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Amp-In vals: [0x00 0x00]
Pincap 0x00003724: IN Detect
Vref caps: HIZ 50 GRD 80 100
Pin Default 0x37a791f0: [Jack] Mic at Oth Mobile-In
Conn = Analog, Color = Pink
DefAssociation = 0xf, Sequence = 0x0
Misc = NO_PRESENCE
Pin-ctls: 0x24: IN VREF_80
Unsolicited: tag=02, enabled=1
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Node 0x13 [Pin Complex] wcaps 0x400681: Stereo Digital
Pincap 0x00000020: IN
Pin Default 0x908700f0: [Fixed] Line In at Int N/A
Conn = Analog, Color = Unknown
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x20: IN
Unsolicited: tag=00, enabled=0
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Node 0x14 [Beep Generator Widget] wcaps 0x70040c: Mono Amp-Out
Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
Amp-Out vals: [0x1c]
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Node 0x15 [Vendor Defined Widget] wcaps 0xf00600: Mono Digital
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Node 0x16 [Vendor Defined Widget] wcaps 0xf00680: Mono Digital
Unsolicited: tag=03, enabled=1
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Node 0x17 [Audio Output] wcaps 0x49d: Stereo Amp-Out
Amp-Out caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
Amp-Out vals: [0x5a 0x5a]
Converter: stream=0, channel=0
PCM:
rates [0x5ec]: 16000 22050 44100 48000 88200 96000 192000
bits [0x1f]: 8 16 20 24 32
formats [0x1]: PCM
Unsolicited: tag=00, enabled=0
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Node 0x18 [Pin Complex] wcaps 0x400581: Stereo
Pincap 0x00000010: OUT
Pin Default 0x500000f0: [N/A] Line Out at Int N/A
Conn = Unknown, Color = Unknown
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=00, enabled=0
Power states: D0 D3 EPSS
Power: setting=D0, actual=D0
Connection: 1
0x17
Codec: Nvidia GPU 71 HDMI/DP
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de0071
Subsystem Id: 0x10de1116
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
rates [0x0]:
bits [0x0]:
formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
Power states: D0 D1 D2 D3 CLKSTOP EPSS
Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
Control: name="IEC958 Playback Con Mask", index=0, device=0
Control: name="IEC958 Playback Pro Mask", index=0, device=0
Control: name="IEC958 Playback Default", index=0, device=0
Control: name="IEC958 Playback Switch", index=0, device=0
Control: name="ELD", index=0, device=3
Pincap 0x09000094: OUT Detect HBR HDMI DP
Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
Conn = Digital, Color = Unknown
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=01, enabled=1
Connection: 4
0x08* 0x09 0x0a 0x0b
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
Control: name="IEC958 Playback Con Mask", index=1, device=0
Control: name="IEC958 Playback Pro Mask", index=1, device=0
Control: name="IEC958 Playback Default", index=1, device=0
Control: name="IEC958 Playback Switch", index=1, device=0
Control: name="ELD", index=0, device=7
Pincap 0x09000094: OUT Detect HBR HDMI DP
Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
Conn = Digital, Color = Unknown
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=02, enabled=1
Connection: 4
0x08* 0x09 0x0a 0x0b
Node 0x06 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
Control: name="IEC958 Playback Con Mask", index=2, device=0
Control: name="IEC958 Playback Pro Mask", index=2, device=0
Control: name="IEC958 Playback Default", index=2, device=0
Control: name="IEC958 Playback Switch", index=2, device=0
Control: name="ELD", index=0, device=8
Pincap 0x09000094: OUT Detect HBR HDMI DP
Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
Conn = Digital, Color = Unknown
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=03, enabled=1
Connection: 4
0x08* 0x09 0x0a 0x0b
Node 0x07 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
Control: name="IEC958 Playback Con Mask", index=3, device=0
Control: name="IEC958 Playback Pro Mask", index=3, device=0
Control: name="IEC958 Playback Default", index=3, device=0
Control: name="IEC958 Playback Switch", index=3, device=0
Control: name="ELD", index=0, device=9
Pincap 0x09000094: OUT Detect HBR HDMI DP
Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
Conn = Digital, Color = Unknown
DefAssociation = 0xf, Sequence = 0x0
Pin-ctls: 0x00:
Unsolicited: tag=04, enabled=1
Connection: 4
0x08* 0x09 0x0a 0x0b
Node 0x08 [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
Converter: stream=5, channel=0
Digital: Enabled GenLevel
Digital category: 0x2
IEC Coding Type: 0x0
PCM:
rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
bits [0xe]: 16 20 24
formats [0x5]: PCM AC3
Unsolicited: tag=00, enabled=0
Node 0x09 [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
Converter: stream=0, channel=0
Digital:
Digital category: 0x0
IEC Coding Type: 0x0
PCM:
rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
bits [0xe]: 16 20 24
formats [0x5]: PCM AC3
Unsolicited: tag=00, enabled=0
Node 0x0a [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
Converter: stream=0, channel=0
Digital:
Digital category: 0x0
IEC Coding Type: 0x0
PCM:
rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
bits [0xe]: 16 20 24
formats [0x5]: PCM AC3
Unsolicited: tag=00, enabled=0
Node 0x0b [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
Converter: stream=0, channel=0
Digital:
Digital category: 0x0
IEC Coding Type: 0x0
PCM:
rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
bits [0xe]: 16 20 24
formats [0x5]: PCM AC3
Unsolicited: tag=00, enabled=0
--endcollapse--

---

