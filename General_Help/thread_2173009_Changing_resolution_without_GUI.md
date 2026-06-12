---
title: "Changing resolution without GUI"
date: 2013-09-07
forum: General Help
---

### Post by hiig on 2013-09-07
At my wits end with this one. I've followed the chosen answer over [here]("http://askubuntu.com/questions/18444/how-do-i-increase-console-mode-resolution") and all it did was change the boot loader to the right resolution (1440x900x8), but as soon as it got to the login, it was back to the tiny 800x600 resolution.

I must have been on the right track if I changed one thing, so what am I missing?

Alongside the instructions in the link, I have also changed GRUB_CMDLINE_LINUX_DEFAULT to GRUB_CMDLINE_LINUX_DEFAULT="quiet vga=0x036b"

Running ubuntu-server 64bit with GRUB2 and no GUI

---

### Post by grahammechanical on 2013-09-07
You are missing the fact the text size in Grub only last as long as Grub is in control of the screen. At some point the Xserver takes over and then when we are at the login screen it is Lighdm display manger that is rendering the text size and following lightdm it is Compiz the compositing/window manager that is managing the desktop environment.

What is the optimum resolution of your monitor? Ubuntu usually reads the optimum screen resolution from the monitor. It looks for the EDID (Extended Display Identification Data) that is stored in a chip in the monitor and sets the screen resolution according to that. This is why we do not need to set a screen resolution when we install.

With a server install you are getting the resolution set in the Xserver. If you go to /etc/X11/ you will find stuff relating to the Xserver. There might be something there that can be edited.

Regards.

---

### Post by rai_shu2 on 2013-09-07
I don't think 875 is supported on your video card. I think what you want is 864. See [http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

---

### Post by hiig on 2013-09-07
> **rai_shu2 said:**
> I don't think 875 is supported on your video card. I think what you want is 864. See [http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

THANK YOU! I've been looking for those numbers for ages and I couldn't seem to find them! Finally, I can use this VM to its potential!

---

