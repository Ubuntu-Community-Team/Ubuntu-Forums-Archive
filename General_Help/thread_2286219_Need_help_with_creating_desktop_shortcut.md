---
title: "Need help with creating desktop shortcut"
date: 2015-07-10
forum: General Help
---

### Post by can5 on 2015-07-10
Hello, I'm trying to execute the following command by clicking an icon on desktop:

```
LANG=EN geany
```

I tried creating a Bash script however it just opened the file with Gedit. How can I create a shortcut and execute it?

---

### Post by papibe on 2015-07-10
Hi can5.

Take at look this couple of tutorials: [Unity Launchers and Desktop Files]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles"), and [How can I edit/create new launcher items in Unity by hand?]("http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand")

Let us know if you can take it from there, or you have more questions.
Regards.

---

### Post by can5 on 2015-07-10
Hi, thanks for your reply. I came across with those pages before. Creating a launcher isn't exactly what I need. I want to execute command: LANG=EN geany

I tried the instructions again, at the pages you recommend:

```
[Desktop Entry]
Version=1
Name=Geany
Comment=Geany IDE
Exec=LANG=EN geany
Icon=/usr/share/icons/hicolor/scalable/apps/geany.svg
Terminal=true
Type=Application
Categories=Application;
```

However it gave me error (translation: an error occured while starting application)

---

### Post by mc4man on 2015-07-10
Really don't know except the Exec= line in a .desktop can use/set an env
Maybe - 
Exec=env LANG=EN geany
or 
Exec=env LANG=EN geany %f
(assuming LANG=EN is the correct way to set the env..

edit:
otherwise if you can achieve via a small script, maybe with an export, then set the Exec= to 
Exec=/path/to/script

---

