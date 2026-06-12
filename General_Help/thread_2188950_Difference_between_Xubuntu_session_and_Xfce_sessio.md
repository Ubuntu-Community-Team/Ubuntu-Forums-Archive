---
title: "Difference between Xubuntu session and Xfce session?"
date: 2013-11-20
forum: General Help
---

### Post by vasa1 on 2013-11-20
What are the differences between the two sessions?

I installed **xubuntu-desktop --no-install-recommends** on Lubuntu 13.10 and I see both Xubuntu session and Xfce session  when I check which login sessions are available.

---

### Post by Toz on 2013-11-20
> I installed xubuntu-desktop --no-install-recommends on Lubuntu 13.10
Is xubuntu-default-settings installed? I think it should be if you have the xubuntu session option.


Here is what I think: If you compare the differences in environment variables (specifically related to XDG*) between the two sessions you get:
[LIST=1]
[*]Xfce Session
```
XDG_VTNR=7
XDG_SESSION_ID=c4
XDG_MENU_PREFIX=xfce-
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session1
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
[COLOR="#FF0000"]**XDG_CONFIG_DIRS=/etc/xdg/xdg-xfce:/usr/share/upstart/xdg:/etc/xdg:/etc/xdg**[/COLOR]
XDG_SEAT=seat0
[COLOR="#FF0000"]**XDG_DATA_DIRS=/usr/share/xfce:/usr/local/share/:/usr/share/:/usr/share**[/COLOR]
XDG_RUNTIME_DIR=/run/user/1000
XDG_CURRENT_DESKTOP=XFCE
```
[*]Xubuntu Session
```
XDG_VTNR=7
XDG_SESSION_ID=c6
XDG_MENU_PREFIX=xfce-
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session2
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
[COLOR="#FF0000"]**XDG_CONFIG_DIRS=/etc/xdg/xdg-xubuntu:/usr/share/upstart/xdg:/etc/xdg:/etc/xdg**[/COLOR]
XDG_SEAT=seat0
[COLOR="#FF0000"]**XDG_DATA_DIRS=/usr/share/xubuntu:/usr/local/share/:/usr/share/:/usr/share**[/COLOR]
XDG_RUNTIME_DIR=/run/user/1000
XDG_CURRENT_DESKTOP=XFCE
```
[*]
[/LIST]
The two main differences are XDG_CONFIG_DIRS and XDG_DATA_DIRS.

XDG_CONFIG_DIRS is used to specify which template files are used to create the initial ~/.config file structure (xfce=/etc/xdg, xubuntu=/etc/xdg/xdg-xubuntu). The important thing to note here is that this is only valid for the first login after a new account is created (meaning that if you want to see the real difference between the default states of these sessions, you need to start with a clean ~/.config). Every login thereafter will use the existing .config files regardless of the session selected (see caveat below). If you have a look at those directories, you'll see some differences between the template files. The /etc/xdg/xdg-xubuntu files give xubuntu that different look-and-feel from default xfce. 
Caveat: note that some of those template files are not copied to ~/.config by default (example menu files), meaning that there is some sort of inheritance from the base directories happening - as is evidenced by different menu structures for each session (/etc/xdg/menus vs /etc/xdg/xdg-xubuntu/menus). 

XDG_DATA_DIRS currently contains the additional menu items that the xubuntu session adds to the main menu as well as the default list of file associations.

There are also a few other differences that you can see by reviewing the contents of those directories.

---

### Post by vasa1 on 2013-11-20
@Toz, thank you for replying.

Yes, I do see that **xubuntu-default-settings** is installed.

I had come across */usr/share/xubuntu/applications* and it has some .desktop files that cause entries specific to Xubuntu to appear in the Application Menu dropdown. These include links to the Xubuntu website and to */usr/share/xubuntu-docs/about/xubuntu-index.html*.

As you point out, it's likely that the Xubuntu session has some additional features but, as of now, the menu differences are the most obvious .

---

### Post by vasa1 on 2013-11-30
Lots more here:
[http://ubuntuforums.org/showthread.php?t=1895108](http://ubuntuforums.org/showthread.php?t=1895108)
and
[http://ubuntuforums.org/showthread.php?t=2055912](http://ubuntuforums.org/showthread.php?t=2055912)

---

