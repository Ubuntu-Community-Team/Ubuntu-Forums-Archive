---
title: "RECENT Klibido problems?"
date: 2007-08-30
forum: General Help
---

### Post by bostoncraig on 2007-08-30
Hey all.  Pretty new to Linux, but I've been finding my way alright.  My system is almost where I want it.

Anyway, I'm running Feisty with a Gnome Desktop.  I've been using KLIBIDO without problems to download a lot of files for a week and a half to two weeks.

Today when I started Ubuntu, there was an update:
(from Synaptic>History)
> Commit Log for Thu Aug 30 19:48:44 2007


Upgraded the following packages:
libwrap0 (7.6.dbs-11build1) to 7.6.dbs-11ubuntu0.1
tar (1.16-2) to 1.16-2ubuntu0.1
vim-common (1:7.0-164+1ubuntu7.1) to 1:7.0-164+1ubuntu7.2
vim-tiny (1:7.0-164+1ubuntu7.1) to 1:7.0-164+1ubuntu7.2



Tonight, when I went to use KLIBIDO, I kept getting the "There was an error writing to disk - The download queue has been paused. Chances are that the filesystem is out of space. Correct the error and restart the queue" error even though there was plenty of space on that partition. (I temporarily moved a 1.4GB file into the download directory to test.)

Tracked that down to a corrupt queue.  Deleted ~/klibido/db/queue and restarted as suggested in the klibido faq.  It would download a few more files, then I'd get the same message.:confused:

Is anyone else having similar problems all of a sudden?  If so, then it'd be the update?  If not, any suggestions?

Thanks,
Craig in Boston.

---

### Post by bostoncraig on 2007-08-31
edit: spoke too soon.

Problem still occuring.  Seems to be a bug they're working on.  Happens most often when you're updating one newsgroup while items from another are downloading in queue.

On a good note, though, I did learn how to rollback an update with Synaptic. :)

-C.

---

