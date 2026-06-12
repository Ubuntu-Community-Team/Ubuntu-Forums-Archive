---
title: "Lost all icons and file associations"
date: 2014-05-16
forum: General Help
---

### Post by rlgribble on 2014-05-16
I was trying to change the icon for a single file type and eventually ran update-mime-database -r /usr/share/mime.  After doing so, the system lost all file associations (it apparently believes that everything is a text file and uses gvim to open them) and all nearly all icons have changed to what resembles a white sheet of paper, folded at the upper right corner, with an X in the middle.  When I try to run assogiate, I get a slew of errors:  "(assogiate:6961): Gtk-WARNING **: Error loading theme icon 'gtk-edit' for stock: Unrecognized image file format" ('gtk-edit' changes for apparently all the icons).  These are the icons on the toolbar.

The only icons that seem to have survived are those intrinsic to the program itself, not those set from outside.  I can still set the icon, and the new filename registers, but the new icon is not displayed.  Attempting to open a .svg file with Image Viewer tells me that it is an unrecognized file format.

I'm running Ubuntu 12.04, 3.2.0-61-generic kernel.  I do not use Unity - I prefer the Gnome classic desktop.

If there is any additional information needed to help troubleshoot, I would be happy to provide it.


Thanks!

---

### Post by bapoumba on 2014-05-17
May be here ? [http://ubuntugenius.wordpress.com/2012/06/18/ubuntu-fix-add-program-to-list-of-applications-in-open-with-when-right-clicking-files-in-nautilus/](http://ubuntugenius.wordpress.com/2012/06/18/ubuntu-fix-add-program-to-list-of-applications-in-open-with-when-right-clicking-files-in-nautilus/)
Example is with pdf but can be applied to other files.

---

