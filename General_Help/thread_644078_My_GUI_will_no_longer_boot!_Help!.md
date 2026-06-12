---
title: "My GUI will no longer boot! Help!"
date: 2007-12-18
forum: General Help
---

### Post by flehnerz on 2007-12-18
My distro of Ubuntu 7.10 no longer loads into the GUI on my Toshiba Satellite Laptop. I believe the cause was the fact that I usually  run my machine at 1900 x 1200 on my 24 inch LCD. Now, I'm abroad, monitor less, posting from Windows Virus. Anyways, GRUB seems to boot a bit slower than usual. The if I select Ubuntu, the splash screen with the loading bar displays, then it boots into console with this:
```

Starting up...
Loading, Please wait...
USplash: Setting Mode 1280x1024 failed
USplash: Setting Mode 1152x864 failed
USplash: Using Mode 1024x768
Kinit: name_to_dev_t)/dev/disk/by-vvid/6c0edbf2-177f4935-8aab-50e1bf0aee4a)=sda5(8,5)
Kinit: trying to resume from /dev/disk/by-vid/6c0edbf2-177f4935-8aab-50e1bf0aee4a
Kinit: No resume image, doing normal boot...

Ubuntu 7.10 frank-laptop tty1
frank-laptop login:

```

The max resolution supported by the on board screen is 1280x800. If I remember correctly, I hibernated the session instead of just shutting down the system. Any help would be greatly appreciated. And please note that I may have made some kind of mistake above since I obviously couldn't copy+paste what the console was giving me. I am also fairly new to the Ubuntu/Linux world, so please try to explain things to me. Thank you.

---

### Post by Prefader on 2007-12-18
How certain are you that you aren't parked on a virtual terminal?  If you hit ctl-alt-F7, does your DM show up? (press ctl-alt-F1 to get back to the login prompt if it doesn't work)

If not, what happens if you login and type "startx"?

#EDIT#
duh, it says "TTY1" right there - sorry about that.  Still, try ctl-alt-F7 and see what you get.

---

### Post by flehnerz on 2007-12-18
Prefader,
I would have tried that, but right after my first post I rebooted into Ubuntu and entered 
```

sudo dpkg-reconfigure xserver-xorg

```
 I reconfigured xserver following the instructions closely and rebooted to try your solution and it booted in to the GUI. I had to log out again to get GNOME to boot everything correctly but not I'm back in paradise with my dual boot machine. Thank you anyways.

---

### Post by Prefader on 2007-12-18
Glad you got it working again!

---

