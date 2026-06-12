---
title: "Changing the shortcut redirecting"
date: 2017-02-14
forum: General Help
---

### Post by Mantu2 on 2017-02-14
Hi!

I've just installed Ubuntu 16.04. and I made it to my new laptop (dual boot with windows 10). Yey - it works as should after a small fight. This new computer is having SSD and regular HD for file storage. Hard drive is one terabyte. Before I move all my files to this new computer, I am wondering am I able to make any configuration on File Manager. My plan is to use SSD only for programs, Windows and Ubuntu and all files are put into the HD. At the moment the "file tree" (Home, desktop, documents, pictures, downloads etc.) are redirecting to SSD where Ubuntu is installed. I would like to use these shortcuts for storage files on HD; Is there any method to change them so that when clicking them, it goes to my 1 TB HD?

Thanks for help!

---

### Post by vanadium on 2017-02-14
Replace the Documents, Music, etc, folders by symbolic links to these folders on the HD. Such symbolic links act exactly as folders. Another way, which requires editing /etc/fstab, is to "mount bind" these folders to folders on your HD.

1) Move these folders to your HD
2) Create symbolic links where the folders where. With the file manager: drag the folders while you press Ctrl+Shift to the original folder (your home folder). This will cause symbolic links to be created. Alternative method: select folders, right-click, select "Create link". Move the created links to your home folder and rename them (i.e.e remove the part "Link to " in the folder name).

---

### Post by Bucky Ball on 2017-02-14
Ctl+shft copies the folder, no symlink. Perhaps that's a desktop environment idiosyncrasy as I'm on xfce4 and Thunar. The right-click 'Create link' method works fine, though. ;)

Creating them in a terminal is pretty easy, too, and the syntax is this:

```
ln -s 'location to link to' 'name of symlink'
```

For instance:

```
ln -s /data/Documents /home/user/Documents
```

... would create a link called 'Documents' in your /home/user folder to the *actual* 'Documents' folder on the /data partition .

See [this page for more details]("http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html") if required.

---

### Post by Mantu2 on 2017-02-15
Thanks! 

I found out that the driver was set to root user so I didn't have the permissions for it. Fixed that and then used vanadium's hint of making a file and renaming it. Everything went as should. Only thing is the desktop. Changing that didn't work like that. However, I think I'll leave it as it is because most of the time it holds the files I'm using the most (so need to be on fast ssd).

---

### Post by vanadium on 2017-02-17
Check your file .config/user-dirs.dirs: Make sure the folders mentioned there point to your symlinks - if you graphically deleted/moved the folders and created the symlinks, these references probably will be changed. If needed, edit the file to (again) look like:
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

```

---

