---
title: "Libreoffice F11 and two types of fullscreen"
date: 2013-05-31
forum: General Help
---

### Post by JosephWheatley on 2013-05-31
[SIZE=4]Is there any information out there on the two variants of fullscreen that Libreoffice now performs?[/SIZE]

On pressing F11 I get a fullscreen that hides the taskbar and titlebar while still showing all the toolbars.
On pressing ctrl-shift-J  I get the outright full screen that hides all toolbars.

Yet on looking at the settings under **Tools>Customize>Keyboard **F11 is still assigned to **Styles and Formatting**

I am using Libreoffice 4.0 from the ppa in Lubuntu 12.04.
Libreoffice are telling me very little [https://help.libreoffice.org/Writer/Shortcut_Keys_for_Writer](https://help.libreoffice.org/Writer/Shortcut_Keys_for_Writer)and[ https://help.libreoffice.org/Common/Full_Screen]("https://help.libreoffice.org/Common/Full_Screen")

---

### Post by bela42 on 2013-06-03
To me, this sounds a little like F11 may be mapped as a shortcut by your window manager. Since your'e using LXDE  I can't tell where to look for key mappings, but perhaps someone else can point you to the config of LXDE...

---

### Post by JosephWheatley on 2013-06-11
Thank you.

You have pointed me in the right direction.

I can seen now it is the LXDE setup in the /.config/openbox/lxde-rc.xml file.
WIth a small edit like this from [http://wiki.linuxonlinehelp.de/index.php/Openbox](http://wiki.linuxonlinehelp.de/index.php/Openbox)

```

<keybind key="A-F11"> <action name="ToggleFullscreen"/> </keybind>
```

This means that On pressing alt-F11 I get a fullscreen that hides the taskbar and titlebar while still showing all the toolbars and the two F11 options do not clash.

---

