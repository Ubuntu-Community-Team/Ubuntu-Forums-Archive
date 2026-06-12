---
title: "Need to change display settings"
date: 2006-10-21
forum: General Help
---

### Post by perrymans on 2006-10-21
I recently moved the harddrive I was using for Edubuntu 6.06 to a new machine. Went from Celeron 667 with 64MB to 1.2 Ghz athlon with 512 MB.

Also different is I have change from the onboard Intel graphics of the old system, to a Riva TNT2 16MB card in the new system.

Now when the computer boots, I get:

"Failed to start X server (your graphical interface). It is liely that it is not set up correctly."

Basically, the X config file is setup for the intel graphics, and ubuntu did not kick off any auto-discover to chage the display drivers.

So how can I either force this detection, or change to the proper configuration?

Thanks. Sean.

---

### Post by podunk on 2006-10-21
You might try installing the Nivida drivers per this:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

I don't have Edubuntu, but the command to back up your xorg.conf file in Ubuntu is
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back_up
```

---

### Post by perrymans on 2006-10-21
Thanks for the help, it looks like I needed the nv driver, not the nvidia.

I actually reran the configuration process when the driver update did not work.

sudo dpkg-reconfigure xserver-xorg

Thanks again! Sean.

---

