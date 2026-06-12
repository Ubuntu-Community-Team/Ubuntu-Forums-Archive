---
title: "Alacarte"
date: 2007-02-13
forum: General Help
---

### Post by djaam on 2007-02-13
alacarte is working, but if i launch alacarte from console i see that:

(alacarte:17530): GnomeUI-CRITICAL **: gnome_icon_selection_clear: assertion `gis != NULL' failed

(alacarte:17530): GnomeUI-CRITICAL **: gnome_icon_selection_add_directory: assertion `gis != NULL' failed

(alacarte:17530): GnomeUI-CRITICAL **: gnome_icon_selection_show_icons: assertion `gis != NULL' failed

(alacarte:17530): GnomeUI-CRITICAL **: gnome_icon_selection_clear: assertion `gis != NULL' failed

(alacarte:17530): GnomeUI-CRITICAL **: gnome_icon_selection_add_directory: assertion `gis != NULL' failed

(alacarte:17530): GnomeUI-CRITICAL **: gnome_icon_selection_show_icons: assertion `gis != NULL' failed

(alacarte:17530): GnomeUI-CRITICAL **: gnome_icon_selection_clear: assertion `gis != NULL' failed

(alacarte:17530): GnomeUI-CRITICAL **: gnome_icon_selection_add_directory: assertion `gis != NULL' failed

(alacarte:17530): GnomeUI-CRITICAL **: gnome_icon_selection_show_icons: assertion `gis != NULL' failed


why? can i fix it?

---

### Post by ewankho on 2007-02-14
Maybe you need to run it from the console as : gksudo <program_name>

---

### Post by djaam on 2007-02-14
> **ewankho said:**
> Maybe you need to run it from the console as : gksudo <program_name>

gksudo alacarte


and its shows:

(alacarte:5580): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(alacarte:5580): GnomeUI-CRITICAL **: gnome_icon_selection_clear: assertion `gis != NULL' failed

(alacarte:5580): GnomeUI-CRITICAL **: gnome_icon_selection_add_directory: assertion `gis != NULL' failed

(alacarte:5580): GnomeUI-CRITICAL **: gnome_icon_selection_show_icons: assertion `gis != NULL' failed

---

### Post by Ramses de Norre on 2007-02-14
Does alacarte work despite of that error? If so, don't worry about it.

By the way: Alacarte is the worst piece of software in the standard-ubuntu install that I'm aware off, it has never properly worked here and I need to perform every modification like three times before the menu is actually changed..

---

### Post by djaam on 2007-02-14
> **Ramses de Norre said:**
> Does alacarte work despite of that error? If so, don't worry about it.

By the way: Alacarte is the worst piece of software in the standard-ubuntu install that I'm aware off, it has never properly worked here and I need to perform every modification like three times before the menu is actually changed..


ok, thanks

---

