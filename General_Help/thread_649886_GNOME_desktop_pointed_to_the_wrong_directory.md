---
title: "GNOME desktop pointed to the wrong directory"
date: 2007-12-25
forum: General Help
---

### Post by Ink-Jet on 2007-12-25
I accidentally deleted my ~/Desktop directory a few days ago, but then recovered it from my ~/.Trash directory. I didn't think anything had happened.

However, after downloading a few files today, to my Desktop, I realized they weren't showing up on my Desktop. I checked that they had been download to ~/Desktop, and they were. Somehow my Desktop is pointed towards ~/.Trash/Desktop, because any files moved there are displayed on the Desktop.
Also, the Desktop entry in Places is set to ~/.Trash/Desktop, and creates the folder if I#ve deleted it.

How can I set GNOME to display ~/Desktop as my actual desktop, instead of ~/.Trash/Desktop ?

---

### Post by zvacet on 2007-12-25
Delete that Desktop from trash and make new one 

```
mkdir Desktop
```

---

### Post by Ink-Jet on 2007-12-25
I did do that, and I still have my old one, but GNOME isn't using it as my actual desktop - when I deleted it and re-started, it seemed to set my /home directory as my desktop, even though the entry in the gconf-editor says not to.

---

### Post by zvacet on 2007-12-26
> I did do that, and I still have my old one

Go to the nautilus>home directory>view>show hidden files>.Trash and delete your Desktop from there.If you didn´t made new one you will be without Desktop wich is not bed.When you restart comp you will see in the bottom left corner **sessions** option and choose safe gnome(or something similar,I don´t use english version) and terminal will pop up.


```
mkdir Desktop
```

---

### Post by boltronics on 2007-12-29
I had a similar problem. Gutsy creates a *lot* of directories in ~ that I don't really appreciate. The first thing I did is

```

 $ rmdir *

```

and forgot about the Desktop directory. After setting up my desktop the way I like it, I noticed the next time I logged in that my home directory was used as the Desktop - yuck!

I started poking around in gconf-editor (as nautilus didn't seem to have any other means of configuring this via the GUI) and found "desktop_is_home_dir" under /app/nautilus/preferences. Oddly enough, it was unticked. I ticked it, logged out and in again, and the same problem occurred. I unticked it again, logged out and in again, and the problem still didn't resolve itself.

Having no idea where the *real* setting was stored (other than the fact that it must have been in my home folder somewhere), I started deleting each hidden directory one by one, logging out and in again to see which directory needed to be deleted to solve the problem. After most of my customizations had been erased, I hit the jackpot by deleting '~/.config'.

After it was re-created (via a fresh log-in), I noticed ~/.config/user-dirs.dirs contains the contents:

```

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

```

My guess is that the XDG_DESKTOP_DIR and XDG_DOWNLOAD_DIR directories were somehow changed. I hope this information saves someone else from wasting an hour trying to track down such a simple setting.

---

### Post by dedmonds on 2008-04-01
Thank you, boltronics. I ran into the same problem today in which the icons shown on the desktop were from my home directory rather than the ~/Desktop folder. Editing the ~/.config/user-dirs.dirs file and restarting X corrected the problem.

---

