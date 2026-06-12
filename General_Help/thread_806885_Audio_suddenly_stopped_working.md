---
title: "Audio suddenly stopped working"
date: 2008-05-25
forum: General Help
---

### Post by bpont on 2008-05-25
I've suddenly lost audio on my system.  I have a dual boot system and my audio works in xp, so I know it's not a hardware problem.

I use ktorrent and I've noticed it can disable my audio from time to time, so I'm not sure if that's an issue.  I've rebooted several times, but no audio at all.

I've been through the troubleshooting page [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) but it didn't help.

I ran a script that lists audio info and hopefully someone reading it will have a clue to help guide me where to go from here...I'm stumped:

```
ALSA Audio Debug v0.1.0 - Sun May 25 09:43:17 CDT 2008
http://alsa.opensrc.org/aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux dhamma 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_cmipci             38528  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  2 snd_pcm_oss
snd_pcm                78596  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           12928  1 snd_cmipci
snd_hwdep              10500  1 snd_opl3_lib
snd_mpu401_uart         9728  1 snd_cmipci
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9612  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  15 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Apr 21 2008 for kernel 2.6.24-16-generic (SMP).
 0 [CMI8738        ]: CMI8738 - C-Media CMI8738
                      C-Media CMI8738 (model 37) at 0xb800, irq 10
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  8: [ 0- 0]: raw midi
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 18: [ 0- 2]: digital audio playback
 24: [ 0- 0]: digital audio capture
 26: [ 0- 2]: digital audio capture
 33:        : timer
00-00: OPL3 FM
00-02: CMI8738 : C-Media PCI IEC958 : playback 1 : capture 1
00-01: CMI8738 : C-Media PCI 2nd DAC : playback 1
00-00: CMI8738 : C-Media PCI DAC/ADC : playback 1 : capture 1
Client info
  cur  clients : 4
  peak clients : 4
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 15:0
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
Client  15 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1
Client  16 : "C-Media CMI8738" [Kernel]
  Port   0 : "C-Media CMI8738 MIDI" (RWeX)
Client  17 : "OPL3 FM synth" [Kernel]
  Port   0 : "OPL3 FM Port" (-We-)
  Port   1 : "OPL3 OSS Port" (-we-)

Dev Snd ---------------------------------------------------
controlC0  midiC0D0  pcmC0D0p  pcmC0D2c  seq
hwC0D0	   pcmC0D0c  pcmC0D1p  pcmC0D2p  timer

CPU -------------------------------------------------------
model name	: Pentium III (Katmai)
cpu MHz		: 451.032

RAM -------------------------------------------------------
MemTotal:       515608 kB
SwapTotal:     1052216 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:10.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

```

---

### Post by Cerberu2 on 2008-05-25
since you had audio,i thinks thats correctly configurated,you can listen at the same time 2 audio files, with diferentes applications?i had that problem,was a a flash problem, i did this and it worked for me:

>So for you there is an advice - reinstall pulseaudio and libflashplugin support for ex this way : 
apt-get install --reinstall pulseaudio libflashsupport
>Second thing is to change everything to pulseaudio in "system->preferences->audio settings".

---

### Post by bpont on 2008-05-25
> **Cerberu2 said:**
> since you had audio,i thinks thats correctly configurated,you can listen at the same time 2 audio files, with diferentes applications?i had that problem,was a a flash problem, i did this and it worked for me:

>So for you there is an advice - reinstall pulseaudio and libflashplugin support for ex this way : 
apt-get install --reinstall pulseaudio libflashsupport
>Second thing is to change everything to pulseaudio in "system->preferences->audio settings".

I tried your advice, and unfortunately it didn't help.

---

### Post by Cerberu2 on 2008-05-25
it detects sound devices?

---

### Post by bpont on 2008-05-25
> **Cerberu2 said:**
> it detects sound devices?

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
```

```
lspci -v

00:10.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
	Flags: bus master, medium devsel, latency 32, IRQ 10
	I/O ports at b800 [size=256]
	Capabilities: <access denied>

```

---

### Post by Cerberu2 on 2008-05-25
> **bpont said:**
> ```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
```

```
lspci -v

00:10.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
	Flags: bus master, medium devsel, latency 32, IRQ 10
	I/O ports at b800 [size=256]
	Capabilities: <access denied>

```

do you run it with root acess?
"acess denied"?

---

### Post by bpont on 2008-05-25
> **Cerberu2 said:**
> do you run it with root acess?
"acess denied"?


00:10.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at b800 [size=256]
        Capabilities: [c0] Power Management version 2

---

