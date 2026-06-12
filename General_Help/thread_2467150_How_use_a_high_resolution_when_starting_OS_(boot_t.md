---
title: "How use a high resolution when starting OS (boot terminal details)"
date: 2021-09-17
forum: General Help
---

### Post by aug7744 on 2021-09-17
Using the value in
/etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT=#"quiet splash"

The OS start with boot details in terminal.
When using nouvau driver the screen use high resolution (display monitor being 1366X768 is possible that is using maximum resoltiion).
After if using Nvidia proprietary driver the start boot details in terminal is using a low resolution (display monitor 1366X768 is possible that is using 640X480) with larger font size.

How configure when using nvidia driver a start boot terminal using high resolution ?
I had used in /etc/default/grub GRUB_GFXMODE=640X480X8 and after the boot menu is displayed message "invalid resolution" about that command GRUB_GFXMODE=640X480X8

In /etc/default/grub has that detail
"you can see them in real GRUB with the command `vbeinfo'"
trying the command above not work.

Thanks for your reply.

---

### Post by grahammechanical on 2021-09-17
Grub does not load a video driver. Grub sets a video mode and then loads the Linux kernel. At some point when Linux is in control of the machine the kernel will load a video driver.

The Grub manual says this

> **15.1.12 gfxmode[COLOR=#ff0000][/COLOR]**
 If this variable is set, it sets the resolution used on the &#8216;gfxterm&#8217; graphical terminal.  Note that you [COLOR=#ff0000]can only use modes which your graphics card supports via VESA BIOS Extensions (VBE)[/COLOR], so for example native LCD panel resolutions may not be available.  The default is &#8216;auto&#8217;, which selects a platform-specific default that should look reasonable. Supported modes can be listed by &#8216;videoinfo&#8217; command in GRUB. 

 The resolution may be specified as a sequence of one or more modes, separated by commas (&#8216;,&#8217;) or semicolons (&#8216;;&#8217;); each will be tried in turn until one is found.  Each mode should be either &#8216;auto&#8217;, &#8216;widthxheight&#8217;, or &#8216;widthxheightxdepth&#8217;.


[https://www.gnu.org/software/grub/manual/grub/grub.html](https://www.gnu.org/software/grub/manual/grub/grub.html)

grub.cfg on my system has this entry:

> if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm

The mode is set to "auto."

Regards

---

### Post by aug7744 on 2021-09-21
Thanks for your reply.
Have a nice day.

---

