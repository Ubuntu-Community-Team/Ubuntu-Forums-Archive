---
title: "Script Installed Themes: Yaru-Colors-master terminal Gtk WARNING for some colors"
date: 2020-06-24
forum: General Help
---

### Post by maddenjmf on 2020-06-24
I installed **Yaru-Colors-master **successfully and the Themes, Applications setting works with all installed color variants of Yaru. However when switching to standard and dark variants only (error does not occur with light variants), I get the following message display in terminal when switching to the problem themes:

(gnome-tweaks:3749): Gtk-WARNING **: 01:32:00.488: Theme parsing error: gtk.css:5449:34: Invalid name of pseudo-class

I have checked the theme folders for inconsistencies but I can't spot any.  Most of them have a gnome-shell folder, 3 gtk version folders, a unity folder and an index.theme.

1) I am new to Linux and am trying to identy what is causing the message in the open terminal when gnome-tweaks is run from it and left open? Although the changes are functioning, I'm trying to understand how the system works.
2) How is gnome-shell folder and contents for themes different to that of gtk folder? My **Appearance: Shell** setting through gnome tweaks tool seems to have no effect on anything even though the list is populated with the themes available from Yaru-Colors-master.

The error displays itself each time I switch to a standard color theme or a dark color theme, but does not present itself when I select any light theme color variant.

If I try to close the terminal after the message appears, it says a process is running and that closing terminal will kill it. I close the terminal and it forces gnome-tweaks to close with it.

Thanks in advance for and help and better understanding you can give me of why this is occuring.

**gnome version:**
3.36.2
[B]
gnome-tweaks --version[/B]
3.34.0
[B]
Ubuntu 20.04 LTS Desktop

EDIT* Added info in case it is relevant:
[/B]I created directories for themes in **home/user/.themes** and icons in [B]home/user/.icons
[/B]The per-existing themes I noticed are in [B]usr/share/themes

[/B]

---

### Post by deadflowr on 2020-06-24
The error is in the gtk.css file. My guess is line 5449.
File most likely found in the gtk-3.0 folder. Maybe in gtk-3.20 if existing.

Other than that how'd you install the theme, and from where?

---

### Post by maddenjmf on 2020-06-25
There are gtk.css in more than one folder, so I was wondering how to read the numerical code in the error message to identify the exact file (if possible).

**edit: for example, there is one gtk.css in the 3.00 folder and the 3.20 folder with exact same name, for one individual theme.

It was a .zip download from gnome-look.org and I downloaded the .zip to download.

I then ran the install.sh contained within the unzipped folder, and as part of the script it asked me for a path to store the themes and icons.

---

### Post by maddenjmf on 2020-07-03
No other information regarding identifying my exact problem here and understanding the error code?

---

