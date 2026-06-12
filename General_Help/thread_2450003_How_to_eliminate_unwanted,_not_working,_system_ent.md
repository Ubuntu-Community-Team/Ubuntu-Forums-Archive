---
title: "How to eliminate unwanted, not working, system entries in autostart ?"
date: 2020-09-05
forum: General Help
---

### Post by Nosphky on 2020-09-05
Since making a clean, fresh install of UbuntuStudio 20.04.1 (with XFCE), the screensaver didn't cut in when the desktop was inactive. There was (and still is) an entry visible in the Settings Manager GUI under the autostart section "Screensaver (launch screensaver and locker program)" which I cannot edit or delete so I imagine it has been installed by the system. 

When I hover the mouse over it, I see the command is "usr/share/xscreensaver/xscreensaver-wrapper.sh -nosplash" but this doesn't work. More exactly, it starts an xscreensaver process but the screensaver itself never kicks in no matter the period of inactivity.

I got around the problem by deselecting this entry and making another entry myself with the simple command "xscreensaver --nosplash" and this starts up an xscreensaver process which works correctly whenever the pc is inactive for a set period.

I would like to clean up and remove the entry which does not work. I know that whatever entries I add are files contained within .config/autostart but where are the autostart files that are created by the system?  I cannot eliminate the non-working file by using the GUI so I am hoping someone can tell me where I can find the unwanted entry.

---

### Post by TheFu on 2020-09-05
usr/share/xscreensaver/xscreensaver-wrapper.sh
is VERY DIFFERENT from 
[COLOR="#FF0000"]**/**[/COLOR]usr/share/xscreensaver/xscreensaver-wrapper.sh

You probably want the second, assuming the command is correct.  Understanding absolute and relative paths for files is mandatory. That first / is important - crazy important.
Mine is **/usr/bin/xscreensaver -no-splash** - not in /usr/share.

My xscreensaver is controlled by the window manager. I don't use any DE.  If XFCE uses openbox, then there is ~/.config/openbox/autostart which should list commands to be run.  Back when I used openbox, I'd setup keyboard maps, mouse/touchpad settings, remove some bluetooth modules AND start the screen saver:
```
/usr/bin/xscreensaver -no-splash  &
```

---

### Post by ajgreeny on 2020-09-05
I have been using Xubuntu for many years and have always used xscreensaver simply to show all my own photographs though I have never needed a script to autostart this.

Using xcfe4-settings-manager **Session and Startup** I have the xscreensaver set using the same command, but using the shortened pathway, as shown by TheFu, ie ***xscreensaver -no-splash***

Why does it need a script to start it rather than using the autostart facility available already in xfce4's settings?

---

### Post by Nosphky on 2020-09-06
Thanks for the reply,TheFu. The missing initial slash was my mistake. I just rechecked and the command in the Settings Manager GUI > Sessions & Startup > Application Autostart section is in fact /usr/share/xscreensaver/xscreensaver-wrapper.sh -nosplash.  That was my mistake.

As for the path, I checked and the xscreensaver-wrapper.sh file is in /usr/share/. When I made the clean install of 20.04.1, I just did a plain old vanilla install and had nothing to do with any choices of where stuff was installed. After install, I changed my home directory to a separate hard disk where it resides since long time.

UbuntuStudio doesn't use openbox as far as I can tell.

Since I do have the xscreensaver working correctly now from the autostart entry I made, all I would like to do is clean out the autostart entry which wants to go thro that wrapper.sh and which doesn't start a working screensaver.

---

### Post by Nosphky on 2020-09-06
Thanks for the reply, ajgreeny.  I did say in my post that I now had xscreensaver working with an entry I made myself in the settings manager, autostart section. And it was simply what you quoted above - xscreensaver -nosplash.

I don't know why the clean install of 20.04.1 UbuntuStudio with XFCE put that wrapper shell in the /usr/share/ path but looking at the script, it seems to have something to do with logins - more than that I cannot say because it's past my competence level.

In any case, all I want to do now is remove that unwanted and non-working entry from the autostart settings in the Settings Manager. It cannot be removed or edited from within the GUI so I am hoping someone can say where the system autostart file entries are held. Any autostart entries I create myself get installed in my /.config/autostart/ directory but those made by the system at install time do not.

---

### Post by Nosphky on 2020-09-06
Thanks for the reply, ajgreeny.  I did say in my post that I now had xscreensaver working with an entry I made myself in the settings manager, autostart section. And it was simply what you quoted above - xscreensaver -nosplash.

I don't know why the clean install of 20.04.1 UbuntuStudio with XFCE put that wrapper shell in the /usr/share/ path but looking at the script, it seems to have something to do with logins - more than that I cannot say because it's past my competence level.

In any case, all I want to do now is remove that unwanted and non-working entry from the autostart settings in the Settings Manager. It cannot be removed or edited from within the GUI so I am hoping someone can say where the system autostart file entries are held. Any autostart entries I create myself get installed in my /.config/autostart/ directory but those made by the system at install time do not.

---

### Post by Nosphky on 2020-09-07
I found where the system autostart files are stored. Just a quick note in case anyone else has similar problem with system autostart entries.

They are in:    /etc/xdg/autostart

---

