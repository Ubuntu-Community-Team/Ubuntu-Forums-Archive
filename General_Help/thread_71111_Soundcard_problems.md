---
title: "Soundcard problems"
date: 2005-10-02
forum: General Help
---

### Post by rollebolle on 2005-10-02
Hi, 
are you willing to help me with my souncard problems? I have really tried a lot of different ways, maybe the biggest problem is that I'm a beginner with Linux and really don't understand all that I find at different forums. At the moment I think I have problems with Alsa, if I write "alsaconf" i get the answer:  command not found. I have tried to reinstall the alsa-parts from add/remove programs/advanced.

Modprobe gives the following: Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-o <modname>] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]

and modinfo sb gives: filename:       /lib/modules/2.6.10-5-386/kernel/sound/oss/sb.ko
description:    OSS Soundblaster ISA PnP and legacy sound driver
license:        GPL
parm:           io:Soundblaster i/o base address (0x220,0x240,0x260,0x280)
parm:           irq:IRQ (5,7,9,10)
parm:           dma:8-bit DMA channel (0,1,3)
parm:           dma16:16-bit DMA channel (5,6,7)
parm:           mpu_io:MPU base address
parm:           type:You can set this to specific card type (doesn't work with pnp)
parm:           sm_games:Enable support for Logitech soundman games (doesn't work with pnp)
parm:           esstype:ESS chip type (doesn't work with pnp)
parm:           acer:Set this to detect cards in some ACER notebooks (doesn't work with pnp)
parm:           pnp:Went set to 0 will disable detection using PnP. Default is 1.

vermagic:       2.6.10-5-386 preempt 386 gcc-3.3
depends:        sb_lib
srcversion:     4278BCEB17DA25853F492D0

I have allocated an older computer for this linux testing, I think I have a SB 16 soundcard on this. Everything else is running smooth so I don't want to try another distribution and please don't ask me to go back to Windows...:confused:

---

### Post by mlomker on 2005-10-02
The most useful thing is to run **alsamixer** and make sure that the levels and inputs are properly configured.  [Here is a checklist.]("http://linux.iuplog.com/default.asp?item=94639")

---

