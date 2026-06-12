---
title: "Want to keep ROTATE SCREEN LEFT default"
date: 2008-07-05
forum: General Help
---

### Post by gobuntu on 2008-07-05
Dear friends,

Ubuntu Gutsy Gibon (updates uptodate), Lenovo laptop.

At Systems/Preferences/ScreenResolution CAN DO OK Rotate Screen Left, works good.

I click Options [x] "Make default for this computer only" and click "Apply", get no error message. 

Keeps working OK in portrait mode.

BUT, time and time again, every time upon turn computer on again, the Rotation is NORMAL, and have to again repeat System/Preferences/ScrrenResolution, check box, Apply, "set default", etc., and REFUSES TO KEEP the "Rotate LEFT" default.

I use this laptop always on the portrait mode, and it's  difficult to set up every time.

Have searched and researched the web, and still no fix.

Can someone please assist? What can I put in the configuration files to FIX it?

I have visual effects as NONE at "Appearance/preferences" for that's the only way rotation does work, but again, need it to becomes the default mode.

Thanks!

---

### Post by ryanhaigh on 2008-07-07
If you want to make the change permanent you need to add the rotate option to the device section of your /etc/xorg.conf file. Open the terminal: Applications>accessories>terminal

Backup your existing config
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

Open the file for editing
```

sudo gedit /etc/X11/xorg.conf

```

Find the section that looks similar this > 
   Section "Device"

       Identifier  "Card0"
       Driver      "intel"
       VendorName  "Intel Corp."
       BoardName   "82852/855GM Integrated Graphics Device"
       BusID       "PCI:0:2:0"


And add the rotate option
> 
   Section "Device"

       Identifier  "Card0"
       Driver      "intel"
       VendorName  "Intel Corp."
       BoardName   "82852/855GM Integrated Graphics Device"
       BusID       "PCI:0:2:0"
**       Option      "Rotate" "CW"**


Im assuming here that you are using an intel graphics card if not you should post back details of the graphics card in the machine and maybe your existing xorg.conf file.

---

### Post by gobuntu on 2008-07-08
> **ryanhaigh said:**
> If you want to make the change permanent you need to add the rotate option to the device section of your /etc/xorg.conf file. Open the terminal: Applications>accessories>terminal

Backup your existing config
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

Open the file for editing
```

sudo gedit /etc/X11/xorg.conf

```

Find the section that looks similar this 

And add the rotate option


Im assuming here that you are using an intel graphics card if not you should post back details of the graphics card in the machine and maybe your existing xorg.conf file.

Thank you.

Did change 
sudo gedit /etc/X11/xorg.conf

AFTER having made backup copy as follows:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

then shutoff,
start computer,

grub OK,
starts graphical boot
but does not get to 
request username and pw.

Instead boots to terminal
with messages:
usplash: Setting mode 1280x854 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768

This screen then by itself turns off in a blink,
and then comes back to the same messages,
and I can log in in the terminal mode.

I do sudo reboot and exactly same thing happens.

How to fix from terminal mode now?

---

### Post by ryanhaigh on 2008-07-08
This is why we made a backup, log in via terminal and create a copy of your xorg.conf and Xorg.0.log so you can post them here.
```
cp /etc/X11/xorg.conf ~/xorg.txt
cp /var/log/Xorg.0.log ~/Xlog.txt
```

The restore your older version of xorg.conf and probably provide a copy of that so we can see what you changed.
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
cp /etc/X11/xorg.conf ~/oldxorg.txt

```

You can then restart and be back to how it was before.

Attach the files xorg.txt, Xlog.txt and oldxorg.txt to your next post, they will be in your home directory.

---

