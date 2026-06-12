---
title: "transfer files between linux boxes on same lan"
date: 2007-02-21
forum: General Help
---

### Post by scottsanpedro on 2007-02-21
Hi,
I have two ubuntu boxes on the same LAN and want to transfer files between the two. One is test system and one is going to be new production server.
What would be the best way to do this?
Many thanks for any response...Scott

---

### Post by Falcorian on 2007-02-21
Well... There are a few ways.

You could set up folder sharing, using either Samba or NFS.

You could also use ssh (which would be slower I believe, because it encrytps everything) and then either use scp from the shell, or mount the ssh share as a file system.

You can find guides for those options around the forums. I use samba and I couldn't be happier with it. Allows fast transfers, and I can mount the other machines harddrive just like it was a drive on my machine.

---

### Post by scottsanpedro on 2007-02-21
thanks..i will look into these now
Scott

---

### Post by scottsanpedro on 2007-02-21
managed to get it working.
Went to System - Administration - Shared Folders
created the share name.
went to other computer and Places - Network folders and found the computer on our domain.
and found the share.
Just a note - it didn't show for ages. I went into the actual files and right clicked and shared there also. That show the same share name I had originally set up.
It then appeared, not sure if that was a coincedence
thanks
Scott

---

### Post by boredandblogging.com on 2007-02-21
If you are trying to keep files in sync, you might want to look into rsync.

---

