---
title: "Finding network Files"
date: 2006-11-24
forum: General Help
---

### Post by Fire on 2006-11-24
I have a samba server running on Xubuntu.  I used Kino to download all my video from my video camera and all of the video is on a drive shared through samba.  I want to use kinos to edit and create a video.  I can't seem to see the samba shares when using kinos.  This is the case for many programs.  It doesn't seem to be able to see the folders that are shared from the server.  What do I need to do to make these files show up in all programs...

---

### Post by psyeye on 2006-11-24
Difficult question.

Problem is: your program (here: "kino" - never tried it, though) needs to be able to cope with files over the network. E.g. gedit can transparently edit files, because it's using Gnome-VFS "fully".

So Kino seems to be restricted to local files.

A workaround would be: mount these SMB-shares locally, using smbmount. Kino should then be able to open these files.

Real solution: file a bug with Kino ;-)


hth
psyeye

---

### Post by Fire on 2006-11-24
I was trying to do the smbmount but i get the following:

bash: smbmount: command not found

I don't know a lot about samba and am still learning.. so any help with that would be great.

---

