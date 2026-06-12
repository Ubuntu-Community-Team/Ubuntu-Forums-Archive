---
title: "gconftool, gconf-editor, and dconf-editor"
date: 2013-05-19
forum: General Help
---

### Post by Iggy64 on 2013-05-19
As I understand it, there is a Gconf Reporsitory that stores key-value pairs defining a user's preferences for various environment settings, such as defaultmusicsink.  

One tool for editing the values is gconftool, a CLI command.
Another approach is to use gconf-editor, which is a GUI version.
The path to the musicaudiosink is /system/gstreamer/0.10/default/musicaudiosink

It appears that gconf-editor has recently been replaced by dconf-editor.
However, there does not seem to be a dconftool replacement for gconftool.

So that leaves me with the choice between gconftool (CLI) and dconf-editor (GUI).

I see, though, that the path to the musicaudiosink in dconf-editor is different from that in gconf-editor.
Now it is  /Desktop/gstreamer/0.10/default-elements/musicaudiosink

I am confused.

Do dconf-editor and gconftool write to the same configuration repository?
If so, which path to the musicaudiosink is correct?  Is the path the same in dconf-editor and gconftool?

I am running Bodhi Linux (e17) on Ubuntu 12.04.

---

### Post by Frogs Hair on 2013-05-19
I believe the  dconf-editor is geared towards the Unity desktop because that is when I first installed the tool  . The dconf-editor gui is in the Ubuntu repository, but I can't speak for Bodhi.

---

### Post by ajgreeny on 2013-05-19
Bodhi uses Ubuntu repos so it will certainly be available in the repos you have access to in Bodhi.  You need the package dconf-tools.

I do agree, however, that it is now rather confusing when you want to change something using the GUI, and it is often necessary to search through both gconf-editor and dconf-editor

---

### Post by CatKiller on 2013-05-19
DConf is a replacement for GConf. They aren't the same thing.

Tools will follow, the same way they always do when something gets changed.

---

### Post by diesch on 2013-05-19
In Gnome3 *gconf* has been replaced by GSettings with *dconf* as its default backend. They don't use the same database.

You can use *gsettings* to access GSettings from CLI, or *dconf* to directly access to the dconf database. Usually you want to use *gsettings*.

---

### Post by Iggy64 on 2013-05-19
Thanks to all for the kind replies.  This afternoon, I have been researching this as best I could.  It looks like most of you already knew what it took me so long to research:

GConf has been largely replaced by GSettings.
gconftool and gconf-editor have been replaced by gsettings and dconf-editor.
The paths and the element names are different in GSettings than they were in GConf.

What remains confusing is that both databases remain in my 12.04 distro, leaving me wonder which database is actually controlling my configuration.  I'll be saving changes to keys in each, in an attempt to see which one is actually active.  I'm wondering if some apps are configured in one, and others in the other.  Right now, most important to me is which one is controlling GStreamer.  If I figure it out, I'll check back in.

Thanks again for the helpful comments.

---

### Post by stinkeye on 2013-05-20
> **Iggy64 said:**
> Thanks to all for the kind replies.  This afternoon, I have been researching this as best I could.  It looks like most of you already knew what it took me so long to research:

GConf has been largely replaced by GSettings.
gconftool and gconf-editor have been replaced by gsettings and dconf-editor.
The paths and the element names are different in GSettings than they were in GConf.

What remains confusing is that both databases remain in my 12.04 distro, leaving me wonder which database is actually controlling my configuration.  I'll be saving changes to keys in each, in an attempt to see which one is actually active.  I'm wondering if some apps are configured in one, and others in the other.  Right now, most important to me is which one is controlling GStreamer.  If I figure it out, I'll check back in.

Thanks again for the helpful comments.

May have to search both  gconf-editor and dconf-editor for the setting you want.
Both use ctrl+F for search.

Bit strange here.
gstreamer here, shows by drilling down to **desktop > gstreamer-0.10 > default-elements**
but the actual schema path is **org.freedesktop.gstreamer-0.10.default-elements** as shown in the bottom pane.
[ATTACH=CONFIG]242801[/ATTACH]

If you want to make a script , gsettings is fairly easy to use.

example changing the gstreamer audio source.
Get current..
```
gsettings **get** org.freedesktop.gstreamer-0.10.default-elements audiosrc
```

Change to pulse....
```
gsettings **set** org.freedesktop.gstreamer-0.10.default-elements audiosrc pulsesrc
```

Reset to default (alsasrc)...
```
gsettings **reset** org.freedesktop.gstreamer-0.10.default-elements audiosrc
```

---

