---
title: "Nautilus fails to copy, reports &quot;Not on the same file system&quot;...?"
date: 2007-10-22
forum: General Help
---

### Post by dwasifar on 2007-10-22
I have two nfs shares set up on a server (running Edgy).  My desktop (running Feisty) is connected to these; they are mapped in fstab to two local folders as mount points. 

When I try to move or copy anything from one of these folders to the other, Nautilus throws up an error box: 'Error "Not on the same file system" while moving [/path/filename].  Would you like to continue?'  Clicking Retry just refreshes the error box, ad infinitum. I thought at first it might be a permissions issue, but I have the same problem even when running Nautilus as root.  Nautilus will move files in either direction between a remote share and folder on the local drive, but not between two folders that are both remote shares.

I can do the moves just fine using Thunar or from the commandline, running as a normal user.  It's just Nautilus that won't do it.

---

### Post by macjones on 2007-12-25
Try pessing shift-del, not just del.

[http://ubuntuforums.org/showthread.php?t=388487](http://ubuntuforums.org/showthread.php?t=388487)

Mac 
New Zealand

---

### Post by AndyC_772 on 2007-12-28
I have the same problem - it's not just when deleting (by moving to .Trash), it affects any copy from one NFS share to another. The bug seems to be new in Gutsy.

Any fix yet?

---

### Post by OliW on 2007-12-30
I get the same(ish)

I have a physical raid array mapped through to /media/hobo
I have my /home mapped from /media/hobo/home

When I try and move something to my /home/user directory from /media/hobo/*, it thinks it's on the same filesystem (which it technically is - same hardware) so. by default tries to move it when dragging. When I release the mouse button (in move mode) it throw up the same error.

I'd rather that it was stupid and thought it was on a different fs (so it copied by default) or it worked so I don't have to toss around copying *then* deleting files to move them.

---

### Post by Versusnja on 2008-03-06
Shift+Del works. Thank you!

---

