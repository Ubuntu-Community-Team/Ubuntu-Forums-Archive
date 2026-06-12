---
title: "Is there a way to add options when launching a program from the launcher?"
date: 2017-07-08
forum: General Help
---

### Post by nixietube on 2017-07-08
When Spotify opens from my launcher in Ubuntu 17.04 on my Dell XPS machine, the fonts are too small.  I found a way to launch it from the terminal and have the fonts at the right size: 

spotify --force-device-scale-factor=2

Is there a way to change the launcher icon behavior so that when I click the Spotify icon, it runs with the options specified above?  If I right-click on it, all I get is the option to undock it or open it.

---

### Post by deadflowr on 2017-07-08
Find the spotify desktop file.
(Probably in /usr/share/applications, or in ~/.local/share/applications, but the second one only if you're lucky)
open it in gedit, or open gedit and either drag it into gedit or use a terminal command 
```
gedit /path/to/where-the-spotify.desktop-is
```
if you want spotify to always open with that command simply add your additional --force-XXX to the Exec= line.

If you would like to add it as an extra option which you can choose through right clicking on the launcher, then add the Actions option to the file
Add
```
Actions=whatever name you want
```
and then make the corresponding Entry section for it
```
[Desktop Action some name you want]
Exec=spotify --force-device-scale-factor=2
```
Note the name in the Actions section must match the name in the [Desktop Action ***] section
So if you want to call it spotify resize, then the name must be the same in both places.
Basically the file should look something like this
```
[Desktop Entry]
Name=Spotify
Exec=spotify
Type=Application
Icon=spotify
Actions=spotify-scaled

[Desktop Action spotify-scaled]
Name=Spotify scaled
Exec=spotify --force-device-scale-factor=2
```
Then save it, but with just not save, use save as (Shift+ctrl+S to save as; unless that changed?)
you need to save it in the ~/.local/share/applications folder; 
(.local is hidden by default but you can show hidden by right clicking in the main window area of the save dialog box.)

Once saved in the local folder, remove the icon from the launcher, click on the top icon to open the dash menu and search for the launcher again.
then re-add it to the launcher.
The new launcher should have the options in it now.

Probably easier to just add the extra scale stuff to the main line, but gave you some more anyway.

Hope it helps and makes sense.

---

### Post by nixietube on 2017-07-08
Thanks, it was located in /usr/share/applications and I was able to edit it with nano.  It worked!

---

