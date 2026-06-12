---
title: "making a folder within another folder without really transfferring the contents?"
date: 2017-07-14
forum: General Help
---

### Post by ronjjjg8885 on 2017-07-14
Hi
I wish to make the music and videos that are in my hd link to my ssd where my os is running from, so when i enter the music folder it will show the content of music of my hd folder.

It should be done in a secured way, so when I will share the files they will be relatively secure.

Hope it's clear to understand
I would appreciate a solution

---

### Post by Dennis N on 2017-07-14
One way would be to make a symbolic link in your Music folder to the folder on your HD.

cd to Music Folder and run the command (with items inside <  > supplied by you):
```
ln -s <full-path-to-HD-folder> <link-name>
```
to create such a link. Do not include the < and > symbols in the actual command.

---

### Post by TheFu on 2017-07-14
*[symbolic links]("https://en.wikipedia.org/wiki/Symbolic_link")* or [bind mounts]("https://unix.stackexchange.com/questions/198590/what-is-a-bind-mount").  These work locally.

Remote file sharing is different.  Just create multiple network shares. Good media servers understand multiple shares for the same sort of content.

---

### Post by ronjjjg8885 on 2017-07-14
the "ls" command will be great for local purpose. i see.

but ok. i created the network share with samba (pc to libreelec).
i followed all of this article:
[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated%2C%20Simple%20and%20Brief%20Way%21](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated%2C%20Simple%20and%20Brief%20Way%21)

but. after all of the configuration on the pi side it told me something like 'no access'. (i've tried to add the music folder and open it. it did actually show the computer name (my ubuntu) but it doesn't had access.

i must mention that i did the last step by browsing the smb shares and not by typing this:
```
[COLOR=#333333][FONT=Ubuntu]To access your network share use your username (<user_name>) and password through the path "smb://<HOST_IP_OR_NAME>/<folder_name>/" (Linux users) or "\\<HOST_IP_OR_NAME>\<folder_name>\" (Windows users). Note that "<folder_name>" value is passed in "[<folder_name>]", in other words, the share name you entered in "/etc/samba/smb.conf".[/FONT][/COLOR]
```

in the past i could actually access the music folder. but the problem back then was that it was shared from the ssd and not where the actual music is located with is the HDD

please assist
and thank you

---

### Post by TheFu on 2017-07-14
A few important things - the link to the [prior thread about this]("https://ubuntuforums.org/showthread.php?t=2363101") would help others.  This does seem to be that same question again.

LibreELEC is the normal capitalization, I believe. That would prevent some confusion.  I was seeing a Library, not Libre.   In Unix, words that begin with "lib" generally imply a library - almost universally.

Want a LibreElec device to access stuff on an Ubuntu box.  
Won't use NFS or DLNA methods.  
Want to use samba.
Won't make multiple shares to similar content on different disks, as was suggested. Perhaps this wasn't understood?

Did I miss anything?

---

