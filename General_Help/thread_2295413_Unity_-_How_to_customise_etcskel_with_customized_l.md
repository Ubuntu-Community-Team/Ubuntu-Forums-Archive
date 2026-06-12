---
title: "Unity - How to customise /etc/skel with customized launcher"
date: 2015-09-18
forum: General Help
---

### Post by jonnymccullagh on 2015-09-18
Hi,
I am planning on installing Ubuntu on several school machines with users logging in against Active Directory. I've got that working but now I would like to show icons on the launcher for the software users are most likely to use. So for example I would like to add the /usr/share/applications/filezilla.desktop and possibly remove the Calc icon.
I realise that it can be done manually by clicking-and-dragging and at the command-line with 'gsettings set com.canonical.Unity.Launcher favorites'
 but I need this to be automated so was investigating what I could add to /etc/skel . Is there any way of manipulating the Launcher, the Wallpaper etc with files under /etc/skel ?
Or even a way of auto-running the gsettings set command as new users log in?
Thanks in advance.

---

### Post by deadflowr on 2015-09-18
Don't use /etc/skel for this, but instead create override files in /usr/share/glib02.0/schemas.
See
[http://askubuntu.com/questions/363754/how-can-i-set-default-applications-in-unity-launcher-for-other-users](http://askubuntu.com/questions/363754/how-can-i-set-default-applications-in-unity-launcher-for-other-users)
the same methodology can be used to set default wallpapers.

(The path for the background should be [org.gnome.desktop.background]
with the key as picture-uri =)

Note: no need to invoke interactive sudo (sudo -i) when running the glib-compile-schemas command, simply add sudo to the command is suffice.

Hope it works and helps.

---

### Post by jonnymccullagh on 2015-09-21
Perfect. Many thanks.

```
sudo vi /usr/share/glib-2.0/schemas/99_launcher.favorites.gschema.override
```
> 
[com.canonical.Unity.Launcher]
favorites = ['application://ubiquity.desktop','application://nautilus.desktop','application://firefox.desktop','application://filezilla.desktop','application://libreoffice-writer.desktop','application://ubuntu-software-center.desktop', 'unity://running-apps', 'unity://expo-icon', 'unity://devices']

```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```

Log in as a new user and Voila!

---

