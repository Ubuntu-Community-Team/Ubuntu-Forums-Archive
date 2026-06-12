---
title: "Root user theme discrepancy (GNOME)"
date: 2006-10-02
forum: General Help
---

### Post by Zaryun on 2006-10-02
I've [already searched the forums]("http://www.ubuntuforums.org/showthread.php?t=268560"), but none of the problems seem to match mine.

Themes function fine when opening apps as a normal user, but as soon as I open something as root, the theme changes to a previous theme I had, and one that I'm not particularly fond of.

When I attempt to manually change the theme for root with "gksudo gnome-theme-manager," I get the following warning (which is also displayed using the old theme):

> Unable to start the settings manager 'gnome-settings-daemon'. Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

After clicking "OK," the theme manager starts successfully, but despite trying multiple theme options, the theme manager stays styled exactly the same.

I have not installed any other window manager and there's nothing I can recall that may have caused this. It just randomly decided to break.

Incidentally, when running "gksudo gnome-theme-manager," the following errors are displayed:

> 
(gnome-theme-manager:13284): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Window manager warning: Failed to read theme from file /usr/share/themes/Office/metacity-1/metacity-theme-1.xml: Failed to open file '/usr/share/themes/Office/metacity-1/metacity-theme-1.xml': No such file or directory

(gnome-theme-manager:13288): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion `icon_info != NULL' failed

(gnome-theme-manager:13288): Gtk-CRITICAL **: gtk_icon_info_free: assertion `icon_info != NULL' failed


Any help would be appreciated, as I do run GUI applications as root often.

---

### Post by aysiu on 2006-10-02
Does pasting these commands into the terminal help? ```
ln -s ~/.themes /root/.themes
ln -s ~/.icons /root/.icons
```

---

### Post by jazee on 2006-10-02
Nice I had been looking for this same thing. Thanks that works perfectly.

---

### Post by IYY on 2006-10-02
Cool, I've never even thought of doing that. :eek:

---

### Post by Zaryun on 2006-10-02
Thanks, although unfortunately that doesn't work. The same error messages and theme appear when running apps as root. :/

I think I've found the culprit theme to be "Traditional." I ran "locate Traditional" from Terminal and found /usr/share/Traditional, where I proceeded to rename index.theme to something else. This also didn't work, although I've had bad experiences with caching and perhaps the theme is cached elsewhere. Is there anyway to refresh it?

Still wondering about the errors when running the theme manager as root -- I'm sure that has something to do with it.

---

