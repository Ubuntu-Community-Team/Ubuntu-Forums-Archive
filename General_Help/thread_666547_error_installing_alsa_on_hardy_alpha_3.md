---
title: "error installing alsa on hardy alpha 3"
date: 2008-01-13
forum: General Help
---

### Post by wiiittttt on 2008-01-13
im having trouble compiling ALSA driver from source. I believe i have all the correct dependencies etc. I do 

```
sudo ./configure --with-cards=emu10k1x --with-sequencer=yes
```

and it works fine, but when i do

```
sudo make
```

i get the following output:

```
adam@adam-ubuntu:/usr/src/alsa/alsa-driver-1.0.15$ sudo make
make dep
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/acore'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/acore/ioctl32'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/acore/ioctl32'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/acore/oss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/acore/oss'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/acore/seq'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/acore/seq/instr'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/acore/seq/instr'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/acore/seq/oss'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/acore/seq/oss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/acore/seq'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/acore'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/i2c'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/i2c/l3'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/i2c/l3'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/i2c/other'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/i2c/other'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/i2c'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/drivers'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/drivers/mpu401'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/drivers/mpu401'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/drivers/opl3'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/drivers/opl3'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/drivers/opl4'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/drivers/opl4'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/drivers/pcsp'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/drivers/pcsp'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/drivers/vx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/drivers/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/drivers'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/isa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/isa/ad1816a'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/isa/ad1816a'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/isa/ad1848'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/isa/ad1848'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/isa/cs423x'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/isa/cs423x'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/isa/es1688'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/isa/es1688'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/isa/gus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/isa/gus'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/isa/msnd'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/isa/msnd'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/isa/opti9xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/isa/opti9xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/isa/sb'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/isa/sb'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/isa/wavefront'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/isa/wavefront'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/isa'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/synth'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/synth/emux'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/synth/emux'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/synth'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/ac97'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/ac97'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/ali5451'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/ali5451'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/asihpi'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/asihpi'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/au88x0'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/au88x0'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/ca0106'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/ca0106'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/cmi8788'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/cmi8788'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/cs46xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/cs46xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/cs5535audio'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/cs5535audio'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/echoaudio'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/echoaudio'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/emu10k1'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/emu10k1'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/hda'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/hda'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/ice1712'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/ice1712'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/korg1212'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/korg1212'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/mixart'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/mixart'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/nm256'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/nm256'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/pcxhr'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/pcxhr'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/pdplus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/pdplus'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/riptide'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/riptide'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/rme9652'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/rme9652'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/trident'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/trident'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/vx222'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/vx222'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pci/ymfpci'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci/ymfpci'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pci'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/aoa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/aoa/codecs'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/aoa/codecs'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/aoa/core'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/aoa/core'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/aoa/fabrics'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/aoa/fabrics'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/aoa/soundbus'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/aoa/soundbus'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/aoa'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/soc'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/soc/at91'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/soc/at91'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/soc/codecs'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/soc/codecs'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/soc/pxa'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/soc/pxa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/soc/s3c24xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/soc/s3c24xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/soc/sh'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/soc/sh'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/soc'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/usb'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/usb/caiaq'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/usb/caiaq'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/usb/usx2y'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/usb/usx2y'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/usb'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pcmcia'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pcmcia/pdaudiocf'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/pcmcia/vx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pcmcia/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/pcmcia'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15/misc'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15/misc'
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15'
make -C /lib/modules/2.6.24-3-generic/build SUBDIRS=/usr/src/alsa/alsa-driver-1.0.15  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-3-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/src/alsa/alsa-driver-1.0.15/acore/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.15/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-3-generic'
make: *** [compile] Error 2

```

please help :(

---

### Post by wiiittttt on 2008-01-13
bump

---

### Post by martinrandau on 2008-01-14
Same problem here. I need to recompile the thing because sound stopped working after the alsa-base package was upgraded, but I get that error.

Soundless again! Argh! :confused:

---

### Post by findparadise on 2008-01-21
I have the same problem.

---

### Post by tensop on 2008-01-31
Using:

[ftp://ftp.suse.com/pub/projects/alsa/snapshot/lib/alsa-lib-hg20080130.tar.bz2](ftp://ftp.suse.com/pub/projects/alsa/snapshot/lib/alsa-lib-hg20080130.tar.bz2) - Alsa Libraries
[ftp://ftp.suse.com/pub/projects/alsa/snapshot/utils/alsa-utils-hg20080122.tar.bz2](ftp://ftp.suse.com/pub/projects/alsa/snapshot/utils/alsa-utils-hg20080122.tar.bz2) - Alsa Utils
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16rc2.tar.bz2) - Alsa Drivers

I was able to get sound etc to compile for my hda-intel acer 5315 integrated audio chipset

I get a "/usr/sbin/alsactl: load_state:1573:no soundcards found..." Error, but the sound appears to work.

---

