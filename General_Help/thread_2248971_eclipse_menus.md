---
title: "eclipse menus"
date: 2014-10-18
forum: General Help
---

### Post by amiralex32 on 2014-10-18
dear all i am using eclipse kepler with ubuntu 13.10 but the menus of the eclipse doen't appear 
so i made this solution and it didn't succeded 

locate eclipse.desktop
/usr/share/app-install/desktop/eclipse-platform:eclipse.desktop
/usr/share/app-install/desktop/eclipse-platform:eclipse.desktop~
/usr/share/app-install/desktop/redeclipse:redeclipse.desktop
/usr/share/applications/eclipse.desktop
/usr/share/applications/eclipse.desktop~

then i made changes in the desktop entry and replace the exec 

sudo -H gedit /usr/share/applications/eclipse.desktop

[Desktop Entry]
Version=4.3.0
Name=Eclipse
Comment=IDE for all seasons
#Exec=/home/eclipse/eclipse
Exec=env UBUNTU_MENUPROXY=0 /home/eclipse/eclipse
Icon=/home/eclipse/icon.xpm
Terminal=false
Type=Application
Categories=Utility;Application

it was mentioned that it will solve the problem but i couldn't solve it can any one help me

---

