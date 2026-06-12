---
title: "How does Ubuntu create user default directories?"
date: 2013-06-02
forum: General Help
---

### Post by H9D1uAehOP on 2013-06-02
I'm asking this because I just created a project called Ubuntu MATE. Unofficial Ubuntu edition featuring MATE desktop environment, [click here to know more]("https://sourceforge.net/projects/ubuntumate/"). And one of two problems is that after installation, instead of creating the default "Documents, Pictures, Downloads..." directories, it just have "Desktop" folder.
I have two ideas:
1. Create manually (it isn't a great idea, because even if the person choose another language, the home folders will stay with the same english name)
2. Copy the /etc/skel or /etc/root content from Ubuntu ISO to my ISO (doesn't work).
How can I do that? And how do I do the same thing with the icon "Install Ubuntu..."?

---

### Post by ajgreeny on 2013-06-02
In my Xubuntu 12.04, and I think in my previous Ubuntu versions, there is a file in ~/.config called user-dirs.dirs which the system uses to make those default directories.  It's a plain text file containing, in my system
> # This file is written by xdg-user-dirs-update
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


---

