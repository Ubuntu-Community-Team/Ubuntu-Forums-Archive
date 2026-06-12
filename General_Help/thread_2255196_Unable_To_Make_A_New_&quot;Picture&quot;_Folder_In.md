---
title: "Unable To Make A New &quot;Picture&quot; Folder In Sidebar"
date: 2014-12-02
forum: General Help
---

### Post by jooge on 2014-12-02
So I accidentally deleted my Picture folder from my Home folder and naturally it was also removed from the sidebar in Nautilus.


[[IMG]http://i.imgbox.com/s6hflebQ.png[/IMG]]("http://imgbox.com/s6hflebQ")


Is there a way to create a new one that will appear where the old one was?

---

### Post by deadflowr on 2014-12-02
Have you tried making a new folder called Pictures?
note the s at the end.

---

### Post by jooge on 2014-12-03
Yes I have one made there and it doe not appear. It's missing the little design on it. It's just a regular folder.

---

### Post by deadflowr on 2014-12-03
How'd you delete it?
Is it in the trash folder still?
If so, highlight it, and click restore selected items.

Or,
try to quick quit and restart of nautilus.
```
nautilus -q
```
and then open the Home Folder again.
Nautilus is always running so you might need to quit/restart it for changes to take effect.

---

### Post by jooge on 2014-12-03
Naw, that didn't work either.

---

### Post by carl4926 on 2014-12-03
Perhaps
Edit
user-dirs.dirs
in .config

```
# This file is written by xdg-user-dirs-update# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

---

### Post by deadflowr on 2014-12-03
You are renaming it Pictures, and not Picture, right? So we're clear.
Capital P, too. Not pictures, but Pictures.

Also:
 > [COLOR=#000000]Naw, that didn't work either.[/COLOR]

Which didn't work?
And it doesn't answer how you deleted the folder...

---

### Post by jooge on 2014-12-03
> **carl4926 said:**
> Perhaps
Edit
user-dirs.dirs
in .config

```
# This file is written by xdg-user-dirs-update# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

That bookmarked it. 


[[IMG]http://i.imgbox.com/KNvy0UoL.png[/IMG]]("http://imgbox.com/KNvy0UoL")


That works for me. Thanks

---

