---
title: "customize the nautilus folders under computer?"
date: 2012-12-11
forum: General Help
---

### Post by sdowney717 on 2012-12-11
I see you can add bookmarks. was also wondering if this unchangeable folder list could have custom new folder names added?

Like 

Pictures - Boat 
Pictures - house

type idea

---

### Post by Abhinav Kumar on 2012-12-11
Hi sdowney717,

You can bookmark them as told in the first thread. If you want to rename them just right click on the bookmarked folder name in the side pane and choose rename.
[http://ubuntuforums.org/showthread.php?t=1945720](http://ubuntuforums.org/showthread.php?t=1945720)

The second post in the following thread how to customise the home folder sidebar shortcuts.
[http://ubuntuforums.org/showthread.php?t=1986740](http://ubuntuforums.org/showthread.php?t=1986740)
:p

Regards,
Abhinav

---

### Post by sdowney717 on 2012-12-12
Thanks adding the line
XDG_BOAT_DIR="$HOME/boat"
does nothing

BUT adding the line

XDG_VIDEOS_DIR="$HOME/boat"

puts a link to boats and eliminates the link to Videos

How can I get both at same time?

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
XDG_BOAT_DIR="$HOME/boat"
```

---

