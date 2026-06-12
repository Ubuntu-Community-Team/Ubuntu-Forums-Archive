---
title: "Problems setting video drivers."
date: 2021-01-29
forum: General Help
---

### Post by Robert_Gaines on 2021-01-29
I installed an NVIDIA GEFORCE GT 1030 video card onto my HP Compaq 8200 Elite tower, and I can't get it to display through the DP port onto my HDTV. I went through hell trying to do a clean install of Ubuntu 20.10, but I finally discovered that you had to install apt during the live disc session to get the installer to not crash. It begins to boot at 640x480, but when it gets to the login screen, the screen turns blue and says "no signal". I think the resolution is unrecognizable to the HDTV. The HDTV resolution limit is 1920x1080, but the card can go up to 4k. I'm thinking it might be set to 4k. I discovered that I could connect a VGA cable to my TV for onboard graphics and get the computer to use VGA if I disabled the PCI Express slot that the video card is in in the BIOS, but I can't seem to change the resolution of the video card when it's disabled in the BIOS. It's one or the other. The video card is only viewable at 640x480 when I use the 440 driver, but I'm supposed to be using the 460 driver. I think it's just not displaying anything because it's the wrong resolution. I need to somehow edit a settings file while I'm using the onboard VGA graphics while the video card is disabled. This is all a complicated nightmare, and I'm beginning to think it wasn't worth it just to play games.

---

### Post by TheFu on 2021-01-29
```
sudo ubuntu-drivers autoinstall
```
is the way to get the best drivers for supported video cards.

After that, remove all other nvidia driver packages.

---

### Post by CelticWarrior on 2021-01-29
As above.

And don't forget to disable Secure Boot in UEFI.

---

### Post by TheFu on 2021-01-29
We should say that DisplayPort and HDMI ask the monitor what resolutions it supports and will not send anything more than the monitor can support.

Of course, any fault in the GPU card, cables, or monitor can break these things, but almost always if something is wrong, it is a bad cable, so just $4 to fix if you don't have a spare.

Funky connection methods - like displayport --> VGA --> KVM-switch --> VGA --> Monitor can have other odd issues, but you didn't mention anything like that.

I have a 1030 nvidia. Upgraded to 18.04 today. Then I forced the HWE kernel to be installed and had to force the nvidia driver install for the 5.4 kernel. Success:
```
$ lsmod |grep nvid
nvidia_uvm            983040  0
nvidia_drm             57344  3
nvidia_modeset       1224704  6 nvidia_drm
nvidia              34037760  399 nvidia_uvm,nvidia_modeset
drm_kms_helper        184320  1 nvidia_drm
drm                   491520  6 drm_kms_helper,nvidia_drm

$ dpkg -l *nvidia*|grep 460
ii  libnvidia-cfg1-460:amd64         460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-460             460.32.03-0ubuntu0.18.04.1 all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-460:amd64      460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA libcompute package
ii  libnvidia-decode-460:amd64       460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-460:amd64       460.32.03-0ubuntu0.18.04.1 amd64        NVENC Video Encoding runtime library
ii  libnvidia-extra-460:amd64        460.32.03-0ubuntu0.18.04.1 amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-460:amd64         460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-460:amd64           460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-460:amd64         460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-460         460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA compute utilities
ii  nvidia-dkms-460                  460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA DKMS package
ii  nvidia-driver-460                460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-460         460.32.03-0ubuntu0.18.04.1 amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-460         460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA kernel source package
ii  nvidia-utils-460                 460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-460    460.32.03-0ubuntu0.18.04.1 amd64        NVIDIA binary Xorg driver
```
Only installed nvidia-dkms-460 nvidia-driver-460 nvidia-utils-460 packages.  With the older kernel, 460 was automatically installed, but not relinked for the newer kernel.  In a few weeks, after another new 5.4.x kernel gets installed, I'll do some cleanup of the 4.15 kernels, modules and headers. The big things seem to be working, post-upgrade, though the video is not refreshing as it should and leaves artifacts behind sometimes.  Firefox is nearly useless - even in safe-mode after  removing all prior profiles, about 80% of the web pages  used daily refuse to load. Even about:config won't display anything.  Chromium (not snap pkg) is working fine.  Ubuntu forums won't display.  The last 18 months, FF has been sorta bad wt all sorts of problems.  When did they switch to Rust?

---

### Post by grahammechanical on 2021-01-29
On boot up the OS interrogates the Monitor to read the EDID information - Extended Display Information Data. That is where the OS/video driver gets the resolution and frequency of the monitor from.

