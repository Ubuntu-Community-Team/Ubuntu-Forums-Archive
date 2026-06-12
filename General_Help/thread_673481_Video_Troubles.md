---
title: "Video Troubles"
date: 2008-01-20
forum: General Help
---

### Post by gangster fun on 2008-01-20
New to Ubuntu but slightly familiar with Linux in general (I sell something called image guided surgery and the platform runs red hat linux) and just installed Ubuntu on my home PC.

Everything was working fine and I got a message that a restricted driver for my video card (nVidia somethingerother) was available so I installed it.

Next reboot when the system got to the log on screen I got a "can't display video mode" on my monitor (Dell).

I've found some other posts about this issue but no one seemed to know how to help.

When I boot from the live CD everything works fine. Recovery mode works but I don't know enough about linux/ubuntu to know how to remove/replace the driver (I'm assuming the new driver is causing the card to produce a mode incompatible with the monitor)

Any advice?  Is it possible to boot into the xwindow (it is xwindow isn't it?) environment in like a VGA mode to re-configure the video settings?  Is there a config file somewhere with the settings?

TIA,

---

### Post by jleaker01z on 2008-01-20
You can restore the original driver by doing the following

Boot up, then press ctrl+alt+f1 to get a command line

Login

enter "cd /etc/X11"
enter "dir" and look for a backup xorg.conf file (usually xorg.conf.backup)
enter "sudo rm xorg.conf"  this deletes your current xorg.conf file
enter "sudo cp xorg.conf.backup xorg.conf"  this copies your backup file to become the controlling xorg.conf

Reboot and you will be back where you started

---

### Post by jleaker01z on 2008-01-20
Oh and btw...I installed the nvidia driver off of nvidias website, but alot of people here seem to like a program called 'envy' which will download your nvidia driver, install it, and make the necessary changes to your xorg.conf file.  That may be the best way for you to try and install your nvidia drivers.

---

### Post by gangster fun on 2008-01-21
I went into the folder but there was no .backup file.  would it be possible to copy the xorg.config file from the live CD?   Or, if simply delete or rename it will X make a new one when I try and run it?

-Thanks,

---

