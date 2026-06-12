---
title: "Making Arduino IDE 2. appear on my Installed Applications"
date: 2023-10-31
forum: General Help
---

### Post by ozark_hillbilly on 2023-10-31
I have installed Arduino IDE 2.x to my Linux Desktop but there is no currrent link to have it
show up on the Installed Applications.

Currently I go the /Home/Arduino IDE 2.0 sub directory and click on:

 arduino-ide_2.2.1_Linux_64bit.AppImage

to run the program. What is the procedure to make it appear as an Installed Application?

thanks...

---

### Post by Holger_Gehrke on 2023-10-31
Do you mean you want it to appear on the application overview / start menu (or whatever your GUI uses ...) ? Then you need a file with the extension '.desktop' that starts your program and it needs to be in either /usr/share/applications or /usr/local/share/applications or ~/.local/share/applications (recommended, since the program is in a subdirectory of your $HOME). That file is a simple text file with a structure as described [here]("https://specifications.freedesktop.org/desktop-entry-spec/latest/"). Should look something like this:
```

[Desktop Entry]
Encoding=UTF-8
Value=1.0
Type=Application
Name=Arduino IDE
GenericName=Integrated Development Environment for Arduino
Comment=Integrated Development Environment for Arduino
Icon=/home/YOUR_USER_NAME_HERE/.local/share/icons/truecolor/256/YOUR_ICON_FILE_NAME_HERE.png.
Exec="/home/YOUR_USER_NAME_HERE/Arduino IDE 2.0/arduino-ide_2.2.1_Linux_64bit.AppImage"
Categories=Development;

```

Replace the parts in ALL_CAPS with whatever is necessary.

Holger

---

### Post by guiverc on 2023-10-31
You've put this in the Lubuntu area of this forum, but haven't said what release of Lubuntu you're using, thus I'm using the link for the current *stable* release, which is Lubuntu 23.10.

You can always create a *desktop icon* or shortcut that will execute it. Refer to the manual page here - [https://manual.lubuntu.me/stable/5/5.2/desktop_icons.html](https://manual.lubuntu.me/stable/5/5.2/desktop_icons.html)  with this detail being what  				 				 					 						 	[**[COLOR=#000000]Holger_Gehrke[/COLOR]**]("https://ubuntuforums.org/member.php?u=1961578") covered too.

After creation, you can drag/drop it on the *Quick Launch *area of your panel (*use of that is covered in the manual too if you're not familiar with it*)

---

