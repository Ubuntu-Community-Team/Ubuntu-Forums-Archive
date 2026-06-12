---
title: "Gedit Question"
date: 2018-02-16
forum: General Help
---

### Post by shane_faulkinbury2 on 2018-02-16
In Gedit is there any way to get rid of the recently used files showing on the program?

---

### Post by vasa1 on 2018-02-16
See if [https://askubuntu.com/a/269874](https://askubuntu.com/a/269874) helps. But this route will stop all gtk3 applications, not just gedit, from writing to *~/.local/share/recently-used.xbel*.

Some applications have their own mechanism for maintaining a list of recent files and in such cases the answer may not apply.

I looked at gedit's options in Xubuntu 16.04 and didn't come across any obvious way, from within gedit, to prevent recent files from appearing and the answer I linked to stills works in 16.04 for gedit.

---

### Post by shane_faulkinbury2 on 2018-02-16
Well, the last command did the job.  Thanks vasa!

```
[COLOR=#111111][FONT=Consolas]echo gtk-recent-files-max-age=0 >> ~/.gtkrc-2.0[/FONT][/COLOR]
```

---

### Post by vasa1 on 2018-02-16
:???:

Gedit is a gtk3 application. Modifying *.gtkrc-2.0* shouldn't have any effect.

---

### Post by again? on 2018-02-17
There is .... 
```
gsettings set org.gnome.gedit.preferences.ui max-recents
```

However it seems the best you can do is set it to 1
```
gsettings set org.gnome.gedit.preferences.ui max-recents 1
```
Using "0" seems to allow infinite max-recents.

You can clear all recent files by running...
```
echo > ~/.local/share/recently-used.xbel
```

---

### Post by vasa1 on 2018-02-17
Your *~/.config/gtk-3.0/settings.ini* should look like this with "[Settings]" as the first line.```
[Settings]
gtk-recent-files-max-age=0
gtk-recent-files-limit=0
```

---

