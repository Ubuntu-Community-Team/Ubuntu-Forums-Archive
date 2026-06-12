---
title: "How to add favorites to shotcut"
date: 2022-01-01
forum: General Help
---

### Post by satimis on 2022-01-01
How to add favorites to shotcut

I have Shotcut AppImage download on Shotcut website.  I can start it on Terminal running;```

./shotcut-linux-x86_64-211224.AppImage
```

Please advise how to add it to Favorites.

Thanks

Regards

---

### Post by deadflowr on 2022-01-01
If an application you have doesn't create or have a launcher you need to create it yourself.
[https://linuxconfig.org/how-to-create-an-integrated-application-launcher-for-an-appimage-file-in-ubuntu]("https://linuxconfig.org/how-to-create-an-integrated-application-launcher-for-an-appimage-file-in-ubuntu")
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles")
These should give you some reference points, but in general you need to

Create a Desktop Entry text file.
The text file only truly requires 3 entries, but typically you'll want 4.
Those are the Name, Type, Exec, and optionally Icon.
It would look like this:
```
[Desktop Entry]
Name=Foo
Type=Application
Exec=command used to launch app goes here
Icon=Bar
```
then save it to the /home/username/.local/share/applications directory as a .desktop file like shotcut.desktop

Note that the Exec should be the full path name.
Since it doesn't or won't know what ./shotcut references otherwise, but will understand something like /home/me/shotcut.
If that make sense.

Alternative to that you could try your hand at using the appimagelauncher desktop integration tool from here:
[https://github.com/TheAssassin/AppImageLauncher]("https://github.com/TheAssassin/AppImageLauncher")

---

### Post by satimis on 2022-01-02
> **deadflowr said:**
> If an application you have doesn't create or have a launcher you need to create it yourself.
[https://linuxconfig.org/how-to-create-an-integrated-application-launcher-for-an-appimage-file-in-ubuntu]("https://linuxconfig.org/how-to-create-an-integrated-application-launcher-for-an-appimage-file-in-ubuntu")
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles")
These should give you some reference points, but in general you need to

Create a Desktop Entry text file.
The text file only truly requires 3 entries, but typically you'll want 4.
Those are the Name, Type, Exec, and optionally Icon.
It would look like this:
```
[Desktop Entry]
Name=Foo
Type=Application
Exec=command used to launch app goes here
Icon=Bar
```
then save it to the /home/username/.local/share/applications directory as a .desktop file like shotcut.desktop

Note that the Exec should be the full path name.
Since it doesn't or won't know what ./shotcut references otherwise, but will understand something like /home/me/shotcut.
If that make sense.

Alternative to that you could try your hand at using the appimagelauncher desktop integration tool from here:
[https://github.com/TheAssassin/AppImageLauncher]("https://github.com/TheAssassin/AppImageLauncher")

Thanks for your advice.

Performed following steps on Terminal;

$ sudo nano /home/satimis/.local/share/applications/shotcut

Copy following contents on the file```

[Desktop Entry]
Name=Shotcut
Type=Application
Exec=/home/satimis/Music/shotcut-linux-x86_64-211224.AppImage
Icon=Bar
```

Save and reboot

But I couldn't find Shotcut/Bar icon on Activities ?

I haven't tried Launcher.  It is not installed on Ubuntu 20.04

Regards

---

### Post by KBar on 2022-01-02
> **satimis said:**
> $ sudo nano /home/satimis/.local/share/applications/[COLOR=#ff0000]shotcut[/COLOR]

That should be shotcut.desktop (per XDG's specification [https://specifications.freedesktop.org/desktop-entry-spec/latest/](https://specifications.freedesktop.org/desktop-entry-spec/latest/)).

```
Icon=Bar
```

Leave it empty or find a path to its corresponding icon. Also, you may find some generic ones in some of the subdirectories in */usr/share/icons*.

---

### Post by satimis on 2022-01-02
> **kbar said:**
> That should be shotcut.desktop (per XDG's specification [https://specifications.freedesktop.org/desktop-entry-spec/latest/](https://specifications.freedesktop.org/desktop-entry-spec/latest/)).

```
Icon=Bar
```

Leave it empty or find a path to its corresponding icon. Also, you may find some generic ones in some of the subdirectories in */usr/share/icons*.
Delete the line Icon=Bar

$ cat /home/satimis/.local/share/applications/shotcut ```

[Desktop Entry]
Name=shotcut
Type=Application
Exec=/home/satimis/Music/shotcut-linux-x86_64-211224.AppImage
```

Reboot

Still couldn't find shotcut on Activities

Regards

---

### Post by KBar on 2022-01-02
Did you rename the desktop entry to shotcut.desktop?

---

### Post by satimis on 2022-01-02
> **kbar said:**
> Did you rename the desktop entry to shotcut.desktop?
This is the Shotcut AppImage.  I haven't installed Shotcut on Ubuntu 20.04

Where can I find shotcut.desktop ?

Regards

---

### Post by KBar on 2022-01-02
> **satimis said:**
> This is the Shotcut AppImage.  I haven't installed Shotcut on Ubuntu 20.04

Where can I find shotcut.desktop ?

Regards

No. The file you're manipulating, */home/satimis/.local/share/applications/shotcut* is a desktop entry and to be recognized as such, you need to append the *.desktop* extension to its end. Rename the file to */home/satimis/.local/share/applications/shotcut.desktop*

> **deadflowr said:**
> then save it to the /home/username/.local/share/applications directory as a .desktop file like **shotcut.desktop**

> **kbar said:**
> That should be **shotcut.desktop** (per XDG's specification [https://specifications.freedesktop.org/desktop-entry-spec/latest/](https://specifications.freedesktop.org/desktop-entry-spec/latest/)).

---

### Post by satimis on 2022-01-02
> **kbar said:**
> No. The file you're manipulating, */home/satimis/.local/share/applications/shotcut* is a desktop entry and to be recognized as such, you need to append the *.desktop* extension to its end. Rename the file to */home/satimis/.local/share/applications/shotcut.desktop*
On Terminal run;```

$ sudo mv /home/satimis/.local/share/applications/shotcut /home/satimis/.local/share/applications/shotcut.desktop
```

Activities -> shotcut
Now I can find its icon to start Shotcut

After having started Shotcut;
right-click its icon on menu bar -> Add to Favorites

Now I can start Shotcut on menu bar.  Thanks

Regards

---

### Post by KBar on 2022-01-02
FYI, you don't have to run commands with **sudo** if the owner is you, which is expected since you're in your own home directory. **ls -l** shows both owner and group name.

---

### Post by satimis on 2022-01-02
> **kbar said:**
> FYI, you don't have to run commands with **sudo** if the owner is you, which is expected since you're in your own home directory. **ls -l** shows both owner and group name.
Noted and thanks

Regards

---

### Post by KBar on 2022-01-02
No problem. I'm glad that we could help.

Happy New Year.

---

