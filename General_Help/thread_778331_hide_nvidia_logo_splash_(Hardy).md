---
title: "hide nvidia logo splash (Hardy)"
date: 2008-05-02
forum: General Help
---

### Post by logos34 on 2008-05-02
If after upgrading to Hardy 8.04 you're getting that annoying nvidia splash screen (again), it might be because nvidia-xconf has put the hide option in the wrong place.  On mine all I had to do was move it from 'Screen' to 'Device' section:
[B]
sudo nano /etc/X11/xorg.conf[/B]

> Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6100"
    **[COLOR="Blue"]Option         "NoLogo" "True"[/COLOR]**
EndSection


Also, if your Ubuntu splash does not match your desktop screen resolution, try adding it to the /etc/usplash.conf file:

ex:

> ---
# Usplash configuration file
xres=1280
yres=1024


---

### Post by rubicon on 2008-05-02
That's interesting because I still have "NoLogo" option in *Screen* section and it works just like it should.

Anyway, I think this thread will be useful for people with GeForce cards!

---

### Post by Zorael on 2008-05-02
I wouldn't call it the Discussion to End Them All (that's reserved for KDE vs Gnome), but do note that nvidia-xconfig (the official xorg.conf configurer for Nvidia cards) *does* place them in the Screen section. My options are there and they apply.
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AllowGLXWithComposite"	"true"
#	Option		"DamageEvents"	"true"
	Option		"RenderAccel"	"true"
	Option		"NoLogo"	"true"
	Option		"RandRRotation"	"on"
#	Option		"DisableGLXRootClipping"	"true"
	DefaultDepth	24
EndSection
```

---

### Post by logos34 on 2008-05-02
Maybe I'm the only one, or it's just limited to geforce cards.  Hasn't happened before, though.

---

### Post by MaxCapacitor on 2008-05-17
On my system, I copy and pasted lines of code from what seems to be a placeholder device to the next videocard device lines to get it to remove the nvidia splash logo.

```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 GT"
    BusID          "PCI:1:0:0"
    Screen          0
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection
```
Here's another tip, if you're using multiple monitors like me, you need to input the **Option "NoLogo" "True"** line to each screen's videocard device.

You could also have one screen display and the other not display the logo if you want like how I have it above. I did it it out of curiosity.

Oh, and btw, the nvidia logo is great for diagnostic purposes when you're setting up multiple monitors. They're great visual cues when you don't have the multiple screens setup properly or to your liking.

---

### Post by logos34 on 2008-05-17
> **MaxCapacitor said:**
> 
Here's another tip, if you're using multiple monitors like me, you need to input the **Option "NoLogo" "True"** line to each screen's videocard device.

You could also have one screen display and the other not display the logo if you want like how I have it above. I did it it out of curiosity.

Oh, and btw, the nvidia logo is great for diagnostic purposes when you're setting up multiple monitors. They're great visual cues when you don't have the multiple screens setup properly or to your liking.

Hmm.  I'm not one of the lucky few to have multiple monitors (although that may be a blessing in disguise considering the price of electricity these days!)

---

