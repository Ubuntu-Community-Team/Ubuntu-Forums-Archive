---
title: "Enable nomodeset in UEFI mode on Live USB?"
date: 2019-05-29
forum: General Help
---

### Post by styne2 on 2019-05-29
I've been trying to install Linux for the first time. I've tried several Linux distros over the last couple weeks, and have issues with every single one.

I finally got Ubuntu to install the other day, by booting the Live USB in BIOS mode and then enabling the "nomodeset" parameter. This means it was installed in BIOS mode, not UEFI.  

My problem now is that I'm experiencing many issues with my installation. When booting, I get black and white stripes as described here([https://askubuntu.com/questions/689729/ubuntu-has-black-stripes-and-white-stripes-all-over-the-place](https://askubuntu.com/questions/689729/ubuntu-has-black-stripes-and-white-stripes-all-over-the-place)), unless I boot in recovery mode. This is all fine, except I'm trying to use this PC for video consumption and the Intel Graphics drivers don't seem to be working properly in recovery mode. This makes for choppy video which is CPU bound, although in windows the CPU has no problem with video. This leads me to believe it's a video driver issue, and may be related to recovery mode boot.

So, the next thing I'm going to try is booting from a UEFI installation. My question is, how do I enable "nomodeset" when booting the Live USB in UEFI mode, as I can only seem to do it in BIOS mode. Any help is really appreciated. 

Thanks, Alex.

---

### Post by oldfred on 2019-05-29
You edit grub.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
See also link below in my signature.

---

