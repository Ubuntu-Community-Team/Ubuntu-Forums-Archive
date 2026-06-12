---
title: "Creating Desktop Shortcuts"
date: 2012-11-03
forum: General Help
---

### Post by UbuNewbie123 on 2012-11-03
Is there a way to create desktop shortcuts in Ubuntu 12.10? I could not do it since 11.10... Really put me off Ubuntu because of these minor annoyances that I take for granted in Windows.

I can create shortcuts via my Cinnamon menu bar by right clicking on the apps. However, I cannot add shortcuts for the stuff in Places like my HDs.

I am also trying to create Wine shortcuts to run my Windows software. Any idea how to do all this?

---

### Post by mcduck on 2012-11-03
Sure, but that of course depends on the desktop environment you are using, not the Ubuntu version. :)

At least on Unity desktop, you can just use the Alacarte menu editor to add menu entries, and then drag&drop them from the Dash menu into your desktop. I've never used Cinnamon so I can't say much about that...


If nothing else works, and you are using Nautilus as your file manager, you can create desktop shortcuts easily from the right-click menu's "Create new document"-submenu by adding a basic .desktop file template in ~/Templates.

Here's a basic .desktop file you can use as the template:
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=
Exec=
Name[en_US]=Application launcher
Comment[en_US]=
Name=
Comment=
Icon=
```

---

### Post by robert shearer on 2012-11-03
If using Cinnamon from the ppa then Nemo not Nautilus will be the file manager.

see ...[http://ubuntuforums.org/showpost.php?p=12334477&postcount=2682](http://ubuntuforums.org/showpost.php?p=12334477&postcount=2682)

to create shortcuts with Cinnamon right click the desktop and select 'create launcher'.

to add items to the places menu open the file manager and the folder you want to add to places then select Bookmarks from the top menu and 'add bookmark'

---

### Post by exodus on 2013-06-09
> **mcduck said:**
> Sure, but that of course depends on the desktop environment you are using, not the Ubuntu version. :)

At least on Unity desktop, you can just use the Alacarte menu editor to add menu entries, and then drag&drop them from the Dash menu into your desktop. I've never used Cinnamon so I can't say much about that...


If nothing else works, and you are using Nautilus as your file manager, you can create desktop shortcuts easily from the right-click menu's "Create new document"-submenu by adding a basic .desktop file template in ~/Templates.

Here's a basic .desktop file you can use as the template:
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=
Exec=
Name[en_US]=Application launcher
Comment[en_US]=
Name=
Comment=
Icon=
```

In Ubuntu 13.04, I was having nothing but pain trying to create launcher icons for my custom install programs such as eclipse and sublime text which I downloaded and installed manually. This is the only post that has helped me to accomplish what I want. I logged in after quite a long time just to thank you!!!!

---

### Post by Popaul on 2013-07-02
Ubuntu 13.04 same than all previous versions. Not straight forward, but..
2 solutions, but the 1st one gives a white frame around the icon on the desktop, and the 'arrow' to show that this is a link... not nice.
1st solution, easy but not very esthetic... 
   Open Nautilus, 
      preferably as administrator as some files/directories may not work. For that you can start in Terminal and type 'sudo nautilus'
   find the directory/file/application for which you want the shorcut, right click and select 'Make Link' and put this link into the home/desktop folder.
   some generic icon will then appear on the desktop. Right click, 'Properties' so that you can change the name and the icon (right click on the icon and select a 'png' or other image format you want... but not a .ico format... this is for MS Windows... does not work here.

2nd solution much better as the icon on the desktop appears with no frame around and no arrow.
  Open Gedit or whatever plain text editor. You want to create a text file with a name xxx.desktop where xxx is the name you want to give to the file.
  One file for each 'shortcut' on the desktop.
  As said in previous post from mcduck, the file should contain:
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=
Exec=
Name[en_US]=Application launcher
Comment[en_US]=
Name=
Comment=
Icon=
  Now... [en_US] --> replace this with your locale. For ex. for me in the UK, it is [en_GB]
  if you have nothing to put in a line, like above in 'Name=' .... empty, you can ommit the line.
  Type: can be 'application' for ... to launch an application (clever!) or 'link' if it's a link to a file or a complete directory
For example, if you want to create a shortcut for a directory, e.g. your 'home' directory:
[Desktop Entry]
Version=1.0
Type=Link
Icon[en_GB]=gnome-panel-launcher
Name[en_GB]=MyHome
URL=/home/JoBlock
Name=JoBlockHome
Icon=/home/JoBlock/icons/gnubiff.png
   I am sorry, i did not dig to  much as I guess there are plenty of stuff to say on the various command you can have etc... but I hope this clarifies a few bits.

---

### Post by deadflowr on 2013-07-02
Desktop launchers only need to have Name,Exec,and Type.
Everything else is superlative.
If no icon is set, then it should set a generic system icon for it.
As long as the name,exec,and type are set and the file name is file.desktop
Place it in the applications folder
/usr/share/applications(system-wide use)
/home/username/.local/share/applications(per user-only use)

---

