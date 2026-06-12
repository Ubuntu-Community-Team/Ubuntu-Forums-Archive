---
title: "Thinkpad p16 gen 2, Ub 24.04, Internal display GUI only works with discrete graphics"
date: 2024-08-04
forum: General Help
---

### Post by Ranbunta_Bantubunt on 2024-08-04
My Thinkpad P16 gen 2 internal display only works with graphical desktops when Discrete graphics are selected. When hybrid graphics are selected in BIOS, everything is OK until the graphical desktop environment tries to  launch, then the internal display freezes with an underscore character in  upper left corner in text mode. The HDMI out continues to work.

I ordered this computer from Lenovo with custom specs, with Ubuntu 22.04, but when it came, actually there was no OS installed at all. I confirmed this carefully. Anyway it's ok, I went ahead and installed Ubuntu 24.04 without a problem and it worked ok for a while. They advertised it as coming with Ubuntu 22.04 (when I specced it out), so it should work with 22.04; since there was actually no OS at all, I installed 24.04 instead of 22.04, and it worked fine for a long time. 

After initially setting it up, with internal monitor working fine with hybrid graphics and a graphical desktop environment (both Gnome desktop originally and later Cinnamon), I went to clamshell mode and used it exclusively in clamshell with an external HDMI monitor, which also worked ok. 

After a long time of clamshell only (HDMI out only), I needed to take the laptop somewhere and discovered the internal monitor did not actually work any more as soon as the graphical desktop manager started. In other words, everything is OK until the graphical desktop environment tries to launch, then internal display freezes with an underscore character in upper left corner in text mode. The HDMI out continues to work. So I am not sure when the internal monitor stopped being functional with graphical environments as I was clamshell only for a few months. Unfortunately it could be tied to a specific thing I did or a specific install or uninstall that I did, but I don't know what it would be as I didn't detect it before due to the fact that I only clamshelled it. 

The one method I've found of getting the internal display to work with a graphic environment is to set graphics mode to discrete graphics in BIOS. However, the problems with that include that I don't get the onboard sound, and Virtualbox doesn't want to launch my VMs with discrete graphics. 

I've done all of the following trying to get the internal display to show a GUI with hybrid graphics with no success:

-Used both GDM and LightDM with Gnome and Cinnamon desktop environments, with wayland and X11 each
-All sorts of command line defaults in Grub, including the following and variants thereof (currently commented, but I used them before)

```

#GRUB_CMDLINE_LINUX_DEFAULT="i915.force_probe=a788 i915.modeset=1 nvidia-drm.modeset=1 i915.enable_guc=3"
#GRUB_CMDLINE_LINUX_DEFAULT="nomodeset i915.force_probe=a788"
#GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1 acpi_backlight=vendor intel_iommu=on acpi_osi=\"Windows 2015\""
#GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1 acpi_osi=Linux acpi_backlight=vendor intel_iommu=on"
#GRUB_CMDLINE_LINUX_DEFAULT="nvidia-drm.modeset=1 i915.modeset=1 acpi_osi=Linux"
#GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux nvidia-drm.modeset=1 btusb.enable_autosuspend=0 intel_iommu=on i915.modeset=1 acpi_backlight=vendor"
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
#GRUB_CMDLINE_LINUX_DEFAULT=""
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset split_lock_detect=off"
```

-Set prime to intel, NVIDIA, blacklisted intel or NVIDIA and tried to boot with one or the other that way
-Reinstalled NVIDIA drivers in recovery mode after scorched earth purging of all traces of the prior installs using both NVIDIA's .run file and the apt-get repos
-Reinstalled lightdm, gdm, cinnamon, gnome desktop, xorg, etc. after scorched earth purging of all traces of prior installs
-Tried the following kernels:
ii  linux-image-6.8.0-38-generic                   6.8.0-38.38                                amd64        Signed kernel image generic
ii  linux-image-6.8.0-39-generic                   6.8.0-39.39                                amd64        Signed kernel image generic
ii  linux-image-6.9.12-x64v3-xanmod1  
-Run apt-get update & apt-get upgrade, and purged and reinstalled every related package I can think of numerous times

I'm at a loss here about how to proceed. I know it *can* work because when I did a fresh install, it did work, but I am out of ideas. I could do a fresh reinstall, though that would take a long time (especially with disk encryption), and may not even solve the problem or let me know how to avoid it happening again. 

