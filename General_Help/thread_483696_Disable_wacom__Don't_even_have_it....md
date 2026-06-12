---
title: "Disable wacom?  Don't even have it..."
date: 2007-06-25
forum: General Help
---

### Post by rillip on 2007-06-25
I happened to be poking through my log files today, just on a whim, and saw this in kdm.log

```
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun 24 23:25:14 2007
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.

```

I had to look up what wacom was to find out it has to do with touchpads on laptops... I'm running on a PC,  I'm just wondering if anyone's seen this before, and if it's worth it to try and go disable this?  It seems like it'd be quite a waste of time to try and initialize a device that doesn't exist, but if it's not going to make a noticable change, I'm not really going to mess with it.

Thanks for any replies

EDIT:

Actually, I may have resolved this on accident.  I went to remove some programs and found that IBM ThinkPad configuration program installed, along with laptop power management, some other random laptop-specific things... must have come as part of some package and I didn't pay attenention when installing.  Will have to check the log next time I reboot and see.

---

### Post by jocko on 2007-06-25
The wacom drivers are included by default in /etc/X11/xorg.conf, probably because if they weren't there, some laptop users would be left without touchpad.
As far as I have noticed they don't cause any problems other than occasional error messages when starting programs from a terminal.
If you really want to get rid of them, in /etc/X11/xorg.conf there are three different "InputDevice" sections and three lines in the "ServerLayout" section  referring to three different wacom devices.
If you comment out or delete those parts from xorg.conf they will not be loaded.

---

### Post by hardyn on 2007-06-25
i have removed them from my machine... no trouble.

comment out the devices, then don't forget to comment them out in "server layout" as well, or X will not start.

---

### Post by rillip on 2007-06-25
Ah, thanks guys, found it and commented them out after I made a backup.

---

