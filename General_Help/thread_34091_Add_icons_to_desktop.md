---
title: "Add icons to desktop"
date: 2005-05-13
forum: General Help
---

### Post by JulesH on 2005-05-13
Hi all,

I am a total newbie, and have just installed my first program using a .deb package.

I installed Opera web browser using "sudo dpkg -i nameofpackage.deb" from my Home folder, which now works OK if I type in 'Opera' from the command line, so at least the installation went OK.

How do I put an icon for it on the desktop or in a drop down menu? I can't even find it!

I also inadvertently put an entry in the 'Places' drop down menu, but I can't remove it. If I right click on it, this behaves just like a left click, and opens the folder. I am supposed to get a list of options, but there is none.

What do I do?

Regards,
Jules

---

### Post by exile on 2005-05-13
[QUOTE=JulesH]Hi all,

I am a total newbie, and have just installed my first program using a .deb package.

I installed Opera web browser using "sudo dpkg -i nameofpackage.deb" from my Home folder, which now works OK if I type in 'Opera' from the command line, so at least the installation went OK.

How do I put an icon for it on the desktop or in a drop down menu? I can't even find it!

I also inadvertently put an entry in the 'Places' drop down menu, but I can't remove it. If I right click on it, this behaves just like a left click, and opens the folder. I am supposed to get a list of options, but there is none.

What do I do?

Regards,
Jules[/QUOTE]
 I don't use opera so I haven't tried this but you can go to a command prompt and type this:

sudo gedit /usr/share/applications/Opera.desktop

in the file fill in the following details (you'll have to put in the path to where opera is installed)

[Desktop Entry]
Name=Opera
Comment=Opera Web Browser
Exec=[path to opera]
Icon=
Terminal=false
Type=Application
Categories=Application;Network;

save it and it should be in your network menu

To create an icon on your desktop:
1) right click on your desktop
2) goto Create Launcher on the menu
3) fill in the details (similar to how you would making an icon in Windows)

---

### Post by Sam on 2005-05-13
[QUOTE=JulesH]Hi all,

I am a total newbie, and have just installed my first program using a .deb package.

I installed Opera web browser using "sudo dpkg -i nameofpackage.deb" from my Home folder, which now works OK if I type in 'Opera' from the command line, so at least the installation went OK.

How do I put an icon for it on the desktop or in a drop down menu? I can't even find it!

I also inadvertently put an entry in the 'Places' drop down menu, but I can't remove it. If I right click on it, this behaves just like a left click, and opens the folder. I am supposed to get a list of options, but there is none.

What do I do?

Regards,
Jules[/QUOTE]
For the 'Places' menu problem, open any open dialog (from gedit, firefox, ...), and clic on the item on the left part then Remove.


EDIT: (for the icon) You can also copy the file you just created in /usr/share/applications to ~/Desktop.

---

### Post by Maestro23 on 2005-05-13
[QUOTE=JulesH]Hi all,

I am a total newbie, and have just installed my first program using a .deb package.

I installed Opera web browser using "sudo dpkg -i nameofpackage.deb" from my Home folder, which now works OK if I type in 'Opera' from the command line, so at least the installation went OK.

How do I put an icon for it on the desktop or in a drop down menu? I can't even find it!

I also inadvertently put an entry in the 'Places' drop down menu, but I can't remove it. If I right click on it, this behaves just like a left click, and opens the folder. I am supposed to get a list of options, but there is none.

What do I do?

Regards,
Jules[/QUOTE]


Also for Desktop icon, you can right click on the Desktop...Create New....Link to Application

---

### Post by JulesH on 2005-05-13
[QUOTE=exile]I don't use opera so I haven't tried this but you can go to a command prompt and type this:

sudo gedit /usr/share/applications/Opera.desktop

in the file fill in the following details (you'll have to put in the path to where opera is installed)

[Desktop Entry]
Name=Opera
Comment=Opera Web Browser
Exec=[path to opera]
Icon=
Terminal=false
Type=Application
Categories=Application;Network;

save it and it should be in your network menu

To create an icon on your desktop:
1) right click on your desktop
2) goto Create Launcher on the menu
3) fill in the details (similar to how you would making an icon in Windows)[/QUOTE]

Thanks for replying. I tried the first line (sudo etc) but got nothing! I'm not sure where Opera is installed to. I see an entry in /usr/bin/ for opera. Is this it?

I tried this:

[Desktop Entry]
Name=Opera
Comment=Opera Web Browser
Exec= /usr/bin/Opera
Icon=
Terminal=false
Type=Application
Categories=Application;Network;

Nothin shows up! Is there an entry for the Icon= ?

Jules

---

### Post by harryc on 2005-05-13
[QUOTE=JulesH]Thanks for replying. I tried the first line (sudo etc) but got nothing! I'm not sure where Opera is installed to.[/QUOTE]From any console as user;

```
which opera
```

---

### Post by exile on 2005-05-13
Check out [http://www.ubuntuguide.org/#menu-editor](http://www.ubuntuguide.org/#menu-editor)

The menu editor might be a nicer way of doing it.

You can found out where opera is by typing at the prompt 

locate opera

or

which opera

With gnome it've found that changes to the menu don't happen straight away. Look at that link above and there is a refresh gnome panel step.

Stick with it  :)

---

### Post by JulesH on 2005-05-13
[QUOTE=harryc]From any console as user;

```
which opera
```[/QUOTE]

Thanks. That sorted it. I now have a working entry in Applications/Internet/opera.

Great!

Now I still cannot delete that false entry in 'Places'. Sam mentioned some steps, but I don't see two panes in gedit. Whats wrong?

Jules

---

### Post by JulesH on 2005-05-13
[QUOTE=exile]Check out [http://www.ubuntuguide.org/#menu-editor](http://www.ubuntuguide.org/#menu-editor)

The menu editor might be a nicer way of doing it.

You can found out where opera is by typing at the prompt 

locate opera

or

which opera

With gnome it've found that changes to the menu don't happen straight away. Look at that link above and there is a refresh gnome panel step.

Stick with it  :)[/QUOTE]

Thanks. With all your help I got an entry in applications drop down menu.

However, I still cannot get rid of that false entry in 'Places'. I installed smeg, but it doesn't edit 'Places'. I'm stuck!

Jules

---

