---
title: "ubuntu tweak crash"
date: 2013-05-07
forum: General Help
---

### Post by Hodevah on 2013-05-07
Can't seem to figure it out. I run Gnome 3. I have Ubuntu Tweak installed yet each time I attempt to run it. It crashes. 
It crashes from the panel and it seems to crash from the Terminal too. 

```
user@user-desktop:~$ ubuntu-tweak
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : Default
[utils.icon][WARNING] Icon 'gconf-editor' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'gconf-editor' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'gnome-session-hibernate' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'gnome-session-hibernate' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'gnome-app-install' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'gnome-app-install' not present in theme (icon.py:32)
[utils.icon][WARNING] get_from_list for folder-home failed, try next (icon.py:56)
[utils.icon][WARNING] get_from_list for folder-home failed, try next (icon.py:56)
[utils.icon][WARNING] Icon 'application-x-theme' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'application-x-theme' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'computerjanitor' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'computerjanitor' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'gconf-editor' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'gconf-editor' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'gnome-app-install' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'gnome-app-install' not present in theme (icon.py:32)
[utils.icon][WARNING] get_from_list for folder-home failed, try next (icon.py:56)
[utils.icon][WARNING] get_from_list for folder-home failed, try next (icon.py:56)
[utils.icon][WARNING] Icon 'application-x-theme' not present in theme (icon.py:32)
[utils.icon][WARNING] Icon 'application-x-theme' not present in theme (icon.py:32)

(ubuntu-tweak:6645): Gtk-ERROR **: GtkBox child GtkTreeView minimum width: -1 < 0 for height 339
Trace/breakpoint trap
```

This did  not seem to work either to have UT for 13.04.


  ```

sudo add-apt-repository ppa:tualatrix/ppa sudo apt-get update sudo apt-get upgrade -y
```

---

### Post by grahammechanical on 2013-05-07
You are trying to run three commands one after the other without telling apt-get that they are separate commands. Run them as single commands or

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo add-apt-repository ppa:tualatrix/ppa && sudo apt-get update && sudo apt-get upgrade -y
```
[/FONT][/COLOR]
Regards.

---

### Post by Hodevah on 2013-05-08
Yes. I believe I did. It just happened to come out as the way as you see it because I copied/pasted all the commands _once_ (rather than individually) and had them pasted as you see them above in CODE.

What do all the Warnings in first post I made mean. I had Ubuntu Tweak installed prior to the 13.04. Then after the upgrade a couple of programs, including the Ubuntu Tweak just crash.

---

### Post by fantab on 2013-05-08
Ubuntu Tweak is for Ubuntu_Unity, AFAIK. If you are using Gnome-Shell then you need 'gnome-tweak-tool'. Moreover, compiz, which Unity needs, and on which Ubuntu_Tweak depends,  is not compatible with Gnome-Shell/Gnome.

---

