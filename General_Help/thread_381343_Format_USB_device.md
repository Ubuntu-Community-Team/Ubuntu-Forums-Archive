---
title: "Format USB device"
date: 2007-03-10
forum: General Help
---

### Post by punkybouy on 2007-03-10
I have an old Sony USB memory stick (64 MB) .  Under Dapper I can format the device as root with the ext3 file system and add data as the logged in user (not root).   When carried to my Edgy desktop the device mounts automatically to the users desktop but I see no files.  I can then format the device on Edgy as root and it will mount to the users desktop but I can't add any files to it (not an option).  I suspect its a permissions issue.  It looks like root is user and owner but as root I don't seem to be able to change those permissions so the non-root user can use the device.  Any ideas?  Thanks for the help.

---

### Post by punkybouy on 2007-03-10
I found the answer here on the forum.
if its ext3 do the following:
1. Open a terminal
2. Type "sudo chown [your username] /media/nameoftheusbdrive". Press enter
3. Type "sudo chgrp [your username] /media/nameoftheusbdrive". Press enter again.

Thanks to ah, um....well thanks anyway.

---

