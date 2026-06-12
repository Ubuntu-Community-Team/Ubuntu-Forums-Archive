---
title: "Need help with audio drivers"
date: 2007-04-30
forum: General Help
---

### Post by DrPppr242 on 2007-04-30
I install Feisty about a week ago and everything had everything working except for a bug where the sound was so quiet it was inaudible, so I tried to install the drivers for my soundcard (it's an onboard sound for an abit IC7 motherboard) and that didn't work and I've spent the last couple days trying and failing to fix it with every sound problem guide I could find none of witch worked.  now the volume control can't find any devices at all can anyone help me get my sound setup?

---

### Post by DrPppr242 on 2007-04-30
went to the alsa wiki and ran aadebug...

> paul@paul-desktop:~/Desktop$ ./aadebug
ALSA Audio Debug v0.1.0 - Mon Apr 30 20:36:06 MST 2007
[http://alsa.opensrc.org/aadebug](http://alsa.opensrc.org/aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux paul-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
cat: /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0p  pcmC0D2c  pcmC0D4p  timer
pcmC0D0c   pcmC0D1c  pcmC0D3c  seq

CPU -------------------------------------------------------
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
cpu MHz         : 3207.431
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
cpu MHz         : 3207.431

RAM -------------------------------------------------------
MemTotal:      1035740 kB
SwapTotal:     1526132 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
02:07.0 Multimedia controller: Motorola DSP56301 Digital Signal Processor (rev 02)


that was the output if that helps.

**I re installed the linux kernel to get things set up still no sound at all but it seems to have the drivers above is what I got when I re-ran aadebug

---

### Post by DrPppr242 on 2007-05-01
Well I got it working after reloading the kernel I install alsa mixer and turned everything up and it worked!

---

