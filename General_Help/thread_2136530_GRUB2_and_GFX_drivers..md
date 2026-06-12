---
title: "GRUB2 and GFX drivers."
date: 2013-04-17
forum: General Help
---

### Post by pingaan on 2013-04-17
Hi,

I've been searching and trying a few different things but I can't seem to sort it out.
I would like to have my GFX drivers loaded with GRUB2. It's Nvidia I'm using.

Anyone who knows what to add to grub.cfg?

Cheers.

---

### Post by oldfred on 2013-04-18
Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'
> `GRUB_GFXMODE'
     Set the resolution used on the `gfxterm' graphical terminal.  Note
     that you can only use modes which your graphics card supports via
     VESA BIOS Extensions (VBE), so for example native LCD panel
     resolutions may not be available.  The default is `auto', which
     tries to select a preferred resolution.  *Note gfxmode::.


   From a grub command line to see available settings
vbeinfo

   vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)
"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

After any changes to /etc/default/grub
sudo update-grub

---

