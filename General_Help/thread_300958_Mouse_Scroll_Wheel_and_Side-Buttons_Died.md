---
title: "Mouse Scroll Wheel and Side-Buttons Died"
date: 2006-11-16
forum: General Help
---

### Post by new2linux on 2006-11-16
Hi,

   I just upgraded to edgy (using the approved method).  After installation my xorg died (which is normal).  I reconfigured it, but have since noticed that my mouse scroll wheel and buttons are not working.  I had both of these configured as per the directions on the ubuntuguide.org guide to dapper.
   These settings had involved imwheel and modifying my xorg file.  It occurred to me that perhaps as edgy was being installed these settings were reset and imwheel was removed.  However, that is not the case.  I also thought that the edgy directions might be different but they appear to be the same.  Does anyone know how to re-configure both of these things?

Thanks for any help,

EHD

---

### Post by mgmiller on 2006-11-18
I have had the same problem,  I have gotten all my buttons working again in firefox 2.0 by editing /etc/X11/org.conf

first back it up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then edit the file:
```
sudo gedit /etc/X11/xorg.conf

```
This is what my mouse section looks like:

```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" 		"/dev/input/mice"
        Option      "Protocol" 		"ExplorerPS/2"
        Option      "ZAxisMapping" 	"6 7"
        Option      "ButtonMapping" 	"1 2 3 4 5"
EndSection
```

You will see the zaxis and buttonmapping lines have changed their numbers around since Dapper.

Save your changes and log off and restart x for the changes to take effect. (ctrl+alt+backspace)

The buttons should work normally in firefox.  
I used the imwheel method to get the side buttons working in nautilus with Dapper, but I can't get the side buttons to work yet in Edgy.

At least this is a start for you.

---

### Post by new2linux on 2006-11-18
Thanks for the help!

The buttons and scroll wheel are now working!

EHD

---

### Post by Bretls on 2006-11-19
I ended up finding [this article]("http://doc.gwos.org/index.php/Logitech_mice_dapper") and just used the part about xbindkeys and xvkbd and now the back and foward buttons work in nautilus.
Also, I removed imwheel before I did this. I don't know if it makes any difference though.

---

