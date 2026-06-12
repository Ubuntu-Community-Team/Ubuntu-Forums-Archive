---
title: "Session only lasted ten seconds"
date: 2007-06-04
forum: General Help
---

### Post by Death_Sargent on 2007-06-04
for some reason using any decent mac theme from gnome-look.org causes a "Session only lasted ten seconds" error

here is the session error log 

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "pete"
/etc/gdm/Xsession: Beginning session setup...
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SESSION_MANAGER=local/pete-laptop:/tmp/.ICE-unix/6555
Initializing nautilus-main-menu extension
Initializing gnome-mount extension
Unable to open desktop file file:///home/pete/Desktop/Cedega.desktop for panel launcher: No such file or directory

** (gsynaptics-init:6680): WARNING **: Using synclient
Debug: Loading Beagle.Util.Conf+IndexingConfig from indexing.xml
Debug: Loading Beagle.Util.Conf+DaemonConfig from daemon.xml
Debug: Loading Beagle.Util.Conf+SearchingConfig from searching.xml
/usr/bin/bonager:30: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
  import egg.trayicon 	# egg == python-gnome2-extras
Unknown parameter CoastingSpeedThreshold
Unable to open desktop file file:///home/pete/Desktop/Reserve.desktop for panel launcher: No such file or directory

(gnome-panel:6637): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 23
LOADED : /home/pete/app_launchers/ooo-writer.desktop
LOADED : /usr/share/applications/ooo-calc.desktop
LOADED : /usr/share/applications/ooo-impress.desktop
LOADED : /home/pete/.local/share/applications/ooo-draw.desktop
LOADED : /usr/share/applications/gimp-2.2.desktop
LOADED : /usr/share/applications/kde/amarok.desktop
LOADED : /usr/share/applications/firefox.desktop
LOADED : /usr/share/applications/gwget.desktop
LOADED : /home/pete/app_launchers/frostwire.desktop
LOADED : /usr/share/applications/kde/ktorrent.desktop
LOADED : /usr/share/applications/evolution-mail.desktop
LOADED : /usr/share/applications/skype.desktop
LOADED : /usr/share/applications/gaim.desktop
LOADED : /home/pete/app_launchers/EVE.desktop
LOADED : /home/pete/app_launchers/WOW.desktop
LOADED : /home/pete/app_launchers/(old)Oblivion.desktop
LOADED : /home/pete/app_launchers/Steam.desktop
LOADED : /home/pete/app_launchers/UT2004.desktop
HOME environment variable not set?
Launched application : 7095
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Checking mime type application/x-desktop
Checking mime type application/x-desktop
Checking mime type application/x-desktop
Checking mime type application/x-desktop
Checking mime type application/x-desktop
Checking mime type application/x-desktop
Checking mime type text/plain
Checking mime type text/plain
```

any ideas on what to do

---

### Post by Death_Sargent on 2007-06-04
anyone please

here are some links to the themes 

[http://www.gnome-look.org/content/show.php/AER-OS-XK?content=49990](http://www.gnome-look.org/content/show.php/AER-OS-XK?content=49990)

[http://www.gnome-look.org/content/show.php/OSX?content=31618](http://www.gnome-look.org/content/show.php/OSX?content=31618)

[http://www.gnome-look.org/content/show.php/OsX_MoD?content=54851](http://www.gnome-look.org/content/show.php/OsX_MoD?content=54851)

---

### Post by Death_Sargent on 2007-06-04
im open for any idea no matter how ill-witted it may sound

---

### Post by Rui Pais on 2007-06-04
You are bumping your thread too quickly. 
Thats considered not polite. Wait until someone with answers read it.

Go to a console (Ctrl+Alt+F1) and check the output of:
```
echo $HOME
```
and
```
ls -s /home
```

---

### Post by Death_Sargent on 2007-06-04
for 
```
echo $HOME
```

i get 

```
/home/pete
```

for

```
ls -s /home
```

i get

```
total 60
 4 guest  48 lost+found   4 pete   4 test

```

---

### Post by Rui Pais on 2007-06-04
uhmm, seems normal.

Do you remember doing anything special before that starts to happen?

There are some references to python stuff and a bonager (do you know this one?)

check if it's only a bad config on gnome:
```
mkdir gnome_BACKUP
mv gnome* gconf* gnome_BACKUP/
```
and then try to restart session.

---

### Post by Death_Sargent on 2007-06-04
that solved it now i just have to rebuid my settings thank you

---

### Post by Rui Pais on 2007-06-04
> **Death_Sargent said:**
> that solved it now i just have to rebuid my settings thank you

no problem :)

you can try move back the gnome folders one by one to your /home/pete folder till you find the bad one...
but usually one wastes more time then redoing  personal settings...

---

