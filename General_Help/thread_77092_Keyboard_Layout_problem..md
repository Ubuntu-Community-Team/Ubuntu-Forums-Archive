---
title: "Keyboard Layout problem."
date: 2005-10-16
forum: General Help
---

### Post by emperon on 2005-10-16
Hello I have made a fresh install of Breezy over Hoary and now, although i have set the default keyboard layout as Turkish, nothing has changed. I also have installed language support for Turkish, still no difference. This was working in hoary, what can i do ?

---

### Post by alper_tr on 2005-10-16
I have the same problem with the turkish keyboard layout. Seems like its a bug, almost everyone with international keyboards having that problem... 

Hoary sanki cok daha iyiydi breezy'den :( Epey bir bug var, biraz bekleyip update ler ciktiktan sonra yüklemek daha mantikli olabilirdi.. ama neyse :)

---

### Post by JanZ on 2005-10-16
Hello,

sudo nano -w /etc/X11/xorg.conf

In the xorg configuration file, find the following section:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

The XkbLayout should be defined as "us" (mine was). Change it to turkish (sorry, I don't know the abbreviation). After doing so, exit with Ctrl+X (type Y at prompt to save changes). Restart the X. On the startup, Gnome should notify you that the X and Gnome have different keyboard layouts defined. Force Gnome to use X's layout and you should be done.;)

EDIT: you may want to backup the original xorg.conf in case something goes wrong. Alternatively, you can use any text editor to modify the file, e.g. sudo gedit -w /etc/X11/xorg.conf

---

### Post by Dooglus on 2005-10-16
I believe this is a known bug, which should be fixed soon:

    [https://bugzilla.ubuntu.com/show_bug.cgi?id=15372](https://bugzilla.ubuntu.com/show_bug.cgi?id=15372)

Alternatively, I hear you can download the fix directly from the above bugzilla entry and fix it for yourself.  Download the two .deb files in comment #35, install with "sudo dpkg -i <filename>" and set the right keyboard type in xorg.conf.

Here's how I saw it described on IRC:
```

22:36 < Knorrie> i_r_e_n_e: (now with text) i had that problem and installing the debs at #38 in this page fixed it:  http://bugzilla.ubuntu.com/show_bug.cgi?id=15372
22:37 < Knorrie> i_r_e_n_e: it's a bug in the keyboard tool
22:38 < Knorrie> i_r_e_n_e: i downloaded those two debs and installed them with dpkg -i (both .debs at once here)
22:40 < Knorrie> i_r_e_n_e: after that, set the right keyboard in /etc/X11/xorg.conf, restart X and in the dialog that asks user X or gnome keyboard settings choose use X

```

---

### Post by emperon on 2005-10-16
[QUOTE=JanZ]Hello,

sudo nano -w /etc/X11/xorg.conf

In the xorg configuration file, find the following section:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

The XkbLayout should be defined as "us" (mine was). Change it to turkish (sorry, I don't know the abbreviation). After doing so, exit with Ctrl+X (type Y at prompt to save changes). Restart the X. On the startup, Gnome should notify you that the X and Gnome have different keyboard layouts defined. Force Gnome to use X's layout and you should be done.;)

EDIT: you may want to backup the original xorg.conf in case something goes wrong. Alternatively, you can use any text editor to modify the file, e.g. sudo gedit -w /etc/X11/xorg.conf[/QUOTE]
Thanks a lot it worked like charm. 
How ever, i should have tell another minor bug with  ID 13260. So for no one interested. And i didn't understand it why.

Also there is an issue with Caps lock and Shift combinations of Turk letters i and I

---

