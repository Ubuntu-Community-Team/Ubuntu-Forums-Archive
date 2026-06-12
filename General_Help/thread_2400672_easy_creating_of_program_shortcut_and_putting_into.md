---
title: "easy creating of program shortcut and putting into &quot;start&quot; menu"
date: 2018-09-08
forum: General Help
---

### Post by marchello_lippi2 on 2018-09-08
Hi all, 
Is there any easy way to create program shortcut and putting it into "start" menu?
How come it is so complicated in ubuntu? 
Thanks for any suggestion.

---

### Post by ajgreeny on 2018-09-08
What start menu do you mean? 

Ubuntu with gnome does not have a menu of that type by default but has a dock on the left hand side of the screen. I think you can add a menu if you wish by installing one of the tweak packages.

If you open an application its own icon will appear in the dock and you can right click on it and choose to lock it there, I believe, though I don't use gnome and may have the wording wrong from the right click context menu; try it and see.

A possible alternative way to do what you want, however, would be to use another DE such as Xfce (Xubuntu) which has a classic desktop instead of Ubuntu with gnome.

---

### Post by marchello_lippi2 on 2018-09-08
My bad, I did not mentioned that I'm using Lubuntu. I got Eclipse, no icon appeared anywhere. I can run it using console: /home/user/Downloads/eclipse/eclipse, I wonder how do I create shortcut that can be placed and will be working in the "start menu" then.

---

### Post by ajgreeny on 2018-09-09
How did you install eclipse?

---

### Post by marchello_lippi2 on 2018-09-10
> **ajgreeny said:**
> How did you install eclipse?
Well, I just downloaded it from [https://www.eclipse.org](https://www.eclipse.org) and then extracted. 
Any idea how do I create link in Lubuntu "start menu" that will point to [COLOR=#000000]/home/user/Downloads/eclipse/eclipse ? 
No urgency though as it works well by starting from terminal/yakuake. Just... curious. [/COLOR]

---

### Post by ajgreeny on 2018-09-11
You can create an eclipse.desktop file (a text file launcher) and put it in ~/.local/share/applications. It should then be added to your menu automatically.

This is an example of a .desktop file from my system which you should be able to edit to make your own.
```
[Desktop Entry]
Name=Mousepad
Comment=Text editor
Exec=mousepad
Icon=/usr/share/icons/elementary-xfce/apps/128/xfce4-notes-plugin.png
Terminal=false
Type=Application
MimeType=text/plain
Categories=GTK;Utility;TextEditor;
StartupNotify=false
Path=
```

Are you aware that eclipse is available in the repos? Perhaps your version is newer than the repo version and you need to install direct from eclipse; just curious!

---

### Post by marchello_lippi2 on 2018-09-11
[COLOR=#C61919]ajgreeny,[/COLOR]
That worked! Thx!
It appeared in "standard" directory of my start menu in Lubuntu :) 
How do I move it to the "programming" directory?

---

### Post by marchello_lippi2 on 2018-09-11
Upd: I believe it makes sense to get latest software directly.
> [COLOR=#000000]Are you aware that eclipse is available in the repos?[/COLOR]

---

### Post by ajgreeny on 2018-09-11
> **marchello_lippi2 said:**
> [COLOR=#C61919]ajgreeny,[/COLOR]
That worked! Thx!
It appeared in "standard" directory of my start menu in Lubuntu :) 
How do I move it to the "programming" directory?
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

Not sure about moving it to the programming section as it's not a menu section I need or use, but if you have other applications in there open one of those launchers for that program either from ~/.local/share/applications or maybe /usr/share/applications in a text editor (right click ->Open with) and see what is in the line **Categories=**.
Copy that to your eclipse launcher text, and see it it moved; you may have to logout and in again for the change to occur.

---

### Post by marchello_lippi2 on 2018-09-11
Marked the thread as SOLVED. 
Will check later if "moving" is possible.

---

