---
title: "Fonts size issues"
date: 2017-10-25
forum: General Help
---

### Post by sabotage3d on 2017-10-25
Hi,

I am having some problems with the font size in Kubuntu 17.04. After the installation all the fonts were really small especially in the terminal and I had to increase the DPI to 115 using the force DPI option in the Fonts settings. At work we have CentOS and Mate both using 101 DPI and the fonts are substantially larger. It seems that after setting the DPI Chrome and Firefox don't obey the new DPI or at least not on all pages. I tried using the scale display option but using fractional values makes some things to look fuzzy. This is how it currently looks: [https://i.imgur.com/np6MTP4.png](https://i.imgur.com/np6MTP4.png).

Some additional info:

```
xdpyinfo | grep -B2 resolution
screen #0:
dimensions:    1920x1080 pixels (508x285 millimeters)
resolution:    96x96 dots per inch


```

```
xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
HDMI-3 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 475mm x 267mm
1920x1080     60.00*+
1600x1200     60.00   
1680x1050     59.88   
1280x1024     60.02   
1440x900      59.90   
1280x960      60.00   
1280x720      60.00   
1024x768      60.00   
800x600       60.32   
640x480       59.94   
720x400       70.08  


```

---

### Post by SeijiSensei on 2017-10-26
The appearance of applications using GTK like Firefox is controlled separately from the rest of KDE.  Try navigating to System Settings > Application Style > GNOME Application Style (GTK).  You'll see a font box there.

---

### Post by sabotage3d on 2017-10-26
I just checked these settings and the GTK fonts are set to size 10 by default but outside Chrome and Firefox size 10 looks bigger because of my DPI settings. It seems that the GTK applications are not affected by the global DPI settings is that a bug?

---

### Post by SeijiSensei on 2017-10-27
No, I think that is a "feature" of KDE.  KDE is written using the Qt libraries, not GTK, and its native applications like Konqueror, KMail, Konsole, Dolphin, etc., all rely on Qt.  Supporting GTK is a kludge, just like supporting Qt apps on GNOME-based Ubuntu flavors is also something of a kludge.  If you live only in a KDE world, you wouldn't need to futz with settings for GTK-based apps.  That said, I install Firefox and Thunderbird every time I install Kubuntu, so I got accustomed to adjusting the GTK fonts.  Once you've gotten everything to look the way you want, you shouldn't have to fiddle with them again.  All your settings are stored in your home directory.

---

### Post by Chanath on 2017-10-27
> **sabotage3d said:**
> Hi,

I am having some problems with the font size in Kubuntu 17.04. After the installation all the fonts were really small especially in the terminal 

Application Launcher > System Settings > Appearance > Fonts and change the font sizes to your liking.

---

