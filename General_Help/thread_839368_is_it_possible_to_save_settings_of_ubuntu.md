---
title: "is it possible to save settings of ubuntu?"
date: 2008-06-24
forum: General Help
---

### Post by dinbrca on 2008-06-24
is it possible to save ubuntu settings like the about me pages? the theme i corrently use? the desktop wallpaper the login window? the keyboard layout? the screen resolution? screen saver? software icons, themes? all the settings of my current user.?  is it possible to export an settings file?

---

### Post by Taxman415a on 2008-06-24
Yes, these are all stored in various .files and subdirectories in your home directory. You can peruse them by opening a terminal and running a ls -l or opening your home folder in the GUI and hitting ctrl-h. 

A great way to save them is to install a backup program. Simplebackup is one of the easiest to use.  but it Go to synaptic or your favorite way to install programs and install it. Actually I can't recall off the top of my head if the package is called simplebackup or sbackup, it shows up under the System --> Administration menu. You can set it just to backup your home directory and then it will automatically backup all these settings you are asking about including your bookmarks, files stored in your documents folder, etc. Then go burn that backup to disc and keep a copy offsite :)

---

### Post by fragos on 2008-06-25
Some more configuration files are in /etc. You may or may not need them. These are some that I save and use when I install new versions of Ubuntu:

/etc/bluetooth/rfcomm.conf (bluetooth)
/etc/X11/xorg.conf (Wacom tablet parameters)
/etc/apache2/httpd.conf (support of PHP and others in Apache2)

---

