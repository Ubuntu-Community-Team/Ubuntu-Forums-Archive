---
title: "Can't save to SMB from OpenOffice"
date: 2007-07-26
forum: General Help
---

### Post by brion on 2007-07-26
I hope that this is the right place to post this question, and if it has already been answered countless times, please point me at a solution (I didn't find any when I searched).

I am using OpenOffice (presentation application).  I can save a file to my main Ubuntu directory, but when i try to Save  As to a network drive (SMB) it fails ("General Error - General Input/Output Error).

However, if can easily copy (with the Ubuntu explorer) the file from my main Ubuntu directory to the network directory, so I know that I'm allowed to write there.  Why is OpenOffice failing when I try to write directly to the network directory?

Thanks,

Brion

---

### Post by MrHippocampus on 2007-07-26
Ive heard of the problem before but I don't remember seeing a solution :(

One way you can work around the problem is to either mount the share you want to write to as part of your file system. That way the networked folder will be in e.g. /media/netfolder, openoffice should have no trouble saving in there because it will just see it as another normal folder.

There are two ways to do this the first is to mount the share with cifs, the second is to mount the whole windows network as a folder using fusesmb. I havent done either of these but they should both work, just searching the forum/google for "cifs" or "fusesmb" should work :)

---

### Post by brion on 2007-07-26
Unfortunately, it already is mounted.  At least I think so.    I found it on the network and indicated "Connect to this Server" and now it shows up on my desktop and in the explorer.  That  means that it is mounted, right?

---

### Post by MrHippocampus on 2007-07-26
Its a bit complicated to explain, but doing it that way means its mounted using gnome-vfs, which a program has to be specifically programmed for to be able to use it. e.g. if you use gedit you should be able to save to that location quite happily because it knows about gnome-vfs and can use it.

By using a cifs or fusesmb mount a program doesn't have to do anything special as the share is part of the greater file system starting at /, the cifs/fusesmb share is simply another folder in the system and not anything special so any program can write/read to/from it as normal.

---

