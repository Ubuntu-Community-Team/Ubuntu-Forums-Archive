---
title: "How can I use this to create location icons (folder shortcuts) on the LXDE panel?"
date: 2013-03-08
forum: General Help
---

### Post by gotnexusbluz on 2013-03-08
The following information has been in circulation for LXDE users who want to add a panel shortcut to the shutdown functions:In a terminal session, create and open the new file:```
gksudo leafpad /usr/share/applications/lubuntu-logout.desktop
``` 

Then these commands are added to the file:
```

[Desktop Entry]
Name=Shutdown
Comment=Shutdown or Reboot
Icon=system-shutdown-panel
Exec=lubuntu-logout
#NoDisplay=true
Type=Application
Categories=Settings;
```

Shutdown then appears under the Preferences category when you create an Application Launch Bar on the Panel, and then press the Edit button. What I want to do is create such a file for opening pcman to a folder, such as Documents, Downloads, or Music. 

What I need help with is how to do this relative to the above example? The first four commands shown above appear to be self-explanatory. I expect that pcmanfm, followed by my path to the desire folder should follow "Exec=". But what is that statement "#NoDisplay=True?" Will I need this for the LXDE panel to display it somewhere within my Application Launch Bar => Edit options? Should I choose some other "Type" than "Application", and what are the options anyway? I don't think I understand the last statement either, "Categories=Settings;" either. 

I'm also wondering what part of the above code told the LXDE panel to display the Shutdown application under "Preferences" within the Application Launch Bar => Edit window. How would I be able to list or create a different category, and make LXDE display it there?

---

### Post by vasa1 on 2013-03-08
> **gotnexusbluz said:**
> ... What I want to do is create such a file for opening pcman to a folder, such as Documents, Downloads, or Music. 
...
I made the code below and put it in *~/.local/share/applications*. I keep modified .desktop files there rather than in */usr/share/applications*:```

[Desktop Entry]
Type=Application
Icon=system-file-manager
Name=MyFM
GenericName=File Manager
Comment=Browse the file system and manage the files
Categories=FileManager;Utility;Core;GTK;Favorites;
Exec=pcmanfm /usr/share/applications
StartupNotify=true
Terminal=false
MimeType=x-directory/normal;inode/directory;

```
It opens usr/share/applications when clicked on (Menu>Accessories>MyFM). I named it MyFM to distinguish it from the original PCManFM.

---

### Post by gotnexusbluz on 2013-03-08
Thanks!  

Is that folder ~/.local/share/applications supposed to be in the home directory? Mine doesn't have an applications folder in this path - should I create one?  

What I want to do is create one of these apps each (so I think that's what has to be done) for quick access to my Documents, Downloads, and Music folders. How would I have to modify the Exec command to do this (if I need to), while still redirecting it to /usr/share/applications?  

Can you recommend a good tutorial for an explanation and use of all these commands?   

Thanks again.    


> **vasa1 said:**
> I made the code below and put it in *~/.local/share/applications*. I keep modified .desktop files there rather than in */usr/share/applications*:
```
 
[Desktop Entry] Type=Application Icon=system-file-manager 
Name=MyFM GenericName=File Manager 
Comment=Browse the file system and manage the files 
Categories=FileManager;Utility;Core;GTK;Favorites; 
Exec=pcmanfm /usr/share/applications 
StartupNotify=true 
Terminal=false 
MimeType=x-directory/normal;inode/directory; 

``` 
It opens usr/share/applications when clicked on (Menu>Accessories>MyFM). I named it MyFM to distinguish it from the original PCManFM.

---

### Post by Dennis N on 2013-03-08
This explains the keys you can use:

[http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html)

#NoDisplay=True

the # causes the key to be ignored. If you remove the #, it will not be ignored and nothing will display in the menu. NoDisplay is not required, so you can also just delete the whole line.

Categories controls where in the menu your launcher appears.

To utilize ~/.local/share/applications, you can create it if necessary.

[B]Note:
[/B]
If you should want a launcher on the Desktop instead of being in the Menu, then put your .desktop file into the Desktop folder. No category is required for a Desktop launcher. If you did that with Shutdown, then you could shutdown by clicking on the Shutdown Icon on the desktop.

Example of a launcher to open 'Project' folder in your home folder:

```
[Desktop Entry]
Name=Project
Comment=Open Project Folder
Type=Application
Exec=pcmanfm /home/user-name/Project
Categories=GTK;Utility;
Icon=folder-new
```

You could save it as project-folder.desktop


Experiment, and good luck.

---

