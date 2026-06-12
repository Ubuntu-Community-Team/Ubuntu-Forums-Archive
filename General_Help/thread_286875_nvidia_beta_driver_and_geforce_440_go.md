---
title: "nvidia beta driver and geforce 440 go"
date: 2006-10-28
forum: General Help
---

### Post by kashms on 2006-10-28
Hi,

Does anyone have the Nvidia beta drivers working with a Geforce4 440 Go 64Mb card. All I get is a black screen but no freeze. I can login typing blindly and hear the login sound.

If anyone has this configuration working, could you post specific options used in /etc/X11/xorg.conf and /etc/modprobe.d/options.

Thanks

---

### Post by galileon on 2006-10-28
try to reconfigure your x server

ctrl+alt+f1 sends you to a console,
login with regular uname+passwd

sudo dpkg-reconfigure xserver-xorg

follow instructions, then

sudo /etc/init.d/gdm restart

---

### Post by FedeXX on 2006-11-04
> **galileon said:**
> try to reconfigure your x server

ctrl+alt+f1 sends you to a console,
login with regular uname+passwd

sudo dpkg-reconfigure xserver-xorg

follow instructions, then

sudo /etc/init.d/gdm restart

I've the same card, and no problem with the beta drivers... 

try setting default depth to "24" in the sceen section of your xorg.conf, maybe is too low.

---

### Post by kaos on 2006-11-05
I have the same problem with the nvidia beta driver, the tft monitor of my laptop seems to power off. However when I connect an external monitor the desktop is there and working fine, just not on the tft of my laptop.
For the time being I have downgraded the nvidia driver to the one supplied with edgy.

---

### Post by galileon on 2006-11-05
have u tried to reconfigure ur xserver as i explained above?

---

### Post by Nicks Spleen on 2006-11-05
I have a geforce 440 go in my laptop. I have the beta drivers and beryl running on it. I'll post my xorg.conf as soon as I can. I don't remember anything special needing to be done to get them to work with the new beta drivers. What kind of laptop do you have??

---

### Post by kaos on 2006-11-05
I have got Beryl running with Edgy's nvidia drivers following the instructions on [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL"). It's working fine but I want to use AIGLX ([http://ubuntuforums.org/showthread.php?t=263840]("http://ubuntuforums.org/showthread.php?t=263840")) instead.
I didn't try dpkg-reconfigure xserver-xorg but used nvidia-xconfig. I'll try it again later this week once this nvidia beta repo "deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm" is working again.

BTW I have a Dell Latitude C840 with a 64MB geforce 440 go.

---

### Post by adam.skinner on 2006-11-06
You can't use AIGLX with the nVidia driver.  You can use the nVidia beta driver, or the nVidia driver and Xgl.  AIGLX depends on DRI, and nVidia doesn't do DRI.

---

### Post by Eagleevil on 2006-11-07
Anyone have any luck with getting the beta drivers to work on Geforce4 440 go yet? I've tried a few times and all I ever get is a black screen when I restart and I can't seem to find anyway to fix it. It seems as though it just shuts the monitor off completely, but either way all I get is the black screen.

---

### Post by shanepardue on 2006-11-11
Same problem here. I've tried everything to get it working and I've had success on other machines, just not this one.

---

### Post by galileon on 2006-11-11
> **galileon said:**
> have u tried to reconfigure ur xserver as i explained above?

?

---

### Post by shanepardue on 2006-11-11
> **galileon said:**
> ?
i have..yes

---

### Post by Eagleevil on 2006-11-11
Same here, it didn't help at all

---

### Post by kdekid on 2006-11-20
Same here, with a Geforce 2 Go on an Acer desktop. The shipped 8876 driver works with some options tuning in modprobe, however, 9625 does not work. The newer 9740 has not been tested yet.

---

### Post by nocooler on 2006-11-21
I have this issue as well - nvidia drivers = blank screen in edgy, the worked in dapper.

Dell Latitude C840 - Geforce 4 440 go - 1600x1200 LCD panel.

I'm just running the standard NV driver for now - as I dorked up x pretty bad and reloaded.

When I get some time I'll be messing with it more. Does anyone have beryl/compiz running on a GF4 440go @ 1600x1200?

Thanks

---

### Post by Klin'Targ on 2006-11-29
I am having the same issues with my Geforce 420 Go on the 9629 version of the nvidia drivers.

I fixed the black screen issue by adding the following line to the Device section of xorg.conf:
```
Option   "UseDisplayDevice"  "DFP-0"
```

Basically, the new driver is detecting a CRT in addition to the laptop's internal flat panel screen, and this command tells Xorg to use the flat panel.

I am still having some other issues related to EDID / resolution, but at least this got the monitor working with the new driver.

---

### Post by nocooler on 2006-12-05
Got it working!

Thanks for the code Klin'Targ

here's part of my xorg.conf just for giggles

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 80.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 440 Go]"
    Driver         "nvidia"
    Option   "UseDisplayDevice"  "DFP-0"Option   "UseDisplayDevice"  "DFP-0"
    Option   "UseEDID" "False"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 440 Go]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option "ExactModeTimingsDVI" 
    Option "UseEdidDpi" "FALSE" 
    Option "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200_60"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200_60"
    EndSubSection
EndSection

```

Thanks!

---

