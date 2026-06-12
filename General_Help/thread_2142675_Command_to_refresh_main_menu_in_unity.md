---
title: "Command to refresh main menu in unity"
date: 2013-05-06
forum: General Help
---

### Post by Cfhs_1 on 2013-05-06
Hello everyone!
I have created a small script that adds a .desktop file for a menu entry. However in order for it to work I must log out and back in after the script is finished in order to refresh the main menu. Is there not a command I could add to the end of my script that will refresh the menu for me automatically? I've done a few Google searches and came up empty handed. Thanks in advanced for your help.

-NCB

---

### Post by stinkeye on 2013-05-06
I don't know how relevant or helpful, but your post rang a bell and I searched through my notes and found
> after you edit a .desktop file you may need to refresh the desktop cache with
 sudo dpkg-reconfigure python-gmenu
Related post...
[http://ubuntuforums.org/showthread.php?t=1667513]("http://ubuntuforums.org/showthread.php?t=1667513")

---

### Post by Cfhs_1 on 2013-05-06
Thanks for your quick reply, however this doesn't seem to be the solution I'm looking for. It just gives an error. (python-gmenu is not installed by default in ubuntu 13.04) I need this script to work on fresh installations of ubuntu without having to install extra packages first.

---

### Post by stinkeye on 2013-05-06
Will reloading unity do it???
```
setsid unity
```

---

### Post by Cfhs_1 on 2013-05-06
> **stinkeye said:**
> Will reloading unity do it???
```
setsid unity
```

Just gave it a try. Didn't work.

---

### Post by Cfhs_1 on 2013-05-07
Bump!

Anyone else have any suggestions? There HAS to be a way to do this.

---

### Post by stinkeye on 2013-05-07
Hi again.
As a test I created a **mytest-launcher.desktop **  file and placed it in ~/.local/share/applications
and it shows up immediately when searching in the dash home and in the applications menu.

---

### Post by Cfhs_1 on 2013-05-09
> **stinkeye said:**
> Hi again.
As a test I created a **mytest-launcher.desktop **  file and placed it in ~/.local/share/applications
and it shows up immediately when searching in the dash home and in the applications menu.

I tried it, and can confirm that unity will automatically detect .desktop files in $HOME./local/share/applications I've went back and looked at my code again and discovered something. It seems that fresh installations don't have the applications folder under $HOME/.local/share. So in my script it is created with the mkdir command then my .desktop file is copied there. Something about this folder being created requires a logout/login before unity will "see" it or load .desktop files from there. The applications folder is created with standard user permissions and not root, so that can't be the issue. I believe I have pin pointed the issue, I'm just not sure how to fix it. Any ideas?

-NCB

---

### Post by stinkeye on 2013-05-09
I came across this command using gsettings to add a .desktop file to the launcher you may be able to use.
```
gsettings set com.canonical.Unity.Launcher favorites "$(gsettings get com.canonical.Unity.Launcher favorites | sed "s/, *'[COLOR="#EE82EE"]yourapp.desktop[/COLOR]' *//g" | sed "s/'[COLOR="#EE82EE"]yourapp.desktop[/COLOR]' *, *//g" | sed -e "s/]$/, '[COLOR="#EE82EE"]yourapp.desktop[/COLOR]']/")"
```

I can add a .desktop file from **~/.local/share/applications** to the launcher,
even when the .desktop file does not show with a dash search.

eg I created a new user account and created the directory **~/.local/share/applications** and placed
the **mytest.desktop** file in it.
Searched the dash. No results.
Ran the command...
```
gsettings set com.canonical.Unity.Launcher favorites "$(gsettings get com.canonical.Unity.Launcher favorites | sed "s/, *'[COLOR="#EE82EE"]mytest.desktop[/COLOR]' *//g" | sed "s/'[COLOR="#EE82EE"]mytest.desktop[/COLOR]' *, *//g" | sed -e "s/]$/, '[COLOR="#EE82EE"]mytest.desktop[/COLOR]']/")"
```
...and it shows up immediately in the launcher.

---

### Post by Cfhs_1 on 2013-05-09
> **stinkeye said:**
> I came across this command using gsettings to add a .desktop file to the launcher you may be able to use.
```
gsettings set com.canonical.Unity.Launcher favorites "$(gsettings get com.canonical.Unity.Launcher favorites | sed "s/, *'[COLOR="#EE82EE"]yourapp.desktop[/COLOR]' *//g" | sed "s/'[COLOR="#EE82EE"]yourapp.desktop[/COLOR]' *, *//g" | sed -e "s/]$/, '[COLOR="#EE82EE"]yourapp.desktop[/COLOR]']/")"
```

I can add a .desktop file from **~/.local/share/applications** to the launcher,
even when the .desktop file does not show with a dash search.

eg I created a new user account and created the directory **~/.local/share/applications** and placed
the **mytest.desktop** file in it.
Searched the dash. No results.
Ran the command...
```
gsettings set com.canonical.Unity.Launcher favorites "$(gsettings get com.canonical.Unity.Launcher favorites | sed "s/, *'[COLOR="#EE82EE"]mytest.desktop[/COLOR]' *//g" | sed "s/'[COLOR="#EE82EE"]mytest.desktop[/COLOR]' *, *//g" | sed -e "s/]$/, '[COLOR="#EE82EE"]mytest.desktop[/COLOR]']/")"
```
...and it shows up immediately in the launcher.

That's exactly what I needed! It's perfect! I was just about to give up hope! Thank you soo much!

---

