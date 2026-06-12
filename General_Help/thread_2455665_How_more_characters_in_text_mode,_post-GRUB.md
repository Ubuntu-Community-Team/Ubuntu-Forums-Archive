---
title: "How more characters in text mode, post-GRUB?"
date: 2020-12-24
forum: General Help
---

### Post by bcschmerker on 2020-12-24
I've at least two systems running LinUX Kernel 5.4.0 as of 24 December 2020, and I'd like to give Root a larger text field for offline maintenance sans X11.  Both systems default to 640x480px with 8x16px characters in single-user mode; target is 1280x1024px (with a fallback option to 1024x768px) with 8x16px characters.  I don't see an overall display pixels option in console-setup.  So how does one set a larger "terminal" in a VESA-standard video display adapter?

---

### Post by CatKiller on 2020-12-24
It depends primarily on your graphics card, but also on your display and UEFI. 

If you're using UEFI mode you'll have more and higher resolutions available than if you're using Legacy/CSM mode. With Legacy you'll get whichever modes the graphics card manufacturer bothered to put into the emulated VBE, which might not actually work on your display. With UEFI you'll get the modes supported by KMS. 

The parameter you're looking for is GRUB_GFXMODE.

---

### Post by bcschmerker on 2020-12-28
[@CatKiller](https://ubuntuforums.org/member.php?u=65401)  **The Hot Rod gPC's GIGABYTE® GA-MA78GM-S2HP, whose ATi® RS780G 64-bit GPU is still supported, predates the widespread use of UEFI.**  In "recovery mode," the gfxmode parameter (in /boot/grub/grub.cfg) has no effect.  Suspect that, in /etc/default/grub, I'd have to use a "vga=(integer)" parameter in the GRUB_CMDLINE_LINUX target.  Additionally, the *e*machines®/ac*e*r® EL1210-09 that I'm preparing for projector duty, which also predates the widespread use of UEFI, has the same "recovery mode" (mis?)behavior with an *msi*® GT610-1GD3-LP VDA (nVIDIA® GF119 GPU). (The nVIDIA C77 integrated *geForce*® GPU in the *nForce*® 785 MCP chipset is no longer supported; the entire chipset is only partially supported in all LinUX Kernels 5.*x* without the nVIDIA-390 modules.)

---

### Post by CatKiller on 2020-12-28
If you're restricted to BIOS mode then there's a command that you can run from the Grub shell - vbeinfo, I think, although it's been a while - that will list the modes that are available through the emulated VBE. Then, yes, you'd pass the name of the mode you want to use as a video= parameter. You might not have your display's native mode available, but you should be able to fit more characters on the screen. Don't forget to update-grub after configuration file changes, although you can experiment with different configurations as a one-off from the Grub menu if that's quicker.

---

### Post by bcschmerker on 2020-12-30
**Discovered solution on my own:**  The Kernel executes VESA mode numbers (decimal) quite early in the boot process.  Whereas GRUB_CMDLINE_LINUX="video=1280x1024-8" *did not* increase resolution in Recovery Mode (as the Kernel doesn't make it to the 32-bit KMS procedure under such conditions), GRUB_CMDLINE_LINUX="vga=775" *did*, therefore gave me the 160x52-character console I set for goal.  Considering issue RESOLVED FIXED.

**Addition:**  The solution that worked on the EL1210 needed a mod on the Hot Rod, as the ATi® RS780G uses different SVGA modes.  As adjusted (comments redacted):
```
GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_TIMEOUT_STYLE=hidden
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_EARLY_INITRD_LINUX_STOCK=microcode.cpio
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="vga=838" # Kernel warning but executes properly
GRUB_BACKGROUND=/boot/grub/splashimages/ubuntu_GRUB2_Splash1.png
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
#GRUB_TERMINAL=console
GRUB_GFXMODE=auto
GRUB_GFXTERM_FONT=/boot/grub/fonts/u_vga16.pf2
GRUB_GFXPAYLOAD_LINUX=text
#GRUB_DISABLE_LINUX_UUID=true
#GRUB_DISABLE_RECOVERY="true"
GRUB_INIT_TUNE="480 440 1"

```

---

