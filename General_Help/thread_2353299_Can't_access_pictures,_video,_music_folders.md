---
title: "Can't access pictures, video, music folders"
date: 2017-02-20
forum: General Help
---

### Post by boatcat on 2017-02-20
Hi I can't access the pictures, music and video folders in ubuntu gnome 16.10. Not sure why as I haven't made any changes. I've searched for the file types that I know were kept in those folders and can't find anything. Have I lost my data?

I get the message 'unable to find requested file, please check spelling and try again'

Let me know if you need any more info.

---

### Post by #&amp;thj^% on 2017-02-20
Please return the output of this from the terminal
```
cd && ls -l
```

---

### Post by boatcat on 2017-02-21
```
total 43616drwxr-xr-x  3 sharene sharene     4096 Jan 29 05:59 anki-2.0.41
drwxr-xr-x  3 sharene sharene     4096 Feb 20 07:36 Desktop
drwxrwxr-x  3 sharene sharene     4096 Feb 13 19:55 Documents
drwxr-xr-x 14 sharene sharene     4096 Feb 20 21:05 Downloads
-rw-r--r--  1 sharene sharene 39614064 Aug  7  2016 ghetto-skype_1.4.1_amd64.deb
-rw-r--r--  1 root    root           0 Jan  5 20:47 image1.dmg
-rw-r--r--  1 root    root     3071757 Jan  5 22:59 logfile1
-rw-r--r--  1 root    root     1936839 Jan  1 16:50 mapfile
drwxr-xr-x  2 sharene sharene     4096 Dec  5 15:38 Public
drwxr-xr-x  2 sharene sharene     4096 Dec 20 17:30 snap
drwxr-xr-x  2 sharene sharene     4096 Dec  5 15:38 Templates
drwxr-xr-x  5 sharene sharene     4096 Dec  7 20:29 testdisk-7.0
drwxrwxr-x  3 sharene sharene     4096 Feb 20 21:03 Videos
sharene@Sharene-Laptop:~$ ^C
```

it looks like my videos, pictures, musiv folders have disappeared. I was only able to 'recreate' my video folder by restoring a file that was previously there. The files that were in the folder aren't there but the directory now exists. I hope that makes sense?.

---

### Post by howefield on 2017-02-21
Do you know what you did to make the folders vanish ?

What's the output of the terminal command..

```
cat ~/.config/user-dirs.dirs
```

---

### Post by boatcat on 2017-02-26
Hi 

sorry about the delayed response, I've been away this week. To be honest I have no idea what has caused this. 

I upgraded to 16.10 from 16.04 maybe a week before this issue occurred. I tried to use Wine but couldn't get that to work and other than that haven't used my laptop for anything other than web browsing and watching videos.

Output 

```
 cat ~/.config/user-dirs.dirs# This file is written by xdg-user-dirs-update
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
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/Videos"
```

---

### Post by howefield on 2017-02-26
Try editing that file to include the Music and Pictures folders on the relevant line, ie, make it look like..

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

