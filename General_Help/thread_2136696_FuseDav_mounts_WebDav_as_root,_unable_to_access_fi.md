---
title: "FuseDav mounts WebDav as root, unable to access files."
date: 2013-04-18
forum: General Help
---

### Post by SASDOE2 on 2013-04-18
Hi all, 

Having a little trouble, I am trying to install a deluge box on a raspberry pi. The rpi would download it's files to an another computer's webdav (or ftp, but webdav seems to be the better option) directory. Only thing is when i try to mount the webdav directory, fusedav does so as root (because I need to run it as sudo), and makes it unavailable to the main user. 

How could I set fusedav to either mount the directory as the "pi" user, or to mount it with 777 permissions ?

Also running chmod - 777 doesn't work at all obviously.

There is an -o option for fusedav, however I can't seem to find any mention of options available. Tried -o rw just in case, to no avail.

---

### Post by SASDOE2 on 2013-04-18
Ok solved this one myself for once.

Here is how I did, and it's not even a workaround which is something rare on my behalf, way !

Simply add -o default_permissions,allow_other,uid=1000,gid=1000 (or whatver your uid and gid are, simply do an " id " in the command prompt to find out) at the end of your fusedav command and you're golden !

---

