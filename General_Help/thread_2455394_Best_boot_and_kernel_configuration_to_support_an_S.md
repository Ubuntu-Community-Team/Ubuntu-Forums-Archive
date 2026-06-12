---
title: "Best boot and kernel configuration to support an SB0350 in Wolfdale?"
date: 2020-12-18
forum: General Help
---

### Post by bcschmerker on 2020-12-18
I am currently preparing to install ubuntu® or a derivative on a Gateway®/ac*e*r® DX4822-01 (Acer G43T-AM planar; intel® Pentium Processor® E5300 (FCLGA 775), G43 chipset, integrated HD Graphics X4500) packing 6 GiB main memory and retrofitted with a Creative Laboratories® SB0350 PCI 2.0 audio adapter (Creative Technology CA0102 DSP, ALSA: snd-emu10k1) and SB0250 I/O Drive.  I'm already aware of the 31-bit-DMA hardware bug in the CA0102 and preplanned, for /etc/default/grub:
```
# ...
GRUB_DEFAULT=0
GRUB_TIMEOUT=10
GRUB_TIMEOUT_STYLE=hidden
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_EARLY_INITRD_LINUX_STOCK="microcode.cpio"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="debug memmap=2048M\\$6144M"
# ...
```for the purpose of Generic versus LowLatency kernel testing.  (Real-time pre-emption was deprecated by the Kernel 4.0 series.)  How should I prepare a 64-bit OS in the Kernel 5.4 or 5.8 series; or, should AMD64 be unsat in the face of the 31-bit-DMA bug, a Kernel 4.6 i386 configuration from Release(s) 18.04.7-LTS?

---

