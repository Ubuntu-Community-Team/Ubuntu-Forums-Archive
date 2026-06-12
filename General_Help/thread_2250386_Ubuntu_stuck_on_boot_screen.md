---
title: "Ubuntu stuck on boot screen"
date: 2014-10-28
forum: General Help
---

### Post by redrumrogue on 2014-10-28
Hi everyone,

I've been using Ubuntu Gnome for a while but with a custom kernel (3.16.6 now) and also with the nVidia drivers installed from the .run file from the nvidia website.  Everything work really well but now I'd like to revert back to the standard ubuntu kernel and also use nouveau | ubuntu repository nvidia drivers.

When I installed the nVidia .run file I had to add a blacklist file in /etc/modprobe.d to blacklist the nouveau driver so that it wouldn't interfere with the nvidia driver.  During installation of the nvidia driver an Xorg.conf file was generated in /etc/X11.  My understanding was that in order to fall back to the nouveau driver I would just need to remove the blacklist file and remove the Xorg.conf files.  However when I reboot after doing this my machine hangs at the boot screen.  It probably isn't "hanging", but I suppose I'm just not getting an X session or something like that ...

Anybody got any ideas??

---

### Post by redrumrogue on 2014-10-31
Bump ... anyone?

---

