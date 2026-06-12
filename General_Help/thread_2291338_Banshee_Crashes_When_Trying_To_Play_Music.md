---
title: "Banshee Crashes When Trying To Play Music"
date: 2015-08-19
forum: General Help
---

### Post by wpwend42 on 2015-08-19
I have been using Banshee as my primary music player for nearly 5 years. In the past 48 hours, any track I try to play plays for about 5 seconds and then the app shuts down. What could be causing this?

---

### Post by ceejay13 on 2015-08-19
Don't know if this is related, music (local flac files) is breaking up when using Amarok (5+ years), but again only in the last 48 hours.  Just loaded Clementine and get the same thing.

---

### Post by wpwend42 on 2015-08-19
music files work in VLC for me though. Huh.

---

### Post by ceejay13 on 2015-08-19
Tried VLC here and the music is still broken :(

Yesterdays update caused a Network error/crash after the restart.  Did another restart as suggested in the error message and all was/seemed OK.  Didn't try the music until today.

I'll try to read back through the logs to see what happened.

---

### Post by wpwend42 on 2015-08-20
You know, I had a network crash the other day too...

---

### Post by tgalati4 on 2015-08-20
Try running *banshee* with the debug option and watch what happens.

Open a terminal.

```
banshee --debug
```

---

### Post by wpwend42 on 2015-08-20
Okay it ran fine when I did that, but then crashed again after I closed the terminal. The end of the terminal output gave some errors:

[I](Banshee:19564): GLib-CRITICAL **: Source ID 111 was not found when attempting to remove it

(Banshee:19564): GLib-GObject-WARNING **: attempting to add an interface (AtkComponent) to class (__gtksharp_47_Hyena_Gui_BaseWidgetAccessible) after class_init

(Banshee:19564): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_48_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_TrackInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:19564): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_48_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_TrackInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:19564): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_54_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_Database_QueryFilterInfo+601+5b+5bSystem_String+2c+20mscorlib+2c+20Version+3d4_0_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3db77a5c561934e089+5d+5d+2c+20Banshee_Services+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:19564): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_54_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_Database_QueryFilterInfo+601+5b+5bSystem_String+2c+20mscorlib+2c+20Version+3d4_0_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3db77a5c561934e089+5d+5d+2c+20Banshee_Services+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:19564): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_60_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_ArtistInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:19564): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_60_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_ArtistInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:19564): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_66_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_YearInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:19564): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_66_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_YearInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:19564): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_72_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_AlbumInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:19564): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_72_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_AlbumInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init
[/I]

and then...

[I](Banshee:19564): GLib-CRITICAL **: Source ID 938 was not found when attempting to remove it

(Banshee:19564): GLib-CRITICAL **: Source ID 702 was not found when attempting to remove it

(Banshee:19564): GLib-CRITICAL **: Source ID 936 was not found when attempting to remove it

(Banshee:19564): GLib-CRITICAL **: Source ID 769 was not found when attempting to remove it

(Banshee:19564): GLib-CRITICAL **: Source ID 700 was not found when attempting to remove it

(Banshee:19564): GLib-CRITICAL **: Source ID 937 was not found when attempting to remove it

(Banshee:19564): GLib-CRITICAL **: Source ID 935 was not found when attempting to remove it

(Banshee:19564): GLib-CRITICAL **: Source ID 703 was not found when attempting to remove it

(Banshee:19564): GLib-CRITICAL **: Source ID 829 was not found when attempting to remove it

(Banshee:19564): GLib-CRITICAL **: Source ID 928 was not found when attempting to remove it

(Banshee:19564): GLib-CRITICAL **: Source ID 934 was not found when attempting to remove it
[/I]

---

### Post by tgalati4 on 2015-08-20
Did you add any Banshee plug-ins?  Try turning off all plug-ins and then run in debug mode again.

---

### Post by wpwend42 on 2015-08-22
I thought I only had a few turned on (like play queue), but a TON of them were turned on. I turned them all off except for plugins I actually use and now Banshee seems to be running fine.

---

### Post by ceejay13 on 2015-08-22
As an added extra, I used bash to reload Kernel 3.13.0-61 and then reloaded 3.13.0.62 generic.  All OK now on both Clementine and Amarok.

How strange we should both get the network error and now all OK!  

Thanks tgalati4 for your input!

---

