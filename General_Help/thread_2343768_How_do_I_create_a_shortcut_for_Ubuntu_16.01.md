---
title: "How do I create a shortcut for Ubuntu 16.01"
date: 2016-11-18
forum: General Help
---

### Post by numeric2 on 2016-11-18
Hello,

I created an sqlite3 application with Lazarus 1.6.2 and FPC 3.0.0. The application works great. It even uses clipboard and URL features. However the last step is elusive. I need to create a desktop shortcut. This is trivial with windows but, seemingly impossible to do in Ubuntu 16.01. I have spent a great effort and time with this requirement; so far nothing works or is explained in detail. One suggestion uses a "right" mouse click on the application and select "Make Link" option. Unfortunately, "Make Link" is not an available option. Without a desktop shortcut my application is worthless. I am ready to give up on Ubuntu and re-install Windows:eek: :(. I really hate Windows 10. Hopefully there is a solution. While I know a little in terminal mode, after-all, I worked for years in DOS mode, I know nothing about Nautilus. Preferably I prefer the GUI mode, or terminal mode clearly explained. 
Help is greatly appreciated. Thank you
Rob

---

### Post by howefield on 2016-11-19
Have you browsed this page ?

[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

---

### Post by numeric2 on 2016-11-19
> **howefield said:**
> Have you browsed this page ?

[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

NO, but I have tried using the same form of template. It partially worked once I got the path correct. Seems that he path is case sensitive; it can really make things difficult. The shortcut, however, did not find a required SQL file. I tried adding the PATH to the existing path; but still could not find the SQL file.
 
[B]I did find a simple solution. 
[/B]Simply hold the ctrl and shift key and drag the program to the desktop. Also do the same for the SQL file. It worked!!. The ctrl and shift key method was found in one of the Ubuntu forms. The desktop icon is a link and not the actual binary file. Not the same as a copy and past procedure.

---

### Post by CantankRus on 2016-11-20
You can use the desktop entry key "[COLOR="#FF0000"]Path[/COLOR]" to set the working directory to run the program in.
eg the desktop file for teatime-unity...
```
[Desktop Entry]
Type=Application
Name=Tea Time
GenericName=Timer
Keywords=egg;
Exec=/usr/share/teatime/teatime.py
[COLOR="#FF0000"]Path[/COLOR]=/usr/share/teatime/
Icon=/usr/share/icons/Humanity/actions/48/sleep.svg
Terminal=false
Categories=Utility;GTK;
```

To make sure you get the correct path to use in the "Exec=" field, navigate to your application in the file browser and right click on it and select **copy**  
Then just paste into your desktop file. If the path has spaces, enclose in quotes.
eg
```
Exec="/path/to/my application"
```
For a desktop file to appear in the unity dash, place in **~/.local/share/applications**

---

### Post by numeric2 on 2016-11-21
> **CantankRus said:**
> You can use the desktop entry key "[COLOR=#FF0000]Path[/COLOR]" to set the working directory to run the program in.


Thank you CantankRus for your help; the added "[COLOR=#ff0000]Path[/COLOR]" worked!! 
**Benefits**; its easier to change the icon and no extra files needed on the desktop. 
BTW, is there documentation for this text file template? I looked, but haven't found any yet. 
Rob

---

### Post by CantankRus on 2016-11-21
Yep..... [https://specifications.freedesktop.org/desktop-entry-spec/latest/ar01s05.html](https://specifications.freedesktop.org/desktop-entry-spec/latest/ar01s05.html)

---

