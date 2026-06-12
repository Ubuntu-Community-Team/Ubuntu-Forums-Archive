---
title: "HOw to create launcher on desktop?"
date: 2012-12-10
forum: General Help
---

### Post by oxf on 2012-12-10
I'm using Gnome here. How do I create a launcher icon for LibreOffice Writer on the desktop? I tried just dragging it from the Applications menu but all I get is a "broken" icon thingy.

Thanks

---

### Post by pkadeel on 2012-12-11
> **oxf said:**
> I'm using Gnome here. How do I create a launcher icon for LibreOffice Writer on the desktop? I tried just dragging it from the Applications menu but all I get is a "broken" icon thingy.

Thanks
Application launchers are placed in /usr/share/applications.
If you are the drag n drop on desktop is not working for you somehow then you can always go the the above location and copy the required link/.desktop file and paste it where you want it.

---

### Post by rnerwein on 2012-12-11
> **pkadeel said:**
> Application launchers are placed in /usr/share/applications.
If you are the drag n drop on desktop is not working for you somehow then you can always go the the above location and copy the required link/.desktop file and paste it where you want it.
hi
the way i am doing this is:
1. create a file in your ~/Desktop directory e.g. owriter.desktop (.desktop is a must ! )
    example for /bin/bash
        [Desktop Entry]
       Version=1.0
       Name=bash
       Comment=back to the roots
       Exec=/bin/bash
       Icon=/home/richi/desktop/red_glasses.png
      Terminal=true
      Type=Application
      Categories=Utility;Application;

# i copy all the icons i need to my ~/desktop becaus the location of the icons  are always changed in new versions (desktop is my private directory !)
2. open nautilus
3. navigate to your ~/Desktop
4. grep the owriter.desktop and drag it to your desktop or to your sidebar.
cheers
~

---

### Post by Abhinav Kumar on 2012-12-11
> **oxf said:**
> I'm using Gnome here. How do I create a launcher icon for LibreOffice Writer on the desktop? I tried just dragging it from the Applications menu but all I get is a "broken" icon thingy.

Thanks
Hi oxf,
Just right click on the application menu launcher and select Add this launcher to Desktop.:P

Abhinav

---

### Post by rnerwein on 2012-12-11
> **Abhinav Kumar said:**
> Hi oxf,
Just right click on the application menu launcher and select Add this launcher to Desktop.:P

Abhinav
yeah
this works on 10.04 standard but not in 12.04 (standard)

---

### Post by cmcanulty on 2012-12-11
for some reason writer won't make a launcher like it should here is a screenshot of my launcher properties that works in 12.04 classic. The icon is in /usr/share/icons/gnome/48x48/apps/libreoffice-writer.png

---

### Post by rnerwein on 2012-12-14
> **cmcanulty said:**
> for some reason writer won't make a launcher like it should here is a screenshot of my launcher properties that works in 12.04 classic. The icon is in /usr/share/icons/gnome/48x48/apps/libreoffice-writer.png
hi
ok you are wright. i was thinking about the panel on top of the screen (for me a better solution then dos like sidebar)
cheers

---

### Post by cmcanulty on 2012-12-14
for the top panel just drag it from menu and hold until you see the little + sign, then release. Move by alt+rt cl

---

