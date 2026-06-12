---
title: "[SOLVED] Move|copy files in one dir to another using ncftp?"
date: 2008-04-08
forum: General Help
---

### Post by x1a4 on 2008-04-08
Hi,

Is it possible--and if so how--to move or copy files from one directory to another on a remote host, using ncftp?  

I want to move files and directories in /art/gallery/ to /art/ on the remote host.  I tried using Nautilus but got a 'permission denied' error.  

If it isn't possible to do using ncftp how do I do it using Nautilus?

Thank you.

---

### Post by asbjorne08 on 2008-04-08
I've never seen the possibility to change the ftp-server directory structure like that from a ftp client.

The obvious way is to download it, and then upload it to the right place.

fxp could of cource be used if the server supports it, by opening two connections to the same server and copy.

---

### Post by x1a4 on 2008-04-08
That's what I thought.  Oh well, after I came home I just ssh'ed to my account and moved the files that way.

---

