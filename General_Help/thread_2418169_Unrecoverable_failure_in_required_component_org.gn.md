---
title: "Unrecoverable failure in required component org.gnome.Shell.desktop"
date: 2019-05-02
forum: General Help
---

### Post by stepheny on 2019-05-02
I am running a brand new install of Ubuntu 18.10 under Wayland (but the same error occurs under Xorg) on a brand new laptop. I use about 15 Gnome extensions. In my logs I get the "important" warning > Unrecoverable failure in required component org.gnome.Shell.desktopI have nailed the error down to this line in syslog:

> failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/xrandr_AU_Optronics_gdm_123

What is this error referring to? I have no symptoms or problems with the setup other than this error message.

---

### Post by dino99 on 2019-05-03
That error (harmless) point to 'color manager'

Looks like related to the video devive (screen) and its pixel depth definition.

here is the main documentation page: [https://help.ubuntu.com/stable/ubuntu-help/color.html](https://help.ubuntu.com/stable/ubuntu-help/color.html)

Please run

colormgr get-devices-by-kind display
from a terminal and post the output. Thanks.

---

### Post by stepheny on 2019-05-03
Thanks for the response. I followed the instructions you linked to to calibrate the screen but the "calibrate" button is grayed out.

Here is the output of "colormgr get-devices-by-kind display"

```
steve@steve-N8xxEZ:~$ colormgr get-devices-by-kind display
Objektpfad:    /org/freedesktop/ColorManager/devices/xrandr_AU_Optronics_steve_1000
Besitzer:      steve
Angelegt:       3.Mai.2019, 06:13:01
Geändert:      3.Mai.2019, 06:13:08
Typ:           display
Enabled:       Yes
Embedded:      Yes
Modell:        N8xxEZ
Hersteller:    TUX
Seriennummer:  unknown
Seat:          seat0
Geltungsbereich:temp
Farbraum:      rgb
Gerätekennung:xrandr-AU Optronics
Profil 1:      icc-9f828e43448e098186ac78c8df95273e
               /home/steve/.local/share/icc/edid-c128d8b4f6deb3c62c402f3a7a7b6cec.icc
Metadaten:     XRANDR_name=eDP-1
Metadaten:     OutputPriority=primary
Metadaten:     OwnerCmdline=/usr/lib/gnome-settings-daemon/gsd-color 
Metadaten:     OutputEdidMd5=c128d8b4f6deb3c62c402f3a7a7b6cec
```

---

