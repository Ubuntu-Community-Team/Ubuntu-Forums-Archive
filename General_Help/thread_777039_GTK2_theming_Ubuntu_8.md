---
title: "GTK2 theming Ubuntu 8"
date: 2008-05-01
forum: General Help
---

### Post by Etamami on 2008-05-01
Hello! :)

Love Ubuntu, but I wanna change the theming. I searched on DA some very nice themes for GTK2+. How do I know if I have installed GTK2+ engine here on the stock Ubuntu? ...do I have to install it fist?

How can I use the themes that I grabbed? ...how can I install them?

Well, it's also nice is someone could provide some "tutorial" link, or some website where is briefly described like for dummies, because i'm tottaly new in Ubuntu....but I love it right away now! :)

*Thanks for helping!

---

### Post by Etamami on 2008-05-01
For example:

> Kemikal for GTK.

Requires the pixmap and mist engine.

Metacity theme and start-here.png icon included.

Icons are XubuntuStudio from xfce-look.org
Font is AvantGarde LT Medium.

To use the start-here.png icon you'll need to check your icon theme. It should be located in /home/username/.icons/ (Press ctrl+h in your file manager to view hidden folders.) If you don't have the .icons folder you can create one and put your icon sets there. (This may however be different if you use any other dist than Debian/Ubuntu. If so, then open gconf editor and select to use a custom icon for the applications menu.)

Go to /.icons/your icon theme/scalable/places/ and see if you have a start-here.svg icon. If you have one, make a backup of it and remove the original. Now go to (or create) the 48x48/places/ folder and make a backup of the start-here.png icon (if any). Then put the start-here icon from Kemikal in that folder. Open a terminal and write killall gnome-panel to refresh the panels.


I downloaded:
gtk-mist-engine_0.10.orig.tar.gz
QtPixmap-0.28_1.tgz

How can I install them? ...what to do with them? :confused:

---

### Post by Etamami on 2008-05-01
Or this one says:

> My little contribution to the Shift Linux project. - [link]

This is a pixmap + mist theme. (Engines included by default in Ubuntu.)

(CTRL+H to view hidden folders in your filemanager.)

1. Put the emerald theme in /home/username/.emerald/themes/
Open the emerald theme manager and select Shiftie from the list.

2. Put the Shiftie folder in /home/username/.themes/
Open the settings for Appearance and select Customize. Select Shiftie in the widgets list.

3. To use the star-here.png (shift logo) icon you'll need to put it in your current icon theme's folder and backup+remove any icons that are named start-here.svg/png. Your icon theme should be located in /home/username/.icons/.

If you're using an OS default icon theme you'll need to open the gconf-editor and select to use a custom application icon in the applications-menu.

After all this - Terminal > killall gnome-panel to refresh the panels.

---

### Post by Etamami on 2008-05-04
...anybody did somethings like this? :confused:

---

### Post by pofigster on 2008-07-08
Open **System->Preferences->Appearance** then just drag the theme folders into that window and it should install them for you.  They'll be available for selection from the same menu.

---

### Post by Etamami on 2008-07-08
> **pofigster said:**
> Open **System->Preferences->Appearance** then just drag the theme folders into that window and it should install them for you.  They'll be available for selection from the same menu.

WOW! Thanks! I will try to find it! :KS

---

### Post by urukrama on 2008-07-08
If a theme needs a particular gtk engine, look for it in Synaptic (System > Administration > Synaptic Package Manager), right click on the package name, select install, and press apply. Most applications you'll need are probably in the repositories and can be installed through Synaptic. You don't have to hunt them down on the internet like you have to do in Windows. See [this page]("https://help.ubuntu.com/community/SynapticHowto") for more help on this.

There are a few themes in the repositories as well, that you can install through Synaptic (search for [gnome-themes-extras]("http://packages.ubuntu.com/hardy/gnome-themes-extras"))

If you are unable to install a theme you find on the internet (on gnome-look.org for example) by dragging it into the Appearance window as pofigster mentioned, you can extract the archive, and copy the theme folder to /home/USERNAME/.themes/ as mentioned in that text you posted earlier (directories that start with a dot (.) are hidden; press Ctrl+H in the file manager to see them.) Once the theme folder is copied to that directory, you can select it in the Appearance window. (Icon themes go to /home/USERNAME/.icons/)

Once a theme is installed, you can use it through the Appearance window, as mentioned by pofigster.

EDIT: See also [here]("http://art.gnome.org/faq.php#q2")

---

