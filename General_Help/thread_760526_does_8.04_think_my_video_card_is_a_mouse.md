---
title: "does 8.04 think my video card is a mouse?"
date: 2008-04-20
forum: General Help
---

### Post by nacho32 on 2008-04-20
I type in this  sudo nvidia-xconfig
and this is what it says?


jeff@jeff-desktop:~$ sudo nvidia-xconfig
[sudo] password for jeff: 

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

jeff@jeff-desktop:~$ 


help

---

### Post by Diabolis on 2008-04-20
nop, its telling you that your xorg.conf file is not complete or it has errors.
The errors don't seem to be critical, so they pop out as warnings. If they were critical you would know, this file has the configuration of your xserver.
xserver handles all your graphics, keyboard layout and mouse configuration. Stuff like your mouse type, screen resolution etc.

fix it with this:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by nacho32 on 2008-04-20
I did that and retyped and this is what it says 
jeff@jeff-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

jeff@jeff-desktop:~$

---

### Post by Diabolis on 2008-04-20
Thats weird, you didn't pick a driver? I don't think so. Why don't you post the contents of your xorg.conf file.
```
cat /etc/X11/xorg.conf
```

---