FWIW, here are the results of  [COLOR=#0000ff]$ journalctl -b 0 | grep -i -e nvidia -e intel -e gpu, from my current session with discrete graphics selected. 

[/COLOR]```

[COLOR=#000000][FONT=Droid Sans Mono][COLOR=#0000ff]Journal file /var/log/journal/3896cb836fb54877836a1c5b0928ffc1/system@00061e84932b9110-fcfc2bf59397404f.journal~ is truncated, ignoring file.[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:39 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Command line[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] BOOT_IMAGE=/vmlinuz-6.8.0-39-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro i915.force_probe=a788 i915.modeset=1 nvidia-drm.modeset=1 i915.enable_guc=3[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:39 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff]   Intel GenuineIntel[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:39 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Kernel command line[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] BOOT_IMAGE=/vmlinuz-6.8.0-39-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro i915.force_probe=a788 i915.modeset=1 nvidia-drm.modeset=1 i915.enable_guc=3[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:39 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] smpboot[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] CPU0[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] 13th Gen Intel(R) Core(TM) i9-13950HX (family[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] 0x6, model[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] 0xb7, stepping[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] 0x1)[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:39 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Performance Events[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] XSAVE Architectural LBR, PEBS fmt4+-baseline,  AnyThread deprecated, Alderlake Hybrid events, 32-deep LBR, full-width counters, Intel PMU driver.[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:39 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] DMAR[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Intel(R) Virtualization Technology for Directed I/O[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:39 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] intel_pstate[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Intel P-state driver initializing[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:39 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] intel_pstate[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] HWP enabled[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:39 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] intel-lpss 0000:00:15.0[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] enabling device (0000 -> 0002)[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:39 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] idma64 idma64.0[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Found Intel integrated DMA 64-bit[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:39 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] intel-lpss 0000:00:15.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] enabling device (0000 -> 0002)[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:39 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] idma64 idma64.1[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Found Intel integrated DMA 64-bit[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] input[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Intel HID events as /devices/platform/INTC1070:00/input/input18[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] intel_pmc_core INT33A1:00[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff]  initialized[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] intel_rapl_msr[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] PL4 support detected.[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Intel(R) Wireless WiFi driver for Linux[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] intel_rapl_common[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Found RAPL domain package[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] intel_rapl_common[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Found RAPL domain core[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] intel_rapl_common[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Found RAPL domain psys[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] snd_hda_intel 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] DSP detected with PCI class/subclass/prog-if info 0x040380[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] snd_hda_intel 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Digital mics found on Skylake+ platform, using SOF driver[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] snd_hda_intel 0000:01:00.1[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] enabling device (0000 -> 0002)[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] snd_hda_intel 0000:01:00.1[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Disabling MSI[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] snd_hda_intel 0000:01:00.1[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Handle vga_switcheroo audio client[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] intel_rapl_common[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Found RAPL domain package[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] input[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input19[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] input[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input20[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] input[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input21[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] input[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input22[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] iwlwifi 0000:00:14.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Detected Intel(R) Wi-Fi 6E AX211 160MHz, REV=0x430[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] DSP detected with PCI class/subclass/prog-if info 0x040380[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Digital mics found on Skylake+ platform, using SOF driver[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] DSP detected with PCI class/subclass/prog-if 0x040380[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] use msi interrupt mode[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] nvidia[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] loading out-of-tree module taints kernel.[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] nvidia[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] module license 'NVIDIA' taints kernel.[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] nvidia[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] module license taints kernel.[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] hda codecs found, mask 1[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] using HDA machine driver skl_hda_dsp_generic now[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] DMICs detected in NHLT tables[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] 2[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Firmware paths/files for ipc type 0[/COLOR][COLOR=#cd3131]:[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff]  Firmware file[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff]     intel/sof/sof-rpl-s.ri[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff]  Topology file[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff]     intel/sof-tplg/sof-hda-generic-2ch.tplg[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Firmware info[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] version 2:2:0-57864[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Firmware[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] ABI 3:22:1 Kernel ABI 3:23:0[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] unknown sof_ext_man header type 3 size 0x30[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] nvidia-nvlink[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Nvlink Core is being initialized, major device number 511[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] nvidia 0000:01:00.0[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] enabling device (0006 -> 0007)[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] nvidia 0000:01:00.0[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] vgaarb[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] VGA decodes changed[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] olddecodes=io+mem,decodes=none:owns=none[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Firmware info[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] version 2:2:0-57864[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] sof-audio-pci-intel-tgl 0000:00:1f.3[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Firmware[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] ABI 3:22:1 Kernel ABI 3:23:0[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] intel_tcc_cooling[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Programmable TCC Offset detected[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] NVRM[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] loading NVIDIA UNIX x86_64 Kernel Module  535.183.01  Sun May 12 19:39:15 UTC 2024[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] nvidia-modeset[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  535.183.01  Sun May 12 19:31:08 UTC 2024[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:40 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] [drm] [nvidia-drm] [GPU ID 0x00000100] Loading driver[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:41 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Bluetooth[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] hci0[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Found device firmware[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] intel/ibt-1040-0041.sfi[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:41 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:01:00.0 on minor 1[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:41 comp systemd[1][/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Starting systemd-backlight@backlight:nvidia_0.service - Load/Save Screen Backlight Brightness of backlight:nvidia_0...[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:41 comp systemd[1][/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Finished systemd-backlight@backlight:nvidia_0.service - Load/Save Screen Backlight Brightness of backlight:nvidia_0.[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:41 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] nvidia_uvm[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] module uses symbols nvUvmInterfaceDisableAccessCntr from proprietary module nvidia, inheriting taint.[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:41 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] nvidia-uvm[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Loaded the UVM driver, major device number 508.[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:42 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Bluetooth[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] hci0[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Found Intel DDC parameters[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] intel/ibt-1040-0041.ddc[/COLOR]
[COLOR=#0000ff]Aug 04 00:36:42 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Bluetooth[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] hci0[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Applying Intel DDC parameters completed[/COLOR]
[COLOR=#0000ff]Aug 04 00:38:09 comp systemd[1][/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Starting gpu-manager.service - Detect the available GPUs and deal with any system changes...[/COLOR]
[COLOR=#0000ff]Aug 04 00:38:09 comp systemd[1][/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Starting nvidia-persistenced.service - NVIDIA Persistence Daemon...[/COLOR]
[COLOR=#0000ff]Aug 04 00:38:09 comp nvidia-persistenced[2311][/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Verbose syslog connection opened[/COLOR]
[COLOR=#0000ff]Aug 04 00:38:09 comp nvidia-persistenced[2311][/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Now running with user ID 125 and group ID 130[/COLOR]
[COLOR=#0000ff]Aug 04 00:38:09 comp nvidia-persistenced[2311][/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Started (2311)[/COLOR]
[COLOR=#0000ff]Aug 04 00:38:09 comp nvidia-persistenced[2311][/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] device 0000:01:00.0 - registered[/COLOR]
[COLOR=#0000ff]Aug 04 00:38:09 comp nvidia-persistenced[2311][/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Local RPC services initialized[/COLOR]
[COLOR=#0000ff]Aug 04 00:38:09 comp systemd[1][/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Started nvidia-persistenced.service - NVIDIA Persistence Daemon.[/COLOR]
[COLOR=#0000ff]Aug 04 00:38:09 comp systemd-logind[2346][/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Watching system buttons on /dev/input/event10 (Intel HID events)[/COLOR]
[COLOR=#0000ff]Aug 04 00:38:09 comp sensors[2371][/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] GPU[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff]          +42.0°C[/COLOR]
[COLOR=#0000ff]Aug 04 00:38:10 comp systemd[1][/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] gpu-manager.service[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Deactivated successfully.[/COLOR]
[COLOR=#0000ff]Aug 04 00:38:10 comp systemd[1][/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] Finished gpu-manager.service - Detect the available GPUs and deal with any system changes.[/COLOR]
[COLOR=#0000ff]Aug 04 01:44:34 comp kernel[/COLOR][COLOR=#cd3131]:[/COLOR][COLOR=#0000ff] [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000100] Failed to grab modeset ownership[/COLOR][/FONT][/COLOR]

```

It's difficult to know if any particular entry has any significance as the more I vary all the various things I can vary, various messages and errors come up in the logs and change depending on the setup, but repsonding to all of them doesn't seem to fix the issue. :(

Any really smart people know how I can troubleshoot further? Thanks!

---

### Post by euol on 2024-08-05
If Ubuntu is updated and drivers are updated, you can try this:

sudo nano /etc/default/grub

Add or modify the following parameters to handle hybrid graphics issues: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on nvidia-drm.modeset=1"

sudo update-grub

---

### Post by Ranbunta_Bantubunt on 2024-08-06
> **euol said:**
> If Ubuntu is updated and drivers are updated, you can try this:

sudo nano /etc/default/grub

Add or modify the following parameters to handle hybrid graphics issues: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on nvidia-drm.modeset=1"

sudo update-grub

Thanks for the suggestion. I had previously essentially tried that plus some other parameters, as you see above one of the grub command lines I tried was: 
```
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1 acpi_osi=Linux acpi_backlight=vendor intel_iommu=on"

```So it was  almost the same as what you are suggesting, however, your suggestion  brings back splash and gets rid of the acpi_osi=Linux and  acpi_backlight=vendor items, so not quite the same, so I went ahead and tried it, and unfortunately I am still experiencing the same behavior. 

Any high-level, 20,000 foot ideas about what may be going on here? 

I really love my new ThinkPad, but still not at the point of getting it up and running smoothly.

---

### Post by whytigr on 2024-09-09
_**HISTORY**_:
We've been experiencing something similar when building P1Gen6 and P16Gen2 laptops for our clients. The main problem *seems* to be, a microcode load is blocking for what seems like forever on either the iGPU or the network adapter. I have not seen an actual log of the failure because most people are too impatient and reboot FAR before that, then in either case reinstall without gathering logs. I do, however, have a picture of it puking on the screen when it finally gave up the ghost though. If you leave it alone for long enough, (reportedly 24hrs+), a lot of the time the host will eventually blowup and spit the microcode load failure screen and freeze. After power cycling, it will recover and will now allow access to the frame-buffer so it can boot into the GUI.

_**WHILE YOU ARE SUFFERING**_:
Please note that when you are seeing the black screen with the cursor at top-left, you do have console access should you choose to use it.. Press CTRL+ALT+F3 (or CTRL+ALT+FN+F3 in you didn't switch the f-keys to be f-keys) and you will get a login prompt.  You can do whatever, you just wont have GDM access yet. install the linux-modules-extra package for the current kernel and it will work.  It will be gimped and you'll see hardware badness and unknown devices though, but it will finally boot.  Check /boot for any other kernels that need linux-modules-extra for and install them manually now, or you'll just need to reboot back to the previous kernel and do it anyway.

_**USEFUL INFO YOU WISH YOU HAD BEFORE YOU BOUGHT THESE:**_
This following URL is very foreboding and basically says if you bought this laptop and you want Ubuntu to work, then you should have had it preloaded, except you can't because Lenovo yanked support for it after their failed 6.5.1(6.5.0) BIOS code.  Support was there 2 weeks ago.. Here is the URL for the remnant (immediately following the Ubuntu URL)

[https://ubuntu.com/certified/202307-31822](https://ubuntu.com/certified/202307-31822)
[https://download.lenovo.com/pccbbs/mobiles/n3tur04w.html](https://download.lenovo.com/pccbbs/mobiles/n3tur04w.html)

_**SEMI_WORKING RESOLUTION (YMMV):**_
A *MUCH* faster way to make Ubuntu 22.04.4 on the P16Gen2 is to reset to BIOS defaults, (keep hybrid graphics on) ... set TXT ON, RAM encryption ON, VMD OFF, enable all three toggles in the UEFI Options, enable Secure Boot and 3rd party CAs. Do not delete Canonical's DBx entry and do not put the computer into secure boot setup mode (unless you have a MOK cert and know what you're doing with that). Make sure that you are using the SB shims from at least a 24.04 installer (obtained from the shim-signed 1.58+15.8 package in Ubuntu noble/24.04 or 1.51.4+15.8-0ubuntu1 on Jammy/22.04.4) for the initial boot,  Please do NOT forget to give all of your warm heartfelt thanks to MS for screwing over most Linux users with their SBAT update on 13Aug2024. 

_**REITERATIONS:**_
The** oem-sutton repo** is specifically made for supporting the various forms of Lenovo hardware and functionality. Load it before or at first boot. If you have an Ubuntu pro subscription, attach to it as early as possible and update the sources.list. Enable live patching if you are so entitled. When all that completes, install: ubuntu-advantage-utils, ubuntu-pro-client, shim-signed, mokutil, dkms, build-essential, and as per the above URL, linux-image-6.1.0-1036-oem + headers + modules-extra, Blacklist/remove+purge vdpau and nouveau. Install NVidia-535 drivers. Finally, after all of that is done, you *should* be ready to reboot. If you're lucky, everything applied and you'll not only resolve MS SBAT, but you'll have frame-buffer/GUI access and most importantly network functionality, too! 

Best of luck to you.  Feel free to post your results. Maybe we can completely beat this thing and make it a dead horse we can beat some more!

FYI -- This is not limited to these 2 laptop models.  I also had it happen on a P7 3-NVidia GPU build.  I am guessing it has something to do with SBAT and NVidia, but I haven't been able to make that concrete link yet.  Still digging just as you are.

---

### Post by sgriffith23 on 2024-10-06
Turns out, you just need to install the linux-modules-extra package for your kernel.  For some reason it is not installing by default.  If it still doesn't work for you, try the OEM kernel. Just an FYI... The ACPI functionality of this machine is bjorked... Also, WhyTigr is right, you should get the OEM-sutton repo and pro. Also, if you have more than one NVME storage drive and you are using BIOS > 1.51, you will need to boot with kernel parameter noacpi=1 to avoid your NVME slots assigning to different slots whenever you load/reload the NVME kernel module. It shouldn't really matter unless you use the device special files themselves instead of the /dev/disk/* links. E.g. /dev/nvme0n1, /dev/nvme1n1, etc.  But if your ids are seemingly swapping, turn off ACPI. It forces use of SMBios to discover the devices.
 
You probably should *NOT* use discrete mode, it is known to destroy computers :(
If you are using your CUDA cores for anything other than graphics, I recommend you use the Intel video board for your display.

Good luck friends!

---

