---
title: "archive content an ascii char can not mange on ubuntu"
date: 2007-02-28
forum: General Help
---

### Post by foxiness on 2007-02-28
i have an archive that content a backup of my c: drive ,this hold Document and setting and elso you will find file like this ???????????.gif this because when am work on it from windows with code windows-1256 not utf8 like here on Linux.

the tar will stop when it reach any file or folder that has name not English char,because this and file like this one 20GB of size hold my os ,application,doc etc.

the problem of file name it with ascii code ??????.something only you find it on this dir Documents and setting.

i mount the c: dirve like this

mount /dev/hda1 /mnt/win "vfat"

and the backup file on /mnt/backup3/ "ext3"

output: from tar xvpfz /mnt/backup3/backup.tgz

mnt/win/Documents and Settings/user/My Documents/My Videos/den/Thumbs.db
mnt/win/Documents and Settings/user/My Documents/My Videos/den/????? ???????/
tar: mnt/win/Documents and Settings/user/My Documents/My Videos/den/????? ???????: Cannot mkdir: Invalid argument
mnt/win/Documents and Settings/user/My Documents/My Videos/den/????? ???????/abraheam.wmv
tar: mnt/win/Documents and Settings/user/My Documents/My Videos/den/????? ???????/abraheam.wmv: Cannot open: No such file or directory
tar: Skipping to next header

note: last mint i use this 
[http://www.arabeyes.org/download/documents/howto/arabic-howto-en/essentials.html#mountwindowspartition](http://www.arabeyes.org/download/documents/howto/arabic-howto-en/essentials.html#mountwindowspartition)
 
# mount -t auto /dev/hda1 /mnt/win/ -oiocharset=utf8

---

