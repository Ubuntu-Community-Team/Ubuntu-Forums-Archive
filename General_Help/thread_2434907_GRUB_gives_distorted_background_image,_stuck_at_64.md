---
title: "GRUB gives distorted background image, stuck at 640x480, and vbeinfo doesn't work"
date: 2020-01-13
forum: General Help
---

### Post by Cursed Lemon on 2020-01-13
Hey all, just wondering if someone could help me with a little GRUB trouble. I'm trying to make GRUB a little prettier, and...well it's all hecked up. 

I've got a video demonstrating the problem I'm having here: [https://streamable.com/ybt7t](https://streamable.com/ybt7t)

Any further information needed, just ask. I've tried setting a direct graphics mode with "vga=0x0318" under GFX_CMDLINE_LINUX_DEFAULT as well as "nomodeset", and I've tried setting GRUB_GFXPAYLOAD_LINUX="keep" to no effect.

---

### Post by CatKiller on 2020-01-13
The old vga= and vbe methods are deprecated in favour of kernel mode setting. The GRUB_GFXMODE= option works with KMS, I understand.

---

### Post by Cursed Lemon on 2020-01-13
> **CatKiller said:**
> The old vga= and vbe methods are deprecated in favour of kernel mode setting. The GRUB_GFXMODE= option works with KMS, I understand.

So, something like [this]("https://wiki.archlinux.org/index.php/kernel_mode_setting#Early_KMS_start")?

---

### Post by CatKiller on 2020-01-13
Yep, that's the stuff. Arch configures its modules differently to Ubuntu, but the information is good. I'm not near my computer to check, but you list the modules you need in a text file - if you need to - and then update-initramfs.

---

### Post by Cursed Lemon on 2020-01-13
> **CatKiller said:**
> Yep, that's the stuff. Arch configures its modules differently to Ubuntu, but the information is good. I'm not near my computer to check, but you list the modules you need - if you need to - and then update-initramfs.

Apparently the Intel stuff is enabled by default and all one is supposed to do is set the GRUB_GFXPAYLOAD_LINUX variable, which I did to no avail.

---

### Post by CatKiller on 2020-01-13
> **Cursed Lemon said:**
> Apparently the Intel stuff is enabled by default and all one is supposed to do is set the GRUB_GFXPAYLOAD_LINUX variable, which I did to no avail.

Well, you've already done stuff that would stop it working. Nomodeset explicitly disables it. You also haven't said that you used GRUB_GFXMODE= to say what resolution you want, nor whether you remembered to run update-grub.

---

### Post by Cursed Lemon on 2020-01-13
> **CatKiller said:**
> Well, you've already done stuff that would stop it working. Nomodeset explicitly disables it. You also haven't said that you used GRUB_GFXMODE= to say what resolution you want, nor whether you remembered to run update-grub.

I deleted **nomodeset **and replaced it with **i915.modeset=1** to try it out. I have **GRUB_GFXMODE=800x600x24** (I can't imagine that's NOT a supported video mode) set in the video, and I've run **update-grub** each time I made a change to experiment. No dice!

---

### Post by CatKiller on 2020-01-13
> **Cursed Lemon said:**
> (I can't imagine that's NOT a supported video mode) 
It's not, necessarily. It all depends on what your hardware exposes. I didn't have to do anything at all on my Intel machine to have Grub and the TTYs at its native 3200×1800 resolution, but I had to do quite a bit of fiddling with my Nvidia machine. *That* one has ```
GRUB_GFXMODE=2560x1600x32,auto
GRUB_GFXPAYLOAD_LINUX=2560x1600x32
GRUB_TERMINAL=gfxterm
```

dmesg may give you some more information on what's going on with your particular machine.

---

### Post by Cursed Lemon on 2020-01-13
Dmesg output can be found [here]("https://pastebin.com/u0Fs89xx").

Output of **hwinfo --framebuffer** is as follows:

```
02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.459]
  Unique ID: rdCR.pRMQb3ydj2D
  Hardware Class: framebuffer
  Model: "Intel(R) VLV Mobile/Desktop Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R) VLV Mobile/Desktop Graphics Controller"
  SubVendor: "Intel(R) VLV Mobile/Desktop Graphics Chipset Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 61 MB + 960 kB
  Memory Range: 0x00000000-0x03deffff (rw)
  Mode 0x0360: 0x0 (+0), 8 bits
  Mode 0x0361: 0x0 (+0), 16 bits
  Mode 0x0362: 0x0 (+0), 24 bits
  Mode 0x0363: 0x0 (+0), 8 bits
  Mode 0x0364: 0x0 (+0), 16 bits
  Mode 0x0365: 0x0 (+0), 24 bits
  Mode 0x0366: 0x0 (+0), 8 bits
  Mode 0x0367: 0x0 (+0), 16 bits
  Mode 0x0368: 0x0 (+0), 24 bits
  Mode 0x0369: 0x0 (+0), 8 bits
  Mode 0x036a: 0x0 (+0), 16 bits
  Mode 0x036b: 0x0 (+0), 24 bits
  Mode 0x036c: 0x0 (+0), 8 bits
  Mode 0x036d: 0x0 (+0), 16 bits
  Mode 0x036e: 0x0 (+0), 24 bits
  Mode 0x036f: 0x0 (+0), 8 bits
  Mode 0x0370: 0x0 (+0), 16 bits
  Mode 0x0371: 0x0 (+0), 24 bits
  Mode 0x033c: 1920x1440 (+1920), 8 bits
  Mode 0x034d: 1920x1440 (+3840), 16 bits
  Mode 0x035c: 1920x1440 (+7680), 24 bits
  Mode 0x033a: 1600x1200 (+1600), 8 bits
  Mode 0x034b: 1600x1200 (+3200), 16 bits
  Mode 0x035a: 1600x1200 (+6400), 24 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x037d: 640x480 (+640), 8 bits
  Mode 0x037e: 640x480 (+1280), 16 bits
  Mode 0x037f: 640x480 (+2560), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown


```

---

### Post by Cursed Lemon on 2020-01-14
Solved the problem! 

Someone on Reddit suggested that I turn on CSM in my BIOS as that solved some similar boot-time problems for them. As it happened, CSM was already on for me...so I did the exact opposite and turned it off (then reinstalled both OS's in UEFI mode just for the heck of it). And that did it, lol 

Now GRUB displays at the laptop's native resolution and the background isn't effed up. So there ya go!

---

