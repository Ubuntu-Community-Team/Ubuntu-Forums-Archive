---
title: "e2fsck errors"
date: 2015-05-20
forum: General Help
---

### Post by meanmrmustard on 2015-05-20
I'm running e2fsck on a hard disk with a single partition - data only.
The normal superblock is corrupted so I ran it with:
-b 32768

After checks it reported:
Free block count wrong for group #0 (25513, counted=23393)
fix<y>?
I hit enter the next message was the same for group #1
etc.

After hitting enter for the default "yes", it continues to report wrong free block count for group after group, presently up to group #4296.

Should I stop the process where I am to run it again with another option to speed up the repair?... or will that cause more issues?

---

### Post by dino99 on 2015-05-20
[http://askubuntu.com/questions/379572/how-do-i-get-fsck-to-fix-the-errors-it-is-reporting](http://askubuntu.com/questions/379572/how-do-i-get-fsck-to-fix-the-errors-it-is-reporting)
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)
[http://manpages.ubuntu.com/manpages/vivid/man8/e2fsck.8.html](http://manpages.ubuntu.com/manpages/vivid/man8/e2fsck.8.html)

---

### Post by meanmrmustard on 2015-05-20
Yes, thanks but I see no mention of my specific situation where the command is running but I'd like to stop and re-run it with specific flags and what might happen if I do.

---

### Post by tgalati4 on 2015-05-21
You can use the -y switch to answer "yes" to the fix questions.  Yes, there is a risk of messing up your disk even more than it is now.  I would read up on data recovery and make an image of the drive and perform a file recovery on that with *testdisk* first.  Normally free block counts are corrected in one or two passes--usually due to a sudden shutdown or reboot.  If you have a continuous string of bad counts, then that could indicate more serious trouble.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

