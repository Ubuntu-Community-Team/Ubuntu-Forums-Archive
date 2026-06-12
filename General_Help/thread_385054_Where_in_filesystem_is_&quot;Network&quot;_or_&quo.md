---
title: "Where in filesystem is &quot;Network&quot; or &quot;SMB&quot;?"
date: 2007-03-15
forum: General Help
---

### Post by mjpatey on 2007-03-15
I just installed a program on my Ubuntu machine that will be accessing a shared file on another machine (I hope).  In the program's "Open File" dialog, it only lists locations in the local filesystem.

Is there somewhere in Ubuntu's filesystem (besides smb:// itself) that gives access to shared network files?  Like a link?

I've tried creating a link on the Desktop to the folder that the remote file lives in, but the program I'm using doesn't open this link, as it will only open actual folders, or files of its native type.  The program I'm referring to is Moneydance, by the way.

Thanks for any help you may have!

-Mark

---

### Post by DavidTangye on 2007-03-15
If the File Open dialog cannot go up beyond File System, ie local files, then I am guessing you cannot access beyond local files.
If you install and enable the nfs server and portmapper on the server, and nfs client (and portmapper?), and define nfs "exports" on the server, you can then nfs-mount the nfs exports on client machines. I mount these at /mnt/nfs-[host]/[export]. Any file open dialog will find these at this spot as if they are part of the local filesystem.

---

### Post by mjpatey on 2007-03-15
Sounds good, David!  I just did a search on NFS servers for Windows, and found a few to try.  I'll give it a shot!  Of course, I could just slide over to her computer to work on the finances, but how much fun would that be?

-Mark

---

### Post by Detonate on 2007-03-15
If you mount the remote folders and files they will be accessible through the normal browsing of the file system.

---

