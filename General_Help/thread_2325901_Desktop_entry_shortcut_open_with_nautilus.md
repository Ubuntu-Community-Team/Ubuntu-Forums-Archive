---
title: "Desktop entry shortcut open with nautilus"
date: 2016-05-26
forum: General Help
---

### Post by markku2 on 2016-05-26
Hello

I'm trying to make a desktop entry using gedit to start an application. How to make a desktop entry file so it starts an executable file as if I douple click it in nautilus?

So what to write on the line after Exec=
I've tried just filepath and gnome-terminal -e "filepath" after the Exec= but it fails to start. It only starts properly when I douple click the file in nautilus.

Thanks in advance, hope you can understand what i'm trying to achieve.
I'm using 16.04 Ubuntu GNOME 64bit.

---

### Post by ajgreeny on 2016-05-26
I don't know ubuntu-gnome at all but if you list .desktop files with ```
ls /usr/share/applications
``` and then open one of those with ```
gedit /usr/share/applications/*filename*.desktop
```you should be able to adapt it to your own application.

Here's mine for **firefox** to give you an example.
```

[Desktop Entry]
Version=1.0
Name=Firefox
Comment=Browse the World Wide Web
GenericName=Web Browser
Keywords=Internet;WWW;Browser;Web;Explorer
Exec=firefox %u
Terminal=false
Type=Application
Icon=firefox
Categories=GNOME;GTK;Network;WebBrowser;
StartupNotify=false

```

---

### Post by markku2 on 2016-05-28
Thank you for your response. The program isn't listed in the "ls" list.  But in this particular case the executable fails to start from the  .desktop file. It starts when I douple click the executable in the folder it's in with nautilus.
```

Name=executable
Comment=executable
Terminal=false
Type=Application
Exec=/home/markku/Programs/executable %u
Icon=/home/markku/Programs/icon.png
Type=Application

```
Like I previously mentioned I've tried different options after the Exec= but none I've tried worked.
So I think the solution might be to mimic the case when I open the file with nautilus. Maybe somehow open with nautilus or open with run software?

---

### Post by ajgreeny on 2016-05-28
Where is the executable that you can double click to start the application?

To start that with a .desktop file it must either be in one of your $PATH folders which you can see with command ```
echo $PATH
```or you must use the full pathway to the executable in the **Exec=** line.

---

