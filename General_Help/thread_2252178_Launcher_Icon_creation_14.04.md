---
title: "Launcher Icon creation 14.04"
date: 2014-11-09
forum: General Help
---

### Post by felizcortez on 2014-11-09
I am trying to create a custom launcher for the scangearmp with a custom icon that I can add into the Dash and launcher bar on the left hand side of Ubuntu.  

I downloaded an icon image called Scanner.png and placed it in the following location with the following permissions.  It is a 256x256 image 

```
david@HP-Ubuntu:/usr/share/applications$ ls -lrt /usr/share/icons/Scanner.png 
-rw-r----- 1 root root 21642 Nov  9 18:15 /usr/share/icons/Scanner.png

```

I also created a .desktop file in the following location and verified the path to the executable.
> 
david@HP-Ubuntu:/usr/share/applications$ ls -lrt /usr/share/applications/scangearmp.desktop
-rwxr-xr-x 1 root root 165 Nov  9 20:57 /usr/share/applications/scangearmp.desktop

david@HP-Ubuntu:/usr/share/applications$ ls -lrt /usr/bin/scangearmp
-rwxr-xr-x 1 root root 223640 Feb  9  2010 /usr/bin/scangearmp


Here is the contents of the scangearmp.desktop file.

david@HP-Ubuntu:/usr/share/applications$

more scangearmp.desktop

```
[Desktop Entry]
Name=Scanner
Comment=Scan Utility
Exec=/usr/bin/scangearmp
Icon=/usr/share/icons/Scanner.png
Terminal=false
Type=Application
Categories=Application;

```

I cannot get this to show up when I type "scanner" in the Dash Search.  My desire is to create the custom icon and load it into the side bar so I can access my scanner easily.  I've done a few searches and followed a tutorial on Youtube and I still can't get this to work.  I hope I'm missing something simple.  Thanks for any help you can provide.

---

### Post by mc4man on 2014-11-10
May take a log out/in to show up in Dash
One could always test a .desktop with this (then lock to launcher if it shows
gtk-launch .desktop name, so here - 
gtk-launch scangearmp

---

### Post by felizcortez on 2014-11-10
> **mc4man said:**
> May take a log out/in to show up in Dash
One could always test a .desktop with this (then lock to launcher if it shows
gtk-launch .desktop name, so here - 
gtk-launch scangearmp

I have logged out after each trial and tried rebooting multiple times.  Neither has changed the behavior.

Question about the below command?
gtk-launcher scangearmp 

Do I have to specify the full path of the file? e.g.
gtk-launcher /usr/share/applications/scangearmp.desktop

Thanks

---

### Post by mc4man on 2014-11-10
> **felizcortez said:**
> I have logged out after each trial and tried rebooting multiple times.  Neither has changed the behavior.

Question about the below command?
gtk-launcher scangearmp 

Do I have to specify the full path of the file? e.g.
gtk-launcher /usr/share/applications/scangearmp.desktop

Thanks
No, it's simply gtk-launch name of the .desktop so for that one (not gtk-launcher either
```
gtk-launch scangearmp
```

Edit: maybe  try removing Categories=Application; [or use something else]("http://standards.freedesktop.org/menu-spec/latest/apa.html"), never seen Application as a Category myself

---

### Post by felizcortez on 2014-11-10
Running gtk-launch scangearmp launched the application.  However, the icon didn't show up in the bar on the left.

Tried changing categories to office, but that made no difference in terms of being able to see the information in Dash.

---

### Post by felizcortez on 2014-11-10
Running gtk-launch scangearmp launched the application.  However, the icon didn't show up in the bar on the left.

Tried changing categories to office, but that made no difference in terms of being able to see the information in Dash.

---

### Post by mc4man on 2014-11-11
Could be an   issue with the icon, maybe size? Try using a smaller icon, 48x48 or 64x64  would be typical.
For purpose of testing you can use any icon or no icon at all
(- with no icon specified you should get ? icon in launcher & 'empty text' icon in Dash

---

