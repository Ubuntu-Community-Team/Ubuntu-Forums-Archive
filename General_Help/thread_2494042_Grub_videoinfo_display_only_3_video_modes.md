---
title: "Grub videoinfo display only 3 video modes"
date: 2024-01-03
forum: General Help
---

### Post by rodride on 2024-01-03
Hi,

Grub videoinfo display only 3 video modes :
```

0x000  800x600x32
0x001  1024x768x32
0x002  1280x1024x32 

```

My video card is a Nvidia GTX 970 with 2560x1440 screen resolution.

Thanks for your help to fix that

---

### Post by MAFoElffen on 2024-01-03
What is the problem? What are you trying to do? It is supported by NVidia and many Linux Distro's...

You have not mentioned that you are trying to use Ubuntu or any of it's flavors. You have not mentioned anything about it being installed, nor trying to run from any installer LiveUSB. Nor if you have used nomodeset, nor tried to installed a driver (current would be nvidia-driver-535). You have not mentioned what it is running on, nor the display... Nor if you are trying to set it to a desired resolution, etc, etc, etc...

So if you reread your first post, you understand by that how we might be confused?

Maybe if you also include running the system-info script in my signature line and post the URL of where it uploads, along with the answers to what you are trying to do, and having difficulties doing, we might be able to help you. That would be a good start at that. That report answers a lot of those questions, on what you have and how it is set up.

---

### Post by rodride on 2024-01-03
i'm running ubuntu 23.10 with nvidia driver 545.29.06 and a screen resolution of 2560x1440

I'm trying to change the resolution of the grub menu and the plymouth screen and
with the grub videoinfo command, I get a maximum resolution of 1280x1024x32 .

How can I get a higher resolution?

---

### Post by MAFoElffen on 2024-01-03
Here is mine in my /etc/default.grub file:
```

mafoelffen@Mikes-ThinkPad-T520:~$ grep 'GRUB_CMDLINE_LINUX_DEFAULT' /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="-- splash intel_kvm.nested=1 [COLOR=#ff0000]video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank[/COLOR] intel_iommu=on systemd.unified_cgroup_hiercharchy=0 intremap=no_x2apic_optout nox2apic

```
That sets the framebuffer that stays in that mode through kernel KMS, until the Video Graphics Drivers take over after the Linux Graphics Layer comes up...

I use 
```

xrandr -q

``` 
In an Xorg session to see what that see's for the display's modes... Then set to that.

If you go to post #2 of the Graphics Resolution Sticky in my signature line, that has links to instructions on how to do many of those things. The video set in the grub file is in the first post, about halfway through it. The first half of that first post explains how that works.

---

### Post by rodride on 2024-01-06
Thanks it worked for the plymouth screen.

But is it possible to make the grub videoinfo command return more video modes so that I can apply a higher resolution close to the native resolution of my system?

---

### Post by MAFoElffen on 2024-01-06
Before I answer that, so I don't forget, what year did your system come out? (How old is it?)

That is sort of a "complicated" question.

I could just say "No" and leave it at that. But that would not explain the how and why of that, and why other things just work or don't.

Grub2's videoinfo and vdeinfo just report the modes that the BIOS reports back, through one of it's backend video drivers. vbeinfo is for Legacy BIOS and videoinfo is for UEFI BIOS. Those video drivers are listed in file /boot/grub/video.lst or alternately in /boot/grub/x86_64-efi/video.lst.
```

efi_gop
efi_uga
video_bochs
video_cirrus

```
The modes reported by those utilities are the modes that you can set fro the Grub2 menu by setting the GRUB_GFXMODE variable.

The Grub2 video driver variable GRUB_GFXMODE is set by default to auto:
> Set the resolution used on the ‘gfxterm’ graphical terminal. Note that you can only use modes which your graphics card supports via VESA BIOS Extensions (VBE), so for example native LCD panel resolutions may not be available. The default is ‘auto’, which tries to select a preferred resolution. See gfxmode.
GFXMODE:
> If this variable is set, it sets the resolution used on the ‘gfxterm’ graphical terminal. Note that you can only use modes which your graphics card supports via VESA BIOS Extensions (VBE), so for example native LCD panel resolutions may not be available. The default is ‘auto’, which selects a platform-specific default that should look reasonable. Supported modes can be listed by ‘videoinfo’ command in GRUB.

The resolution may be specified as a sequence of one or more modes, separated by commas (‘,’) or semicolons (‘;’); each will be tried in turn until one is found. Each mode should be either ‘auto’, ‘widthxheight’, or ‘widthxheightxdepth’. 
What auto also does is sets the search for a working video driver to auto, which tries different drivers until it finds on that works. You can set that directly to a Grub2 video driver by setting the Variable GRUB_VIDEO_BACKEND... Using on of the video drivers i video.lst

framebuffer and KMS can extend those video modes just past the initial graphics mode for the boot messages and splash... To use Framebuffer video modes and extended VESA Modes.

The Linux kernel FrameBuffer drivers are listed here: [https://docs.kernel.org/fb/index.html](https://docs.kernel.org/fb/index.html)

KMS is described here: [https://wiki.debian.org/KernelModesetting](https://wiki.debian.org/KernelModesetting) There used to be a page in the Ubuntu Wiki that was the definitive guide on that, that is now, somehow missing. 

But both those come in after the kernel is booting... The Grub2 menu comes up before that stage.

There is another answer. But that answer has nothing to do with Grub2, it's drivers, nor it's utilities. It has to do with updated BIOS'es and EFI GOP drivers from graphics card vendors.

Some Graphics cards vendors, such as EVGA, when pressed, have provided updated EFI GOP drivers for "their" cards. After 2019, many motherboard vendors have provided better EFI GOP drivers in their UEFI BIOS images to look at the firmware of the BIOS on the Graphics cards. Then the firmware of the graphics cards have to include a good EFI GOP driver. The problem there was that many of the drivers they provided before that date, didn't work if SecureBoot was enabled... I guess that was forced and a good thing about the arrival of Windows 11.
RE:
[https://www.nvidia.com/en-us/geforce/forums/geforce-graphics-cards/5/212870/nvidia-cards-with-uefi-gop-vbios/](https://www.nvidia.com/en-us/geforce/forums/geforce-graphics-cards/5/212870/nvidia-cards-with-uefi-gop-vbios/)
[https://wiki.osdev.org/GOP](https://wiki.osdev.org/GOP)
[https://www.techpowerup.com/vgabios/](https://www.techpowerup.com/vgabios/)
[https://forum-en.msi.com/index.php?threads/monitor-off-until-load-windows-and-i-cannot-enter-to-bios.376027/post-2129551](https://forum-en.msi.com/index.php?threads/monitor-off-until-load-windows-and-i-cannot-enter-to-bios.376027/post-2129551)
[https://forum-en.msi.com/index.php?threads/blackscreen-issue-after-enabling-safe-mode-in-msconfig.376085/post-2129755](https://forum-en.msi.com/index.php?threads/blackscreen-issue-after-enabling-safe-mode-in-msconfig.376085/post-2129755)

And some people have hacked their BIOS images to include better EFI GOP drivers.

*** So if the EFI GOP driver in the BIOS image included the resolutions that were capable by your hardware, then videoinfo and vbeinfo would report them correctly... Still meaning that those two utilities are reporting correctly, and their hands are tied by the drivers underneath that on your hardware.

I hope this post explained that in an understandable way.

---

### Post by rodride on 2024-01-14
Yes my system is old (10 years ago)
Thanks for your explanations

---

### Post by julian552 on 2024-05-22
Hi, thanks for the solution it helps me too.

---

