---
title: "Mounting FTP with write access"
date: 2007-05-12
forum: General Help
---

### Post by shiznatix on 2007-05-12
Ok what I used to do in windows was run editplus and use its Remote FTP abilities to open and edit the files on the server.

Now in Ubuntu, I figured I could just mount the FTP with the 'Connect to server' thing but when I open the files in gedit I am unable to save it because they are 'write only'. How can I mount all of the FTP's as read write so I can actually edit them?

---

### Post by Cybolic on 2007-05-22
You can open **gconf-editor** (press **Alt+F2** and write **gconf-editor**), go to
*apps/gedit-2/preferences/editor/save/writable-vfs-schemes*
and add **ftp** (and **ssh**) to the list. That should do the trick :) .
It was bugging the hell out of me too ;)

---

