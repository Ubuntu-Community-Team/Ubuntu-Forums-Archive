---
title: "How to Disable Auto-mounting of External Media in 8.04 Hardy Heron"
date: 2008-04-28
forum: General Help
---

### Post by xixsixxix on 2008-04-28
I've been seeing this question a lot.

Users upgrading from 7.10 Gutsy to 8.04 Hardy are having trouble disabling auto-mounting. In Gutsy users could go to *System > Preferences > Removable Drives and Media* to disable auto-mounting, but the tab that managed external storage media is no longer there in Hardy.

So here's a quick HowTo to disable auto-mounting of CDs, USB thumb drives, etc.

Auto-mounting is handled by the desktop environment, Gnome in this case, and more specifically Nautilus, so use Gnome's configuration editor (gconf-editor):

Either hit Alt+F2 to bring up a run box or simply open a terminal and type:
```
gconf-editor
```
The configuration editor will come up. Use the left-side interface to navigate to **apps > nautilus > preferences** and in the right pane _uncheck_ **media_automount**. That's it :)

For those that would like to accomplish this programatically, as I posted in **[Disable automounting of USB drives with a command?]("http://ubuntuforums.org/showthread.php?t=738414")**, you can accomplish the same task with gconftool-2:
```
(disable)
$ gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount false

(enable)
$ gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount true
```

Also, as Xyhthyx noted in the aforementioned thread, in Gutsy (and for general legacy purposes) you may want to use gconftool-2 on */desktop/gnome/volume_manager/automount_drives* as well as */desktop/gnome/volume_manager/automount_media*.

Hope that helps a few googlers ;)

---

### Post by fhmanas on 2008-04-29
Would you know setting as well that will start banshee instead of Rhythmbox when you attach ipod.  This used to be in Removable Drives and Media in Gutsy.  Changing in Nautilus and PReferred Applications does not work.

---

### Post by xixsixxix on 2008-04-29
> **fhmanas said:**
> Would you know setting as well that will start banshee instead of Rhythmbox when you attach ipod.  This used to be in Removable Drives and Media in Gutsy.  Changing in Nautilus and PReferred Applications does not work.

A quick warning - I've heard some people have had trouble getting Banshee to recognize their ipods under Hardy. That being said...

Since I haven't got my ipod here to check I'll just venture a couple guesses. The fist place I'd try, for the sake of simplicity, would be in Nautilus' (open a file explorer) **File > Preferences > Media** tab, which has pretty much replaced the old *Storage* and *Media* tabs from *Removable Drives and Media*. But odds are the media preferences in there would only apply when you loaded the ipod in data mode.

Assuming nothing there helps... while it's not a tab in *Removable Drives and Media* anymore, you can still find some of those older media device settings using **gconf-editor** under */desktop/gnome/volume_manager*. Check there to see if you've still got the **autoipod** and **autoipod_command** keys. Who knows, they may still work ;) Also, if you go under *prompts*, which is a subdir of *volume_manager*, there's a separate ipod_photo option.

---

### Post by Skerit on 2008-05-01
What were they thinking? Removing this option in the "Removable media and drives" app and moving it to nautilus? We have so many settings to control, they really should be kept in one place and not be spread out even more.

Btw, nautilus AND the Removable-app both have a setting for what to do when you plug in a photo-device. I don't think these 2 settings are in any way linked, hmm?

---

### Post by 666f6f on 2009-05-01
I too agree that this is not very user friendly..

---

