---
title: "[SOLVED] Folder icons appeared on desktop"
date: 2008-01-30
forum: General Help
---

### Post by brydong on 2008-01-30
I'm running gutsy on my laptop. I don't keep any icons on my desktop and prefer to keep it clean. I recently logged in to find icons on my desktop for all folders in my home dir. These are not just shortcut folders. If I create a new folder in my user dir, it appears on the desktop. If I delete a folder from the desktop, the folder and all it's contents are all deleted.

I'm not sure what I did to make this happen and therefore have no clue how to get rid of it.

thanks,
brydon

---

### Post by eggdeng on 2008-01-31
There is a bug report at [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4239758]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4239758")
From the last post:
> edit ~/.config/users.dirs.dirs and change the line XDG_DESKTOP_DIR="$HOME/" to XDG_DESKTOP_DIR="$HOME/Desktop

---

