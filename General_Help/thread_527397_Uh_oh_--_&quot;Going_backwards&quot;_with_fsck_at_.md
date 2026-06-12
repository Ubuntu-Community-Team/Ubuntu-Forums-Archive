---
title: "Uh oh -- &quot;Going backwards&quot; with fsck at boot.  Please help!"
date: 2007-08-16
forum: General Help
---

### Post by Phrawm48 on 2007-08-16
Uh oh -- running fsck at boot with FSCKFIX=yes is adding to my disk errors, not reducing or fixing them.

I ran *fsck -n* which identified two errors.

I then tried using *sudo touch /forcefsck* to force *fsck* to run at boot, then restarted.  *fsck* did indeed run at boot, but repeating *fsck -n* showed that it had not corrected the errors.

I then did a Web search and located [http://www.howforge.com/how-force-fsck-ubuntu](http://www.howforge.com/how-force-fsck-ubuntu) which explained that to make fsck fix errors at boot, I should edit */etc/default/rcS* and change the default value of FSCKFIX to read *FSCKFIX=yes*.

So I edited the file, then used *sudo shutdown -F -r now* to force a reboot.

After I rebooted I reran *fsck -n* -- uh oh, now it lists even more errors.  (I've attached them to this submission).

In other words,  I've "gone backwards" with fsck at boot: I started out trying to correct a couple of small problems and now have many more problems.

Evidently my little bit of knowledge is turning out to be a dangerous thing.  Although my Ubuntu system still boots and seems to work (I'm using it to create this post), my disk is accumulating fsck-induced errors.

So, can somebody please explain -- in relatively simple steps -- how can I sort his out?

Cheers & thanks,
Riley

---

