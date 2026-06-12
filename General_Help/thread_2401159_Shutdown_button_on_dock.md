---
title: "Shutdown button on dock"
date: 2018-09-14
forum: General Help
---

### Post by haahrsit on 2018-09-14
Offcourse as usually it seems pretty easy to add a shutdown button to the dock. 

But as usually Ubuntu wont make anything easy. 


I JUST DONT GET IT. The app is there if i search for it, but i cant dock it. . .. ??????? SIGH. 

Mike

---

### Post by ajgreeny on 2018-09-14
Create a shutdown.desktop file (a simple text file) with the following content
```
[Desktop Entry]
Version=1.0
Type=Application
Name=shutdown
Comment=shutdown system
Exec=shutdown -h now
Icon=any icon image you want
Path=
Terminal=false
StartupNotify=false

```
move it to ~/.local/share/applications then in the Activities screen search for shutdown, right click it when it appears and click "Add to Favourites.

That will give you an immediate shutdown with no dialogue asking what you want to do; if you want the option to logout, restart or power-off, search for power-off in the Activities and again right click ->"Add to Favourites"

I just tried it and it worked for my Ubuntu 18.04 with default DE.

---

