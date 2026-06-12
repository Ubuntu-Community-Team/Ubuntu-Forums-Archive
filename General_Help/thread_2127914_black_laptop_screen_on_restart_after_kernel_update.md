---
title: "black laptop screen on restart after kernel update"
date: 2013-03-21
forum: General Help
---

### Post by Ianua on 2013-03-21
I am running 12.04 LTS as a dual boot with Windows 7 on a Toshiba Satellite laptop

As part of the regular package update that I ran last night the kernel was updated to 3.2.0-39-generic and I was asked to reboot. On doing this I was presented with a black screen, i.e. no Toshiba splash, no GRUB menu, although it sounded as though boot up was happening as I heard the Ubuntu sound.


At first I thought the laptop screen was just totally black, but on close inspection there is a very very low brightness - but too low to be functional. I plugged in an external monitor and the display on the external monitor works perfectly.

This is what I have tried so far to get the laptop screen working:

Changing the screen brightness settings. This doesn't do anything to change the virtually black laptop screen.

Following advice from [http://askubuntu.com/questions/168197/brightness-controls-stopped-working-after-update-on-a-samsung-qx412-s01au](http://askubuntu.com/questions/168197/brightness-controls-stopped-working-after-update-on-a-samsung-qx412-s01au) I changed the GRUB config file from:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"

and then to:
GRUB_CMDLINE_LINUX_DEFAULT="quite splash acpi_osi="

After each of these changes I did sudo update-grub and rebooted. No change.

I installed xbacklight and set backlight brightness to 100 but with no affect on laptop screen.

Booting up from GRUB into Windows 7 and previous kernels has no effect. It has crossed my mind that this could be a hardware problem but seems unlikely given that it occured initially after a package/kernel upgrade and reboot.

Any ideas?

---

### Post by INTENSETUX on 2013-03-21
Hi 

You might like to try [http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/) , this solved issues with a black screen whenever i have upgraded Ubuntu.

Burn image to disk , reboot into boot-repair , choose 32bits session or 64 whichever the case may be , choose recommended repair and then click on advanced options and tick ''uncomment GRUB_GFXMODE(solves out of range error)

Hope this helps

---

### Post by Ianua on 2013-03-22
Thanks Intensetux. I tried using the boot-repair as you suggest but there is no change to the problem of the brightness of the laptop screen. Any other suggestions? I am at my wits end.

---

