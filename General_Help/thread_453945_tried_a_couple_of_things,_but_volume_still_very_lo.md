---
title: "tried a couple of things, but volume still very low"
date: 2007-05-24
forum: General Help
---

### Post by wolfen69 on 2007-05-24
when i run- lspci -v and aplay -l,
i get this:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at dc240000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

then did modprobe, here are the results:

don@don-laptop:~$ sudo modprobe snd-
Display all 151 possibilities? (y or n)
snd-ac97-codec      snd-es1688          snd-opti93x
snd-ad1816a         snd-es1688-lib      snd-page-alloc
snd-ad1848          snd-es18xx          snd-pcm
snd-ad1848-lib      snd-es1938          snd-pcm-oss
snd-ad1889          snd-es1968          snd-pcxhr
snd-adlib           snd-es968           snd-pdaudiocf
snd-ainstr-fm       snd-fm801           snd-rawmidi
snd-ainstr-gf1      snd-gina20          snd-riptide
snd-ainstr-iw       snd-gina24          snd-rme32
snd-ainstr-simple   snd-gusclassic      snd-rme96
snd-ak4114          snd-gusextreme      snd-rme9652
snd-ak4117          snd-gus-lib         snd-rtctimer
snd-ak4531-codec    snd-gusmax          snd-sb16
snd-ak4xxx-adda     snd-gus-synth       snd-sb16-csp
snd-ali5451         snd-hda-codec       snd-sb16-dsp
snd-als100          snd-hda-intel       snd-sb8
snd-als300          snd-hdsp            snd-sb8-dsp
snd-als4000         snd-hdspm           snd-sbawe
snd-atiixp          snd-hwdep           snd-sb-common
snd-atiixp-modem    snd-i2c             snd-seq
snd-au8810          snd-ice1712         snd-seq-device
snd-au8820          snd-ice1724         snd-seq-dummy
snd-au8830          snd-ice17xx-ak4xxx  snd-seq-instr

don@don-laptop:~$ sudo modprobe snd-snd-hda-intel
FATAL: Module snd_snd_hda_intel not found.

does anyone have any suggestions?  volume is very low. when i go into the alsa settings there is no option for setting speaker output.  btw, the computer is Toshiba A-105. laptop.

---

### Post by wolfen69 on 2007-05-25
bump

---

