---
title: "can not create application launcher"
date: 2008-04-01
forum: General Help
---

### Post by chunchengch on 2008-04-01
I try to build a deb package, and I make a x.desktop file as follows, but the deb file will not create the launcher in Application > Internet, can any one help? thanks a lot!


[Desktop Entry]
Encoding=UTF-8
Name=x
Comment=Frontend for x
Exec=gksu -S -g /usr/local/bin/x
Terminal=false
Type=Application
Icon=x.png
Categories=Application;Network;Internet;
StartupNotify=false
Name[zh_TW]=x
GenericName[zh_TW]=
Comment[zh_TW]=
Name[en_US]=x
GenericName[en_US]=x

---

### Post by zvacet on 2008-04-02
System>preferences>main menu>on left side select internet and then on right side select **new item.** You will see launcher and enter name,comand...and that is it.

---

