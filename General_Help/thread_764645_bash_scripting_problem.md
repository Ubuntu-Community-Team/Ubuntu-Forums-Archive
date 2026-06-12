---
title: "bash scripting problem"
date: 2008-04-24
forum: General Help
---

### Post by auskento on 2008-04-24
I have just built up a new Ubuntu server to replace one that died.
I had been using 6.06 LTS and have now installed 7.10 64 bit on the new hardware I have.

I have a file processing script i use with SABnzbd to move files and then change their attributes so my Dvico TVIX box can see the media files to play them back.

Since i updated to this new box and installation, there is something screwy going on.

In the script i have lines as follows

chmod -R $FILEACCESS "$DESTFOLDER"
chown -R $FILEOWNER "$DESTFOLDER"

I have put error checking in below these lines ie testing $? and the script output reports no errors, and in verbose mode, indicates that the files have been set to the right owner and with the right permissions.

However, if i look at the resulting folder, the permissions are at 700

I am at a loss as to why this has stopped working.

---

### Post by ibuclaw on 2008-04-24
Are you running the script as root?

Are you **sure** that the appropriate permissions are passed to the $FILEACCESS variable?

Regards
Iain

---

### Post by justleen on 2008-04-24
try running it like ```
 sh -x <scriptname> 
```

for some more verbose output..

---

