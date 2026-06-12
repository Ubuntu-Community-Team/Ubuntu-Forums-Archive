---
title: "Canon Digital Rebel XTi (400D) Hardy trouble"
date: 2008-05-02
forum: General Help
---

### Post by mjpatey on 2008-05-02
Hi, group-

I installed the upgrade from Gutsy to Hardy, and have just now attempted to download photos from my Canon Digital Rebel XTi (also known as the 400D).  Under previous versions of Ubuntu, I'd plug it in, turn it on, and up pops a photo import dialog.

In Hardy, I get no response.

Anybody know how to make this work as it used to?  Thanks for any insight you may have!

-Mark

---

### Post by tacutu on 2008-05-02
same here, but i can still import w/ f-spot (though I hate that application). You can try System - > preferences -> Removable drives and under "digital camera" type f-spot-import. That is, if you can stand using f-spot :((

---

### Post by mjpatey on 2008-05-02
Thanks, I actually tried using Picasa (which I like using, but not for import, as it doesn't handle RAW import)... and it worked for jpegs.

But there was some little app native to Ubuntu Gutsy that would dutifully pop up every time I plugged in, and it's not seeing my camera anymore.  It wasn't F-Spot, but maybe "Gnome Picture Viewer" or "Eye of Gnome"?  I just don't remember.  Any ideas?

---

### Post by tacutu on 2008-05-02
gthumb?

---

### Post by mjpatey on 2008-05-02
Yay!  That's the one.  Thank you!!!  I just imported pictures with gthumb by manually selecting "Import..." in its File menu.

Now I just have to figure out how to make gthumb pop up everytime I connect my camera.  It's as if the default action for plugging in my camera has been set to "do nothing".  I'm off to find out how to change that now.

-Mark

---

### Post by tacutu on 2008-05-03
happy i could help.
Is this what you were loogikng for:
gnome-volume-manager-gthumb ?

---

### Post by mjpatey on 2008-05-03
When I run that, the effect is that gthumb starts... but I get the following error in the Terminal window:

> mjpatey@mycomputer:~$ gnome-volume-manager-gthumb
libhal.c 1310 : invalid udi:  doesn't startwith '/org/freedesktop/Hal/devices/'. 


I don't know what that means, but could it be indicative of why plugging in my camera no longer brings up gthumb automatically?

-Mark

---

### Post by tacutu on 2008-05-03
sorry mate, i have no idea!

---

### Post by DoctorLard on 2008-06-18
For some unknown reason, they decided to pull gthumb importing of photos. I too have a 400D and I too used to happily use the simple gthumb importer. I have managed to figure out how to get gthumb to load - but it's a pain.

1. Create the app launcher for the camera import:

```
sudo gedit /usr/share/applications/gthumb-camera.desktop
```

copy this text in, save and quit:

```
[Desktop Entry]
Name=gThumb Import Photos
GenericName=Import Photos
Comment=Retreive images from your digital camera
Categories=GNOME;GTK;Graphics;Viewer;RasterGraphics;2DGraphics;Photography;
Encoding=UTF-8
Exec=gthumb --import-photos %u
Icon=gthumb
MimeType=x-content/image-dcf;
StartupNotify=true
Terminal=false
Type=Application
NoDisplay=true
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gthumb
X-GNOME-Bugzilla-Component=general
X-GNOME-DocPath=gthumb/gthumb.xml
X-Ubuntu-Gettext-Domain=gthumb

```

3. Refresh the desktop database:

```
sudo update-desktop-database
```

4. In nautilus, go Edit -> Preferences -> Media Tab (far right), and under Photos choose gthumb (you may need to log out and in again...?)

I've got this far but gthumb will still crap out when I try importing photos until I add the following to /etc/udev/rules.d/45-libgphoto2.rules:

```
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3110", MODE="0660", GROUP="plugdev"
```

On one pooter though I noticed that /etc/udev/rules.d/45-libgphoto2.rules was missing altogether

HTH

---

