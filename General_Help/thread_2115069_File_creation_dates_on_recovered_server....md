---
title: "File creation dates on recovered server..."
date: 2013-02-11
forum: General Help
---

### Post by t2service on 2013-02-11
Hi, hope I'm posting this in the right spot.
 I'll be brief as possible: 
New client calls me with a crashed file server running FreeNas7, corrupt file system. I am able to recover all data and retain creation/modified dates.
I replaced FreeNas with Ubuntu Server 12.xx with a Samba share.
I transferred clients files (via SFTP) to the new share. 
I had to change group ownership of files and directories with the chown and chgrp commands.
Everything is perfect...except- All file creation and mod dates are now the same (the date I recovered them).
It's enough of an issue that I will do it again to correct this but I'm unsure of the method that will retain dates keeping in mind that I must also change ownership.

Many thanks in advance for your thoughts on this - 

Ts

---

### Post by LewisTM on 2013-02-11
Use **rsync** instead of SFTP. The -aAX switches will conserve everything, including metadata (date, permissions, owner, ACLs, xattrs). Add -v for some verbose feedback
```
rsync -avXA /local/directory sshuser@nasIP:/target/parent/dir
```
Cheers!

---

