---
title: "XDG user_dirs.dirs not working"
date: 2014-07-27
forum: General Help
---

### Post by Frozen Forest on 2014-07-27
Installed a system where all the Picture, Download etc folders are located on a seperate partition that is encrypted using Encfs which get automounted at login. The issue is that on every single login is all variables in user_dirs.dirs reseted to $HOME, which force me to copy a backup for the correct user_dirs.dirs and then run nautilus -q which resolves the issue. What I would which is a solution that avoided this extra hassel, I tried to setting the variables XDG_CONFIG_{HOME,DIRS} to the .config folder but neither is working. Can this problem be resolved?

---

### Post by ajgreeny on 2014-07-27
I know nothing about encryption and the effect that might have on your problem, but normally the easiest way to deal with this problem would be to make soft links from the Documents, Pictures etc etc folders on the separate partition, back to your /home.

To do this first remove all the problem named folders from your /home, then in terminal run the commands one by one for each folder
```
ln -s /media/path/to/Documents/ Documents
``` If you don't remove the folders in your home first each new folder will be replicated within its own named folder so you will have eg, /home/username/Documents/Documents, not what you want I assume.

You can do this with nautilus, if it is still the same as it used to be, in one go by first removing the folders from home, as before, then dragging those folders from the separate partition using the middle button of your mouse and choose link from the dialog box.

Whichever way you choose, the folders will appear in your home but now as links, leaving all your files still on the separate partition, but they weill also appear in the home folders in the normal way.

---

### Post by Frozen Forest on 2014-07-27
I actually use sym links for the folders on the other partition, but it still do not work. I guessing that an issue might be that the links are dead when xdg run since the partition has to be decrypted before the folders can be accessed.
My config file look like this
[PHP]
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Template"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Document"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Video"
[/PHP]

On login does it look like this
[PHP]
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME"
XDG_DOWNLOAD_DIR="$HOME"
XDG_TEMPLATES_DIR="$HOME"
XDG_PUBLICSHARE_DIR="$HOME"
XDG_DOCUMENTS_DIR="$HOME"
XDG_MUSIC_DIR="$HOME"
XDG_PICTURES_DIR="$HOME"
XDG_VIDEOS_DIR="$HOME"
[/PHP]

---

### Post by mc4man on 2014-07-27
Maybe try opening this file in a root text editor & set to - 
enabled=False

/etc/xdg/user-dirs.conf

---

### Post by ajgreeny on 2014-07-27
I did wonder about the effect of encryption of the data partition on your required setup, but as I say I know nothing about using encrypted partitions.

Presumably the partition is mounted, or the system tries to mount it too soon and before the decryption has happened.  Can you perhaps delay the attempt to mount the partition in some way, or else decrypt the partition at an earlier stage.

How do you automount the partition; it can not be using fstab as the partition is still encrypted at that point so will not be available.

---

### Post by Frozen Forest on 2014-08-01
> **mc4man said:**
> Maybe try opening this file in a root text editor & set to - 
enabled=False

/etc/xdg/user-dirs.conf

This did resolve the issue, sometimes Nautilus gives an error, but it's easily resolved by restarting it.

> **ajgreeny said:**
> I did wonder about the effect of encryption of the data partition on your required setup, but as I say I know nothing about using encrypted partitions.

Presumably the partition is mounted, or the system tries to mount it too soon and before the decryption has happened.  Can you perhaps delay the attempt to mount the partition in some way, or else decrypt the partition at an earlier stage.

How do you automount the partition; it can not be using fstab as the partition is still encrypted at that point so will not be available.

Improper wording, it's only a folder on the partion that is encrypted on the partition. It's the only folder on that partition so therfor the confusion

---

