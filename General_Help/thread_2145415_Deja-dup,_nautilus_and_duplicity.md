---
title: "Deja-dup, nautilus and duplicity"
date: 2013-05-15
forum: General Help
---

### Post by gianiaz on 2013-05-15
Hi, until some days ago I was simply using tar to create backups.
Now I've installed Ubuntu 12.04 LTS, and I'm taking a look at Deja-Dup.
I like it, but It doesn't support backups at a specific day hour. I did a lot of search, and finally understood that deja-dup it's simply not designed to work from cron. ([https://live.gnome.org/DejaDup/HowItWorks#Why_Not_Cron.3F](https://live.gnome.org/DejaDup/HowItWorks#Why_Not_Cron.3F) and [https://bugs.launchpad.net/deja-dup/+bug/479191](https://bugs.launchpad.net/deja-dup/+bug/479191)).
Doing my search i saw that Deja Dup is a back end for duplicity, and I found this guide: [https://help.ubuntu.com/community/DuplicityBackupHowto](https://help.ubuntu.com/community/DuplicityBackupHowto).
Now I'm able to backup my data using duplicity over ssh.
One feature I like very much is the ability to right-click on a folder (or a file) on nautilus and revert to previous version created by deja-dup. 
I've tried configuring Deja-dup to use the same folder (and server) I've used to upload backups created by duplicity, and when I right click on a folder I can see date and hour of the backup, but when I confirm the restore process exit with error "File not found in backup". I think is a problem related to relative and absolute paths, but I can't understand how to fix it.

Anyone has experience on this topic? 
Thank you :-)

---

