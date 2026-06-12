---
title: "[SOLVED] Screen fades after loading hardware drivers on boot"
date: 2008-02-19
forum: General Help
---

### Post by Tails9 on 2008-02-19
I read a thread about making Ubuntu boot faster while I was on xp, so (stupid as it was) I tried to apply the steps to my configuration. Unfortunately I only completed step 1 and 2 because I had to be in Ubuntu to do step 3.

After that, when booting the screen fades in a low depth after loading the hardware drivers.
The GDM is garbled, so I can't get much further. Same thing happens in recovery mode.
These were the steps:

[quote="Orange2k"] Originally Posted by orange2k  View Post
I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

**step 1**: edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

**step 2**: edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

**step 3**: sudo update-initramfs -u[/quote]

I've already reverted what I changed, but the problem persists.
This is what my dmsg says just before the screen fades: 
```
nvidiafb: PCI nVidia NV29 framebuffer (64MB @ 0xC0000000)
[   70.848102] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 16
[   70.848114] ACPI: PCI Interrupt 0000:04:08.0[A] -> Link [LNKA] -> GSI 16 (level, low) -> IRQ 16
[   70.851621] Installing spdif_bug patch: Audigy 2 ZS [SB0350]
[   70.947420] nvidia: module license 'NVIDIA' taints kernel.
[   71.222488] NVRM: The NVIDIA probe routine was not called for 1 device(s).
[   71.222494] NVRM: This can occur when a driver such as rivafb, nvidiafb or
[   71.222496] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
[   71.222498] NVRM: device(s).
[   71.222501] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel module
[   71.222503] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
[   71.222504] NVRM: support), then try loading the NVIDIA kernel module again.
[   71.222592] NVRM: No NVIDIA graphics adapter probed!
```

(Needless to say, I have a Nvidia card)

Could anyone help me with this? I think I've suffered enough being back on xp for half a week :)

---

### Post by Tails9 on 2008-02-20
I reinstalled the kernel (made no difference), but after I removed everything from Nvidia, I got this in my dmsg:

```
63.469000] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 17
[   63.469055] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNEA] -> GSI 17 (level, low) -> IRQ 17
[   63.469188] nvidiafb: Device ID: 10de0292 
[   63.486340] nvidiafb: CRTC0 analog found
[   63.502305] nvidiafb: CRTC1 analog not found
[   63.619314] usbcore: registered new interface driver xpad
[   63.619360] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   63.774191] nvidiafb: EDID found from BUS1
[   64.022045] nvidiafb: EDID found from BUS2
[   64.022105] nvidiafb: CRTC 1 is currently programmed for DFP
[   64.022144] nvidiafb: Using DFP on CRTC 1
[   64.022181] nvidiafb: Panel size is 1920 x 1200
[   64.022218] nvidiafb: Panel is TMDS
[   64.022650] nvidiafb: MTRR set to ON
[   64.022931] nvidiafb: PCI nVidia NV29 framebuffer (64MB @ 0xC0000000)
[   64.025361] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 16
[   64.025417] ACPI: PCI Interrupt 0000:04:08.0[A] -> Link [LNKA] -> GSI 16 (level, low) -> IRQ 16

```

What do the interrupts mean? Should I try to install all the nvidiadrivers now?

---

### Post by Tails9 on 2008-02-20
After reading alot, I guess I have to compile the kernel without the nvidiafb module, 
because I'd like to use the official nvidia drivers so I can run compiz (again), but this time without XGL (so I have direct rendering (so the videotearing will be gone) ).

---

### Post by Tails9 on 2008-03-02
I recompiled the kernel without the framebuffer support, reinstalled the nvidiadrivers with envy and the problem is gone.

---

