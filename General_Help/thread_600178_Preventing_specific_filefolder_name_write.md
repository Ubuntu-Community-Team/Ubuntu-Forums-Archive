---
title: "Preventing specific file/folder name write?"
date: 2007-11-02
forum: General Help
---

### Post by patrickweber on 2007-11-02
I've got a simple file server (running Ubuntu, of course) that I use to move files back and forth between OS X and Windows machines.  Unfortunately, all the operating systems (XP, Server 2003, Vista, Tiger, Leopard) leave traces of themselves floating around (OS X being notably worse than Windows).

What I'd like to do is prevent certain files from being written to the hard drive, probably by checking the file names on the file operations.  These files are something like:

.Trash-*username*
.AppleDB
.AppleDesktop
.AppleDouble
:2eTemporaryItems
Network Trash Folder
Temporary Items
:2eDS_Store
Thumbs.db
etc..

I'm not sure why the .DS_Store files are being written with the . replaced by the :2e, but I digress.

I can't go to every machine and modify each so that they don't write the files, but I'd really like to not have the files there to begin with and a cron job running every once in a while isn't preferred either (although I guess if that was my only option..).

There has to be some simple solution to prevent certain file names from being written, I just am not sure of what that solution is.  Any ideas?

---

