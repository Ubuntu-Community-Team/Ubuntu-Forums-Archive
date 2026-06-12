---
title: "Removing Saveas/Open default path in side pane"
date: 2016-08-05
forum: General Help
---

### Post by c_xy on 2016-08-05
Hello,

We are currently using Ubuntu 14.04 server and xfce as the desktop environment

Whenever we want to open/save a file in gedit, emacs, etc. on the left side panel, the default directories appearing are items such as:


home
Documents
Music
Pictures
Videos

Our group uses none of the above folders and items. Our users access everything from a partition (e.g., "/example") and its subfolders. This is separate from the $HOME directories corresponding to a user. However, whenever we want to save and open a file, the items still appear in the side pane  and we have to sort through to find our /example location.

How does one remove these items permanently for all users of our server? Can we change it to a default directory (/example) to appear instead of the home directory subfolders?

Any input/suggestions would be appreciated.

Thank you.

c

---

### Post by Dennis N on 2016-08-06
You can set bookmarks (or shortcuts) to any folders in Thunar. These folders then appear in the side pane. Then, when you save a file in an application like gedit, those bookmarked folders appear again in the side pane of the save file dialog for selection. See attached image from my computer, where music, webpages, and Common-Files are folders I bookmarked on a separate data partition.

You apparently can remove the default Documents, Music, Pictures, Videos and Downloads as shortcuts by right-clicking on them and selecting "remove shortcut". I did not try this.

---

### Post by c_xy on 2016-08-06
Dennis, thanks for your response.

I see what you are saying, but I don't really want to create bookmarks.

I played around with the user-dirs.dirs. file in:

```
~/.config/
```

> 

XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_VIDEOS_DIR="$HOME/Videos"
XDG_PICTURES_DIR="$HOME/Pictures"




I tried commenting some of those out, and that remove some of them from the side pane. But still the home directory remains.

It seems that there are default bookmarks in the side pane, and it is all coming from the home directory.  We can't remove the home directory. Just want the file system link or a single partition in the side pane. 

I was hoping to find an easy fix, but I think this might be only my alternative:

[http://askubuntu.com/questions/325518/how-can-i-edit-nautilus-places-sidebar-and-unity-quicklist](http://askubuntu.com/questions/325518/how-can-i-edit-nautilus-places-sidebar-and-unity-quicklist)


What do you think?



c

---

### Post by Dennis N on 2016-08-06
Why not make a shortcut in the side pane to the mount point of the other file system? That would function the same as a file system link, would it not? Both would open the file system in a window. I don't use Nautilus any longer (not since 12.04), so not really familiar with what is currently possible with it on customizing the places section. Sorry I can't be of more help.

---

### Post by c_xy on 2016-08-06
Dennis,

Thanks again for the feedback.

The concern is not really creating a file system link. I mentioned that as an example is to what I would rather have in the side pane, instead of the home directory. The issue is not having the ability to remove the home directory from view in the side pane for the saveas/open side panes. In Thunar, we've done it by deselecting those home sub-folders in the Places section of the side pane. Haven't had much success with the Saveas/Open path for applications like gedit,emacs, etc. Certainly we can just ignore it and access the files/folders we would want. Since we aren't using the home directory and its sub-folders for file read/write purposes, they are just in the way and unnecessary.  We would prefer to see the current working directory only. That would make more sense instead of having several folders from the home directory in view that we do not use. I just don't know if it is possible to remove it through a few steps. It seems HOME as a default is embedded in the code, and altering the C code is the only solution I've come across online (at least for Nautilus).

Thanks again for your help.

c

---

