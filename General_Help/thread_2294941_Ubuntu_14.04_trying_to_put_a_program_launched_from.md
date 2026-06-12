---
title: "Ubuntu 14.04: trying to put a program launched from terminal onto taskbar"
date: 2015-09-14
forum: General Help
---

### Post by sdad46 on 2015-09-14
I have a Canon scanner that plays with its own dedicated program when launched from a terminal. I'd like to launch from Unity taskbar, but not sure how to do that.  The command in terminal is "scangearmp".  I have search for a file by that name but am unsuccessful. I dont anticipate using this utility often enough to remember what to type into terminal, hence the desire to have it launch from unity. Someone supply a little guidance?


Thanks

---

### Post by chessnerd on 2015-09-15
In Unity you need to create a ".desktop" file to have a launcher. The details of this are explained here: [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)
 
In your case, I suppose it would be a file called "canon_scanner.desktop" with these contents:

[FONT=Courier New][Desktop Entry]
Version=1.0
Name=Canon Scanner
Comment=Run the scanner
Exec=scangearmp
Icon= *[COLOR="#696969"](you can find an icon image and put the path to it here)[/COLOR]*
Terminal=true
Type=Application
Categories=Utility;Application;[/FONT]

Make the file executable by running the command [FONT=Courier New]chmod +x canon_scanner.desktop[/FONT] and put that file in "~/.local/share/applications/" or "/usr/share/applications/". Then, using the Dash search, search for Canon and the application launcher should show up. Drag the launcher onto the taskbar and you should be good to go.

---

### Post by kerry_s on 2015-09-15
install & use menulibre to create launchers to use in unity.

example of 1 i made for quiting.

---

