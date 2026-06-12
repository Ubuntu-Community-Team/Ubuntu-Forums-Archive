---
title: "Fixing Glib errors in Audacity after 18.04 to 20.04 upgrade"
date: 2020-10-11
forum: General Help
---

### Post by AR_Kozz on 2020-10-11
Parts of Audacity widget are now blackened in, timeline freezes, and other issues. When run as root it runs fine, but no access to installed plugins. Only observed difference when run in terminal is the first few lines:

> $ audacity

(Audacity:18952): GLib-GObject-WARNING **: 21:41:51.552: cannot register existing type 'GdkDisplayManager'
(Audacity:18952): GLib-CRITICAL **: 21:41:51.552: g_once_init_leave: assertion 'result != 0' failed
(Audacity:18952): GLib-GObject-CRITICAL **: 21:41:51.552: g_object_new_with_properties: assertion 'G_TYPE_IS_OBJECT (object_type)' failed
(Audacity:18952): Gtk-WARNING **: 21:41:51.560: gtk_disable_setlocale() must be called before gtk_init()

vs 

> $ sudo audacity
[sudo] password for ***: 
(Audacity:19068): Gtk-WARNING **: 21:42:49.675: gtk_disable_setlocale() must be called before gtk_init()

So, my guess not knowing much about Gtk or glib is some user config of mine is screwing up glib under 20.04. If so, where should I find it?

---

### Post by &amp;KyT$0P# on 2020-10-11
In Settings > Language Support, what do you have set for "Keyboard input method system"?  I had to set this to [FONT=Courier New]none[/FONT] to get Audacity working in Xubuntu 20.04.

(I don't know where the "Keyboard input method system" setting is in other DEs.)

---

### Post by AR_Kozz on 2020-10-12
Thanks, but I'm on regular Ubuntu 20.04 and no such setting. I tried switching to other languages but it had no effect.

The fact the errors don't happen in root point to an old configuration in /home (I think) but so far I can't find where that config is.

Where do we go to rant about upgrade issues getting worse and worse the bigger Ubuntu gets?

---

### Post by tea for one on 2020-10-12
> **AR_Kozz said:**
> 
The fact the errors don't happen in root point to an old configuration in /home (I think) but so far I can't find where that config is.

/home/username/.audacity-data/audacity.config

My version on Ubuntu 20.04.1 is Audacity 2.3.3 (from a fresh install)

I do not think it's a good idea to open Audacity as root because the data and config is in your user directory.

---

### Post by &amp;KyT$0P# on 2020-10-12
> **AR_Kozz said:**
> Thanks, but I'm on regular Ubuntu 20.04 and 

Ok, downloaded Ubuntu 20.04.1 live CD and found it: Settings > Region & Language > Manage Installed Languages

---

### Post by AR_Kozz on 2020-10-13
> **tea for one said:**
> /home/username/.audacity-data/audacity.config

My version on Ubuntu 20.04.1 is Audacity 2.3.3 (from a fresh install)

I do not think it's a good idea to open Audacity as root because the data and config is in your user directory.

Thanks, yes I know about that config file, however it doesn't seem to call or affect anything in glib or gtk. The errors I'm getting seem to happen before the app gets around to checking user config.

Therefore what I think I'm looking for is some obsoleted config of gtk or glib itself. /home/.config has folders for gtk2.0, 3.0 and 4.0, with nothing of substance in any of them. 

I have to run audacity as root or it's unusable

---

