---
title: "Can rhythmbox be started with no window present"
date: 2013-08-21
forum: General Help
---

### Post by CaptainMark on 2013-08-21
In an attempt to write a script to play music automatically can rhythmbox be started with no window present via the terminal so it can then be played with the "rhythmbox-client --play" command?
Or is there any other way to get rhythmbox to play music (shuffle everything) without displaying a gui at all.

I've checked out the terminal helps but I'm not sure if it's possible, Banshee has this feature but banshee is buggy as heck and I don't like it anymore

EDIT: This plugin, doesn't work [https://launchpad.net/~fossfreedom/+archive/rhythmbox-plugins/+packages?field.name_filter=hide&field.status_filter=published&field.series_filter=raring](https://launchpad.net/~fossfreedom/+archive/rhythmbox-plugins/+packages?field.name_filter=hide&field.status_filter=published&field.series_filter=raring)
It pops up and dissappears after a second so is hardly ideal for a background script

---

### Post by bapoumba on 2013-08-21
Maybe something here : [http://ubuntuforums.org/showthread.php?t=1561293](http://ubuntuforums.org/showthread.php?t=1561293)

```

--no-start
              Do not start a new instance of rhythmbox
--no-present
              Don't present an existing rhythmbox window

```
But I do not see their --hide switch in the manual..

---

### Post by CaptainMark on 2013-08-21
Thanks but the --hide flag was removed from rhythmbox a few versions ago it seems, the other flags refer to other situations which don't really apply here, no-start doesn't seem to have any purpose that I can figure, and no-present only works if rhythmbox is already running making it useless as far as I can tell

---

### Post by bapoumba on 2013-08-22
Would you like I move your thread to Multimedia ?

---

