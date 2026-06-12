---
title: "Adding to the Gnome menu"
date: 2007-07-05
forum: General Help
---

### Post by stchman on 2007-07-05
Hello all, I have been trying to add the following to the Applications--->Games menu:

[Desktop Entry]
Name=Microsoft Hearts
Comment=Play Microsoft Hearts
Categories=GNOME;Application;Game;
Encoding=UTF-8
Exec=/usr/bin/wine /opt/mshearts/mshearts.exe
Icon=/opt/mshearts/mshearts_icon.png
Terminal=false
Type=Application 

I save it as the following file /usr/share/applications/mshearts.desktop

Problem is that when I save data to the file there is no menu entry at all.  I have read that the Games portion of the Menu is called Game.

What am I doing wrong?  Do you need to reboot, restart the Gnome menu?  Yes I have a valid copy of Windows XP so I can use MSHearts.

Thanks.

---

### Post by deepclutch on 2007-07-05
u can edit and add menu using alacarte gnome menu editor.go to menu System>preferences>Menu layout.as simple ;)

---

### Post by stchman on 2007-07-05
> **deepclutch said:**
> u can edit and add menu using alacarte gnome menu editor.go to menu System>preferences>Menu layout.as simple ;)

I know this, I was trying to do it this way.  This method would be useful when  installing applications in a script.

---

### Post by deepclutch on 2007-07-05
Oh yes.but u can refer freedesktop.org standard for that.
[http://developer.gnome.org/arch/desktop/panel.html](http://developer.gnome.org/arch/desktop/panel.html)
and:
[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

and do u know that there is a package called menu and menu-xdg which will show as Debian menu in Applications.is there for Debian and Ubuntu.
[http://alioth.debian.org/docman/view.php/30046/2/menu-one-file.html](http://alioth.debian.org/docman/view.php/30046/2/menu-one-file.html)
[http://forums.debian.net/viewtopic.php?p=81451&sid=c7390bf25738c5ee3cfda5f581a30b64](http://forums.debian.net/viewtopic.php?p=81451&sid=c7390bf25738c5ee3cfda5f581a30b64)
[http://www.arsgeek.com/?p=110](http://www.arsgeek.com/?p=110)

---

### Post by Brucevdk on 2007-07-05
> **stchman said:**
> 
[Desktop Entry]
Name=Microsoft Hearts
Comment=Play Microsoft Hearts
Categories=GNOME;Application;Game;
Encoding=UTF-8
Exec=/usr/bin/wine /opt/mshearts/mshearts.exe
Icon=/opt/mshearts/mshearts_icon.png
Terminal=false
Type=Application 


Sounds rather silly but there's a space behind *Type=Application*, is this space present in */usr/share/applications/mshearts.desktop* aswell? If so, please remove it.

---

### Post by stchman on 2007-07-05
> **Brucevdk said:**
> Sounds rather silly but there's a space behind *Type=Application*, is this space present in */usr/share/applications/mshearts.desktop* aswell? If so, please remove it.

I just checked the original and the space does not exist.  It is probably there when I copy-paste the code in there.

---

### Post by dannyboy79 on 2007-07-05
sometimes you have to refresh the menu, i know I had to when I used the Debian Menu, but I forget the command, try to just restart, or maybe it's menu-update? Or kill the gnome-panel and it might refresh the menu?

BUt I always just use the menu editor myself. I don't understand what you mean about adding applications in a script? you can still do it the same way thru the menu editor.

---

### Post by stchman on 2007-07-05
> **dannyboy79 said:**
> sometimes you have to refresh the menu, i know I had to when I used the Debian Menu, but I forget the command, try to just restart, or maybe it's menu-update? Or kill the gnome-panel and it might refresh the menu?

BUt I always just use the menu editor myself. I don't understand what you mean about adding applications in a script? you can still do it the same way thru the menu editor.

Lets say you have a script add a pre-compiled binary.  The pre-compiled binary does not add to the menu.  I would like a script to install the application and then add a Gnome menu entry.  For .deb this is usually not needed as they will update the menu.

---

### Post by dannyboy79 on 2007-07-05
i see. that makes sense. that would be a cool script then, if you would make it so that the script runs, asks you what image you want to use, so on and so forth. cool idea

---

