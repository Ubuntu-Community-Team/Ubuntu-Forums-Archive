---
title: "How do I Symlink to a network path containing spaces?"
date: 2007-07-01
forum: General Help
---

### Post by oomingmak on 2007-07-01
I have been trying (for the best part of 3 hours now) :( to make a link to network folder that has a spaces in the path.

After reading up on hardlinks and symlinks, it seems like symlinks are the way to go when linking to a remote location. I've read ln --help and tried to construct the command correctly, but although the link is created, it doesn't work (error dialog pops up saying that the link is "broken").

When I browse to the network folder using Nautilus, in the path name it inserts %20 where the space should be, but I don't know whether these %20s should be included in the ln -s command for the link target. I've tried with and without %20, but each time the link it creates is always broken. 

Also, for some reason the Link location path keeps gets appended to the front of the Target path (which then makes the Target path wrong).

So how should you create a local symlink to a samba shared network location that has spaces in the path? (I want to make my networked backup folder appear as if it's in my Home folder).

**Target:**  smb://myusername@192.168.1.20/Shared/Linux/Ubuntu 7.04/Backups

**Link**:  /home/name/Backups


Thanks in advance.

---

### Post by mpeters on 2007-07-01
> **oomingmak said:**
> I have been trying (for the best part of 3 hours now) :( to make a link to network folder that has a spaces in the path.

After reading up on hardlinks and symlinks, it seems like symlinks are the way to go when linking to a remote location. I've read ln --help and tried to construct the command correctly, but although the link is created, it doesn't work (error dialog pops up saying that the link is "broken").

When I browse to the network folder using Nautilus, in the path name it inserts %20 where the space should be, but I don't know whether these %20s should be included in the ln -s command for the link target. I've tried with and without %20, but each time the link it creates is always broken. 

Also, for some reason the Link location path keeps gets appended to the front of the Target path (which then makes the Target path wrong).

So how should you create a local symlink to a samba shared network location that has spaces in the path? (I want to make my networked backup folder appear as if it's in my Home folder).

**Target:**  smb://myusername@192.168.1.20/Shared/Linux/Ubuntu 7.04/Backups

**Link**:  /home/name/Backups


Thanks in advance.

I'm not entirely sure I fully understand what you're trying to link to where, but, when it comes to spaces in file names, escaping the space with "\" should do the trick, ie smb://myusername@192.168.1.20/Shared/Linux/Ubuntu\ 7.04/Backups

---

### Post by element3260 on 2007-07-01
Well if quotes doesn't work...

Try:
```
ln -s smb://myusername@192.168.1.20/Shared/Linux/Ubuntu\ 7.04/Backups /home/name/Backups
```

\ is the break character for a space (at least the one that I use most often) so whenever you have a space in a file name just but a \ before it (/home/mike/Desktop/Linux\ Hates\ Spaces/)

---

