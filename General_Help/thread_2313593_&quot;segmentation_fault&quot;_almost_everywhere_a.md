---
title: "&quot;segmentation fault&quot; almost everywhere after running out of /home disk space"
date: 2016-02-13
forum: General Help
---

### Post by Nano_St on 2016-02-13
Nautilus and most Gnome based / oriented applications are crashing with "Segmentation Fault", after a session where I run out of disk space for /home partition.
/home partition got completely filled up with Gimp swap while working with it under Gnome Desktop [SIZE=1](Ubuntu Studio Desktop), and all in desktop got freezed, and after that applications and desktop elements self closed one by one (Gimp, System Monitor, Nautilus, Taskbar and kfind) probably because of lack of disk space.  I had to manually power down the system after desktop being unresponsive for 15 minutes.[/SIZE]

I liberated some space booting in recovery mode, but now I can't open a Gnome session or Xfce Session because they're configured to be Nautilus based desktops, and Nautilus crashes with Segmentation Fault error.
However I can open a Kde Session, but most Gnome based or Gnome oriented applications crashes after trying to start them up, showing Segmentation Fault error when I start them up from a Terminal.  Some Kde applications also crash with Segmentation Fault.  System is barely usable in these conditions.
I think some configuration files got self corrupted while they were updating in a "just some bytes free" enviroment.

WHAT APPROACH would you recommend me to take to solve this?
[SIZE=1]I almost remove and reinstall Nautilus but then I realized I cannot remove it without removing whole Ubuntu Desktop package, and segmentation faults is not only happening with nautilus.[/SIZE]  It feels so bad... It all worked so fine for years and then I ruined it all for just a bunch of megabytes! :(

-------------UPDATE:
As blueridgedog suggested, it's seems to be a user specific issue, because I could log in to gnome with a new user and all seems to work normal.
Something crucial got corrupted, because even simplest applications crashes with "segmentation fault", such as gedit or gconf, as I try to open them in Kde with my traditional user.  Apparently it has to be something that is necessary even for file managing or at least graphical file browsing, as Gimp crashes when opening "save as" or "open" dialogs.
I found a NEW ERROR message when trying to log into gnome and before nautilus crashes: 
"gdm-binary(5618): WARNING: Unable to find users: no seat-id found"

I made a exhaustive kfind search and nothing got modified in .gnome2 and .gnome2private (I'm still using 10.10 [SIZE=1]because 11.04 didn't provide a way to recognize existent LUKS crypted partitions and a upgrade to 11.04 was necesary to upgrade with posterior releases[/SIZE])
Here's a LIST OF MODIFIED FILES when /home got full and system went uresponsive:
[SIZE=1]/home/myusername/.nvidia-settings-rc (0 bytes, but it's not affecting anything)
.config/gtk-2.0/gtkfilechooser.ini  (242 bytes, seems ok)
.local/share/gvfs-metadata folder:
   home, home-f85c328f.log
.gconf/system/networking subfolders:
   many %gconf.xml (0 bytes)
.kde/share/apps/cache (0 bytes)
.kde/share/kde4/services/nsplugin.desktop (0 bytes)
.mozilla/firefox/profile subfolders:
   urlclassifier.pset, cert8.db, key3.db
AND some others zero bytes files that were accidentaly loosed (no one important, I sent them to trash to try but segfaults continued, and files dissapeared after restoring it and suffer a power loss)[/SIZE]

WHAT I TRIED UNTIL NOW:
* Deleting zero bytes jpg in .thumbnails (as I've read that Nautilus sometimes crashes with 0 bytes image files)
* Deleting zero bytes %gconf.xml
* Running gconf-sanity-check-2 wich didn't return any message
I have some old /home backups but I don't know what could be useful to recover from them.
Any suggestion?

---

### Post by blueridgedog on 2016-02-14
Try creating a new user account and logging in via that account.  If that works, then is is user specific and related to temp/config files in your current user's home directory, which can be solved by deleting the appropriate config directories (.gnome etc).

---

### Post by Nano_St on 2016-02-14
Thanks from Argentina, blueridgedog.
As you guessed, this is user specific: I could log in to Gnome with a  new user, and everything seems to work normal.  I have many reasons to  continue using my traditional user loosing the minimum possible settings.  I'll give a try to the approach you suggested, but aparently nothing changed in .gnome folders when /home got full.
PS: I updated my post.

---

### Post by Nano_St on 2016-02-14
SOLVED!
    I tried erasing /home/myuser/.config/gtk-2.0/**gtkfilechooser.ini** wich was modified went disk went full, and it all returned to normality with not even one "segmentation fault" crash!!!.  Lucky me, apparently I didn't loose any noticeable setting or configuration. 
It has to be something crucial as GTK!  So many applications rely on it.  

The file seemed OK, but something was fatally wrong with it.  These were its contents:
```
[Filechooser Settings]
LocationMode=filename-entry
ShowHidden=false
ExpandFolders=true
ShowSizeColumn=true
GeometryX=558
GeometryY=248
GeometryWidth=770
GeometryHeight=561
SortColumn=modified
SortOrder=descending
```
After erasing, it regenerated and the only significative change was LocationMode=path-bar.  Somehow "filename-entry" was the one and only cause of "segmentation fault" almost everywhere.

I want to thank all of you in ubuntuforums.org community for all the light and help you gave me since 2009.  I'm a happy ubuntu studio user, because it rocks!

---

