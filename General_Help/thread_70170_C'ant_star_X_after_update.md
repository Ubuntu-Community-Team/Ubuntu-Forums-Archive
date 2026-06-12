---
title: "C'ant star X after update"
date: 2005-09-29
forum: General Help
---

### Post by quique on 2005-09-29
After an update I c'ant start the X window. I think he problem is the nvidia driver. Here are the Xorg.0.log. Thanks in advance.

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TVStandard" "PAL-B"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "TwinView"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "30-50"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "60"
(**) NVIDIA(0): Option "MetaModes" "1280x1024, 1024x768; 800x600, 800x600; 640x480, 640x480;"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Enabling experimental RENDER acceleration
(**) NVIDIA(0): TV Standard string: "PAL-B"
(**) NVIDIA(0): TwinView enabled
(--) NVIDIA(0): Linear framebuffer at 0xF0000000
(--) NVIDIA(0): MMIO registers at 0xED000000
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by heimo on 2005-09-29
My guess is that your kernel version has changed, you use nvidias proprietary drivers and need to reinstall those. To get temporarily back to X you can change nvidia to nv or vesa in /etc/X11/xorg.conf

EDIT: More obvious way to get back to X is to use the old version of kernel (probably in grub menu, use esc at the very beginning of boot). Not sure about that.

---

### Post by rjwood on 2005-09-29
which nvidia driver do you have installed?

---

### Post by quique on 2005-09-29
How can I known?

---

### Post by rjwood on 2005-09-29
Have you downloaded any drivers from nvidia site? If not you may want to try installing nvivia-glx;

sudo apt-get install nvidia-glx

then hit ctrl>alt>backspace to try to restart x

If you have any other nvidia drivers installed you may have to remove them first

If it works you can go to the ubuntu guide to install the settings

---

### Post by quique on 2005-09-29
OK, thats the correct way to restart X.

Thanks

---

