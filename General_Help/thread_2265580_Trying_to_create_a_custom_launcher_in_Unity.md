---
title: "Trying to create a custom launcher in Unity"
date: 2015-02-16
forum: General Help
---

### Post by Richard_Romick on 2015-02-16
In Ubuntu 14.04, am attempting to create a customer launcher for Higan that will start it with OpenGL3.2.  This is my HiganGL.desktop file

[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Icon[en_US]=gnome-panel-launcher
Name[en_US]=HiganGL
Exec=MESA_GL_VERSION_OVERRIDE=3.2 MESA_GLSL_VERSION_OVERRIDE=150 higan
Comment[en_US]=Launch Higan in OpenGL
Name=HiganGL
Comment=Launch Higan in OpenGL
Icon=gnome-panel-launcher

However, the file will not show up under search in the launcher even though the original Higan launcher appears.  I tried the command in the terminal and it works.  Does anyone know why it doesn't appear?

---

### Post by ajgreeny on 2015-02-16
Where is that HiganGL.desktop file sitting at the moment?

It is also missing the Category field, eg, **Categories=GTK;Utility;System** or similar line that is needed to put such items into the menu of Xubuntu if the desktop file is in the correct place, ie, /usr/share/applications or ~/.local/share/applications.  Have a look at other .desktop files with a text editor to see what the options for this Categories line are.

Unfortunately, for this query, I don't like nor use unity so I'm not certain about where the launchbar gets its default entries from, but those two possible sites are good places to start.

---

### Post by efflandt on 2015-02-16
The easiest way to create launchers that will show up in Dash is to install **Main Menu** from Software Center (alias **alacarte** if installed with sudo apt-get or synaptic). Once you run Main Menu from Dash add a launcher, logout and log back into X, that launcher should show up in Dash. And after launching the launcher from there you can right click it in the Unity bar and lock it there.

However, the Exec= of launchers does not use shell interpretation and sometimes seems to have trouble with spaces or added parameters. So if your Exec= does not work (assuming that higan is in your $PATH), you might need to (single quotes not backticks)```
Exec=sh -c 'MESA_GL_VERSION_OVERRIDE=3.2 MESA_GLSL_VERSION_OVERRIDE=150 higan'
```and/or possibly include a full path to higan (which I am not familiar with) if not in your $PATH.

PS: Not sure if Main Menu is installed by default, but open Dash (top left icon) search for **main**, and see if it shows up.

---

### Post by Richard_Romick on 2015-02-17
The shortcut is in ~/.local/share/applications.  I think efflandt hit the nail on the head, because when I try to modify the original Higan file with my Exec line, it dissapears.  I figured it was because of bad syntax on my part, so I am going to try efflandt's suggestion as soon as I can.  Thanks for the suggestion.

---

### Post by Richard_Romick on 2015-02-20
Putting sh -c and the rest of the command in single quotes fixed it, thank you.

---

### Post by Richard_Romick on 2015-02-20
Now I am trying to change the icon on the launcher.  This is my HiganGL.deskop file now

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=gnome-panel-launcher
Name[en_US]=HiganGL
Exec=sh -c 'MESA_GL_VERSION_OVERRIDE=3.2 MESA_GLSL_VERSION_OVERRIDE=150 higan'
Comment[en_US]=Launch Higan in OpenGL
Name=HiganGL
Comment=Launch Higan in OpenGL
Icon=~/.local/share/icons/higan.svg
Categories=Game;Emulator;
Keywords=emulator;Nintendo;SNES;NES;Gameboy;Famicom;Super

I also have the icon file in the folder listed under icon.  It is the same icon used by the Higan launcher installed with the program, I just copied it to the ~/.local/share/icons folder.

---

