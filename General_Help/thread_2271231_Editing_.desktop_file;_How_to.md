---
title: "Editing .desktop file; How to???"
date: 2015-03-28
forum: General Help
---

### Post by ozark_hillbilly on 2015-03-28
After creating a Minidlna.desktop file and placing it under under /root/.config/autostart I am having difficulty editing it.
The software tells me it is not marked as 'Trusted' and therefore aborts any attempt to edit it under Nautilus. Changing the file attribute under permissions to where the
file is considered EXECUTABLE is not the answer either. As I am wanting to edit the file content and not execute it.

The only workaround is to delete the file in the /.config/autostart folder and replace it with an updated/edited version.

What is the correct method to mark a file as 'TRUSTED' and give me access for editing?

---

### Post by deadflowr on 2015-03-28
You need to open it directly in a text editor.
```
gedit file.desktop
```
should do.
Change the text editor to the editor of choice.
You can also open a text editor first and navigate to the file using the text editor's open function.

---

### Post by mc4man on 2015-03-28
Just to add - 
The trusted deal has nothing to do with opening in a text editor. In gnome .desktop files are not considered text files, (they are application/x-desktop),  so a d. click on attempts to launch the .desktop.
Only .desktop files in /usr/share/applications & probably /usr/local/share/applications can be launched via a d. click without being explicitly marked as executable (ie. trusted)

Note that you may not have permission to edit a file in /root/.config/autostart, &  why you are using that location escapes me altogether..

If you tend to open .desktops for editing a lot then another way to open in for instance gedit from the context menu is to create a nautilus action with Nautilus-Actions configuration tool.  (nautilus-actions package
screens are sorta self explanatory, I also like it to show directly in context menu so disable the root menu option in nautilus-actions > edit > preferences, scr. 4

---

### Post by ozark_hillbilly on 2015-03-28
@mc4man

I ended up going through Terminal mode with sudo gedit to get the file to open. As to why  I am using that "location" reference:
[https://help.ubuntu.com/community/MiniDLNA](https://help.ubuntu.com/community/MiniDLNA)
              To have minidlna load at startup, create the file ~/.config/autostart/minidlna.desktop:
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=MiniDLNA
Comment=Server to stream media over network
Exec=minidlna -f /home/$USER/.minidlna/minidlna.conf -P /home/$USER/.minidlna/minidlna.pid
StartupNotify=false
Terminal=false
Hidden=false

The tip on Nautilus-Actions is tremendously appreciated! A wonderful tool to now know about.

---

### Post by mc4man on 2015-03-29
> **ozark_hillbilly said:**
> @mc4man

I ended up going through Terminal mode with sudo gedit to get the file to open. As to why  I am using that "location" reference:
[https://help.ubuntu.com/community/MiniDLNA](https://help.ubuntu.com/community/MiniDLNA)
              To have minidlna load at startup, create the file ~/.config/autostart/minidlna.desktop:
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=MiniDLNA
Comment=Server to stream media over network
Exec=minidlna -f /home/$USER/.minidlna/minidlna.conf -P /home/$USER/.minidlna/minidlna.pid
StartupNotify=false
Terminal=false
Hidden=false

The tip on Nautilus-Actions is tremendously appreciated! A wonderful tool to now know about.
You really want to stop using sudo gedit, many threads on & alt. means available.
Don't see the connection between /root/.config/autostart & ~/.config/autostart/, you should be using the latter location which doesn't require root access, at least in a normal install..

---

