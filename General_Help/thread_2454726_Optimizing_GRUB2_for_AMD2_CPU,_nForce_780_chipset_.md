---
title: "Optimizing GRUB2 for AMD2 CPU, nForce 780 chipset and Fermi GPU"
date: 2020-12-04
forum: General Help
---

### Post by bcschmerker on 2020-12-04
As of December 2020 I am doing pre-installation testing of a resto-modded *e*machines®/ac*e*r® EL1210-09 (Acer Computer Corp. DA078L:  Advanced Micro Devices Athlon LE-1620 (AMD2) currently installed, Athlon x2 BE-2400 (AMD2) shortlisted for upgrade; nVIDIA® nForce® 785 MCP (integrated 64-bit geForce® GPU by-passed); msi® GT610-1GD3-LP (nVIDIA® GF119 GPU, 1 GiB VRAM)) and have a need to ascertain what modes the GF119 will support in Grand Unified Bootloader 2.04 and subsequent (package **grub-pc**; EFI not relevant this system).  Had to install the nVIDIA 390 driver set for Kernel 5.4.0-*nn*-generic due to a quirk in the nF785 MCP; nouveau will NOT complete shutdowns and/or restarts.  I'd like to be able to support Kernel 5.4.0-*nn*-lowloatency should that become a necessity.  In /etc/default/grub, what options should I consider for appends to GRUB_CMDLINE_LINUX_DEFAULT (currently ="debug"), GRUB_GFXMODE (currently =640x480), and GRUB_GFXPAYLOAD_LINUX (currently =1280x1024, highest supported resolution in GRUB for the GF119 to drive 1680x1050*max*px display units such as the Gateway®/ac*e*r®HD2201); and what, if any, additional amendments to /etc/default/grub and/or related preconfig files used by /usr/sbin/update-grub and/or /usr/sbin/update-initramfs?

---

### Post by bcschmerker on 2020-12-30
**Discovered solution on my own:**  The Kernel loads the VESA BIOS Extension mode quite early in the boot process.  The final /etc/default/grub (comments redacted):
```
GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_TIMEOUT_STYLE=hidden
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_EARLY_INITRD_LINUX_STOCK="microcode.cpio"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="vga=775"
GRUB_BACKGROUND="ubuntu_GRUB2_Splash1.png"
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
#GRUB_TERMINAL=console
GRUB_GFXMODE=1280x1024x8
GRUB_GFXTERM_FONT="u_vga16.pf2"
GRUB_GFXPAYLOAD_LINUX=text
#GRUB_DISABLE_LINUX_UUID=true
#GRUB_DISABLE_RECOVERY="true"
GRUB_INIT_TUNE="480 880 1"
```

---

### Post by bcschmerker on 2021-04-01
**Late-breaking addendum:**  I did some additional tuning to the Boot parameters.  ACPI complains about nvidia-340 not present, but I found nvidia-340 to hang the EL1210; judging from nVIDIA Corporation's non-support of Tesla and sooner in LinUX Kernels 5.8.0-*-*, I'm treating nvidia-340 as a WontFix.  Working with a buggy BIOS (Acer Computer Inc. never released an upgrade to fix the ACPI tables), I have GRUB tuned as follows (comments redacted):
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null  || echo Debian`
GRUB_EARLY_INITRD_STOCK=microcode.cpio
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="agp=off lp=off acpi_rev_override amd_iommu=off atkbd.set=3"
GRUB_VIDEO_BACKEND=vbe
GRUB_BACKGROUND="/boot/grub/images/ubuntu_GRUB2_Splash1.png"
GRUB_GFXMODE=1024x768x8
GRUB_GFXPAYLOAD_LINUX=keep
GRUB_INIT_TUNE="480 440 1"

```The planar nVIDIA C77 rev. a2 works fine on the X.org VESA Driver in the limited capacity I assigned it.  Eventually I'll have to replace the GF119 with a GK208, nVIDIA Corporation intending to pull the plug on Fermi support in Kernel 5.10.

---

