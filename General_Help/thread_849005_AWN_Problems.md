---
title: "AWN Problems"
date: 2008-07-04
forum: General Help
---

### Post by Pligon on 2008-07-04
Avant Window Navigator used to work fine... but when I installed updates today from a few days ago, it suddenly stopped working... Everything seems to have froze and I can't click on any of the icons... when I run AWN in a terminal, I get this:

```


Screen is composited.
LOADED : /usr/share/applications/firefox.desktop
LOADED : /usr/share/applications/wesnoth.desktop
LOADED : /usr/share/applications/zsnes.desktop
LOADED : /usr/share/applications/gsnes9x.desktop
LOADED : /usr/share/applications/ooo-writer.desktop
LOADED : /usr/share/applications/ooo-calc.desktop
LOADED : /usr/share/applications/ooo-impress.desktop
LOADED : /home/stephen/Desktop/kaffeine.desktop
LOADED : /usr/share/applications/gnome-terminal.desktop
LOADED : /usr/share/applications/wine-notepad.desktop
LOADED : /usr/share/applications/rhythmbox.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop

(avant-window-navigator:6829): GLib-GObject-WARNING **: cannot register existing type `AwnTitle'

(avant-window-navigator:6829): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

** (avant-window-navigator:6829): CRITICAL **: awn_title_show: assertion `AWN_IS_TITLE (title)' failed


```

Does anyone have any suggestions? I appreciate the help...

---

### Post by Timemaster on 2008-07-04
you may want to try reinstalling AWN. I can't guarente it will work but its worth a shot.

---

### Post by g-robbie on 2008-07-04
Anyone has a solution to this yet? I've got the same problem - its completely frozen - nothing in the logs to suggest the problem..tried uninstalling and reinstalling but it didn't work

---

### Post by orbital on 2008-07-04
I have the exact same problem. Any fix for this?

---

### Post by csc2ya on 2008-07-04
Exact same problem after installing updates about an hour ago:

administrator@Laptop:~$ avant-window-navigator
Screen is composited.
APPLET : /usr/lib/awn/applets/taskman.desktop

(avant-window-navigator:8499): GLib-GObject-WARNING **: cannot register existing type `AwnTitle'

(avant-window-navigator:8499): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

** (avant-window-navigator:8499): CRITICAL **: awn_title_show: assertion `AWN_IS_TITLE (title)' failed

---

### Post by Cantodea on 2008-07-04
Same problem here,

I think there will be an update soon

---

### Post by Golem XIV on 2008-07-04
Me 3, updated this morning and AWN started locking up.

Uninstalled it, googled a bit, went to the [Awn Wiki installation page]("https://launchpad.net/~awn-testing/+archive"), set up the repository and installed the development version. Now it works fine again.

---

### Post by gilir on 2008-07-04
The update of avant-window-navigator in hardy-proposed is broken. Please don't install it.

To fix :

- Downgrade to 0.2.1-0ubuntu2 : in Synaptic, clic on avant-window-navigator package, do Ctrl + E and select the 0.2.1-0ubuntu2. Do the same for libawn0.

- Installing development version : [http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

---

### Post by orbital on 2008-07-04
> **gilir said:**
> The update of avant-window-navigator in hardy-proposed is broken. Please don't install it.

To fix :

- Downgrade to 0.2.1-0ubuntu2 : in Synaptic, clic on avant-window-navigator package, do Ctrl + E and select the 0.2.1-0ubuntu2. Do the same for libawn0.

- Installing development version : [http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

Thanks, this solved the problem!

---

### Post by Pligon on 2008-07-04
That worked... Thanks for the help.

---

### Post by netuntu on 2008-07-07
Downgrade works perfectly, i hope avant team fix the problem soon as possible!  

Thanks for help.

---

### Post by charlesopondo on 2008-07-07
Same problem here after a recent upgrade. Reinstall doesn't work but the downgrade nails it perfectly. Problem is having to ignore Adept Notifier. Thanks a lot to the great minds of this forum :)

---

### Post by moonbeam on 2008-07-07
> **netuntu said:**
> Downgrade works perfectly, i hope avant team fix the problem soon as possible!  


Well... the awn team doesn't create those particular packages (in proposed)  They are more or less out of our control... If we could control them it's probably be fair to say that they would have been tested/removed several days ago :-)

Info on the awn-testing ppa packages that the awn dev team do control can be found here:  [http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

---

### Post by durfff on 2008-07-07
Yeah - solved my problem and made me discover the lock version functionality, thanks much everyone!

---

### Post by hellomoto on 2008-07-08
i also have the same problem:

AWN has been working great for the past 2 months but i downloaded the latest updates a few days ago and its mucked it up. 

anyone got a fix?

---

### Post by rroberto on 2008-07-12
This forum is really great!

Fixed my AWN after downgrading to the older version.

So, until when can you ignore the update Manager for the AWN upgrade? How do you know when the bug-free version is already available on the update?

Thanks

---