[https://en.wikipedia.org/wiki/Extended_Display_Identification_Data](https://en.wikipedia.org/wiki/Extended_Display_Identification_Data)

[https://help.ubuntu.com/stable/ubuntu-help/look-resolution.html.en](https://help.ubuntu.com/stable/ubuntu-help/look-resolution.html.en)

[https://www.tecmint.com/set-display-screen-resolution-in-ubuntu/](https://www.tecmint.com/set-display-screen-resolution-in-ubuntu/)

> Graham@sdb1-sdb8:~$ xrandr
Screen 0: minimum 16 x 16, current 1920 x 1080, maximum 32767 x 32767
XWAYLAND0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080     29.95*+

Regards

---

### Post by Robert_Gaines on 2021-01-30
I get the feeling that the video card is simply just defective. My TV and the video card are not talking to each other. The onboard graphics over VGA is talking to my TV set. I don't know why the non-recommended video drivers at least produce a 640x480 picture while the correct one produces nothing. Well, it get to the login screen and goes blue. The drivers could simply be incompatible with the card too. I don't know if I can return it. This card probably just belongs in the garbage.

---

### Post by CelticWarrior on 2021-01-30
Have you disabled Secure Boot in UEFI ("BIOS") settings already?

---

### Post by Yellow Pasque on 2021-01-31
> **Robert_Gaines said:**
> I don't know why the non-recommended video drivers at least produce a 640x480 picture while the correct one produces nothing.

640x480 probably means a generic driver is being used (fbdev) rather than the nvidia driver. I wouldn't condemn the hardware yet if it lights up the screen. Make sure SecureBoot is disabled as suggested. It's no use diving into deeper troubleshooting until you do that.

---

### Post by Robert_Gaines on 2021-01-31
I burned a Ubuntu 20.10 amd64 DVD. I originally installed it with a USB drive. There was no legacy install. Rather than attempt to use GParted to get legacy back, I just did it with the install DVD. I verified in the bios that the Legacy was properly set up. I booted it up, and I got a blue, no signal screen still. I feel that was a waste of time. I'm back on onboard VGA again having to set everything back up. I've used different HDMI cables. I don't think all of them are bad.

---

### Post by CelticWarrior on 2021-01-31
Why are you purposefully using legacy?

---

### Post by Robert_Gaines on 2021-02-01
> **CelticWarrior said:**
> Why are you purposefully using legacy?

That's what I thought you told me to do. I dumped the EFI only installation and installed a legacy compatible installation with a disc. Why that would work, I have no idea. All I know is that it didn't.

---

### Post by CelticWarrior on 2021-02-01
No, it absolutely wasn't. I told you to disable Secure Boot, a UEFI exclusive feature, and that can and should be done keeping the UEFI mode installation.
Legacy, as the name suggests is ONLY for legacy OSes and none of that sort is currently supported, not even Windows 7 (that had UEFI support since SP1), so using Legacy in 2021 is ridiculous. Nobody should suggest that, period. I obviously didn't.

Disabling Secure Boot in UEFI is convenient because otherwise users have to manually sign each and every unsigned driver, including Nvidia's.

You need to familiarize yourself with your own firmware and its settings. Understand that you may need to update the firmware even for new systems. And with UEFI and its requirements: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
And understand that although Ubuntu allows UEFI installations in MBR, it probably shouldn't as GPT is preferred (and mandatory for Windows). Take the time to understand all of this and then things will work. Take shortcuts and problems will certainly happen and we can be over this for days, weeks and many pages to accomplish nothing useful.

---

### Post by TheFu on 2021-02-01
There are reasons to use legacy boot today. 
Whether those are good or not, depends on multiple factors. It certainly isn't the end of the world. 
But I do try to use GPT partitioning whenever possible. The good that is GPT vastly outweighs any bad.

UEFI has never seemed worth the issues to me. Certainly not worth going out of my way to switch except if you intend to use secureboot.

---

### Post by Robert_Gaines on 2021-02-02
> **CelticWarrior said:**
> No, it absolutely wasn't. I told you to disable Secure Boot, a UEFI exclusive feature, and that can and should be done keeping the UEFI mode installation.
Legacy, as the name suggests is ONLY for legacy OSes and none of that sort is currently supported, not even Windows 7 (that had UEFI support since SP1), so using Legacy in 2021 is ridiculous. Nobody should suggest that, period. I obviously didn't.

Disabling Secure Boot in UEFI is convenient because otherwise users have to manually sign each and every unsigned driver, including Nvidia's.

You need to familiarize yourself with your own firmware and its settings. Understand that you may need to update the firmware even for new systems. And with UEFI and its requirements: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
And understand that although Ubuntu allows UEFI installations in MBR, it probably shouldn't as GPT is preferred (and mandatory for Windows). Take the time to understand all of this and then things will work. Take shortcuts and problems will certainly happen and we can be over this for days, weeks and many pages to accomplish nothing useful.
  i
The other install was installed over USB, and the Legacy MBR didn't exist. I had to reinstall with a DVD to get the Legacy MBR installed. The secure boot is disabled. Anyway, please don't beat me up over it because I spent many hours trying to get the install to work. It just flat out refused to work, and I did more own research. Coming here was out of desperation after not being able to get anything else to work.

---

### Post by CelticWarrior on 2021-02-02
I'm not beating you up just pointing out the mistakes that seem to be pilling up. A properly installed system in UEFI mode with Secure Boot OFF IS the starting point to the troubleshooting, contrary of what TheFu states above (because he isn't using current hardware). Meaning: If it doesn't work properly with the proprietary drivers installed that's when we dig deeper. Expecting that it'll work in Legacy mode when it doesn't in UEFI mode is absurd.

You say you did your own research but very likely you don't even knew what to look for, this is going by what in terms of knowledge transpires from this thread alone.

Can you please try:
[LIST=1]
[*]Update the motherboard's firmware (UEFI) before anything else (even new computers often need it)
[*]Assure that UEFI only option is set: Security > Secure Boot configuration > Legacy DISABLE
[*]Assure that Secure Boot is disabled: Security > Secure Boot configuration again
[*]At Boot confirm the target drive is the first priority (it should be regardless of the supposedly failed attempts)
[*]Use the one-time boot menu (F9 or ESC then F9) to boot the installation media (the media must be UEFI compatible -> If done with any tool other Rufus in Windows it will be; if using Rufus make sure the options UEFI/GPT are selected before burning the ISO)
[*]Boot a live session (Try Ubuntu)
[*]Before installing open Gparted, make sure the target drive is selected, then Device menu > Create new partition table, select "GPT" (this will clear the entire drive, no need to create partition at this point, the installer will do it automatically later). Exit GParted.
[*]Install -> Make sure the option to install third-party drivers, codecs, etc. is selected
[/LIST]

Optionally, and only if applicable, make sure the addon graphics card is selected instead of the integrated graphics. Yours is a desktop, not a laptop, hybrid graphics isn't a thing in desktops so switchable graphics doesn't apply. It's "either or" and "auto" mode, if applicable, should be avoided as it may revert to the iGPU depending on the connections at that alone can give you the incorrect perception that the Nvidia "isn't working".

Now, this ^^^ is research as I never used or even seen your computer.

Please ask for clarification if you don't understand something.

---

### Post by TheFu on 2021-02-03
Actually, I do have some current hardware - a Ryzen 5 2600. It was a choice NOT to use UEFI for me when doing the install onto the SSD. It is also the machine with an nvidia 1030 GPU.  Post #4 above was run on that system with a 5.4 kernel. Alas, for whatever reason, it doesn't have GPT on the boot disk.  Probably because when choosing LVM in the installer for a default setup, it doesn't/didn't support GPT. It was installed using 16.04 and has been upgraded to 18.04-HWE recently.

---

### Post by Robert_Gaines on 2021-02-09
I eventually found the solution, and it was something I was sure couldn't happen. I ordered a new VGA cable with a combined audio cable that was supposed to be coaxial and HD compliant. Pure garbage. I realized it was crap when the computer didn't recognize me TV. I probably could have worked around that, but the audio being in the cable gave me digital noise too. The Dollar Tree audio cable was actually superior. Anyway, at the same time, I replaced the DP to HDMI cable with an HDMI to HDMI cable. The card also had an HDMI port besides the DP port, but I thought the cable was better quality. It probably wasn't the cable's fault, but I thought just maybe that the card was expecting a computer monitor rather than a TV since I was using the DP port and was formatting it's output for a computer monitor. I mean, HDMI and DP are for the most part passively compatible, so I thought the card would see the TV and act accordingly. Using a standard HDMI cable, the TV was able to display 1080p. I honestly didn't think the ports mattered. I thought both were there for convenience, but output the same signal. That wasn't true. The picture is quite a bit sharper now.

---

