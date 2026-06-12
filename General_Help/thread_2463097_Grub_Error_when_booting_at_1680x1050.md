---
title: "Grub Error when booting at 1680x1050"
date: 2021-06-03
forum: General Help
---

### Post by benyjr on 2021-06-03
Hi Everyone,

I'm using a clean install of Ubuntu 20.04 and I've been playing with dual boot grub themes.

It works great, except that there are no themes for my screen resolution of 1680x1050.

I modified the background image of this theme: [https://www.gnome-look.org/p/1307852/](https://www.gnome-look.org/p/1307852/) to 1680x1050.

Unfortunately, on the next reboot I get the following error:

[INDENT]error: can't find command 'hwmatch'.
error: invalid argument.

Press any key to continue...[/INDENT]

And then grub falls back to the default grub screen and boots normally.

Is there any way to resolve this issue and get grub to support 1680x1050 resolution?

Thank you.
[INDENT][/INDENT]

---

### Post by benyjr on 2021-06-08
For anyone looking into the same issue, this is a side effect of supporting legacy boot drive configuration in your BIOS.

If all your boot drives support UEFI, disable legacy boot support or [COLOR=#191E1E][FONT=Lato]CSM (Compatibility support module) in your BIOS[/FONT][/COLOR] and for some reason this opens up more supported screen resolutions during the bootup process and makes them available to GRUB.

---

