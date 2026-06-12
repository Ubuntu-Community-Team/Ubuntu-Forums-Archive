---
title: "Folder turned into Photo whilst copying"
date: 2022-08-12
forum: General Help
---

### Post by metalcore2 on 2022-08-12
Hi everyone,

I'm not new to Ubuntu anymore, I'm using it since many years, but what happened to me today makes wonder what the hack is going on here.

I wanted to upgrade from 20 LTS to 22 LTS and therefore I backed up all my photos I had on my computer.
So I cut out all those (about 50GB) and and pasted them on my external harddrive. When done I made the upgrade. Everything worked pretty fine and I was happy.

BUT...

After this I wanted to put all my photos back and I didn't want to trust my self what I saw.
It were 3 folders I copied. But on my Harddrive were 1 folder and 2 fotos. The weird thing is, that the photos have the names of the two missing folders and folders them selves are gone. There should have been about 44GB in those 2 folder but now it's only 800kb left.

I'm sure there ist a lot of Data in the background that the system can't see right now.

Has anyone any Idea how to proof this and maybe bring back this data?


BTW: I already tried to look an this forum and on google for this topic, but please.... try to find an answer when looking for "Ubuntu folder turned in foto whilst copying"....


I really appreciate your help and ideas!

---

### Post by TheFu on 2022-08-12
A backup isn't a backup if the data isn't on 3 different storage devices.  If you copy the data from 1 device to another, then delete the original files, that isn't a backup.  Similarly, if you move all the data over, it is never a backup and bad things can happen.  I fear you've learned this the hard way.

The safe way to get pure data (not documents nor programs nor settings) to another HDD/storage device is to use rsync.
rsync validates that the source and target files match along the way.  Also, we can re-run the exact same rsync command immediately when it finishes to see that all files really are on the target storage.

```
$ rsync -avz SOURCE/  TARGET/
```

is the typical way to copy/update everything in the SOURCE to TARGET. Both should be directories and have the trailing '/' character. That means something special, so all .dotfiles are copied too.  The rsync manpage is very extensive. There are just a few tools that everyone needs to know.  rsync is in my top 5 list of those amazing commands.  ssh is another.

Of course, whenever we move or copy files, the OS does buffering and the commands will return well before all the data has actually been written.  If we reboot too soon or physically disconnect the target storage before all the writes are complete, that will cause data loss.  Use the 'eject' button to be certain data writes have completed.   Or type **sync** 3 times into a terminal. This command won't return until all data is flushed to disk. The extra 2 times running the command just provides a little extra proof that the buffers have been cleared.  Don't copy/paste the sync command. Type it each time. This is an old Unix admin technique I was taught decades ago.

For me, copying more than a few files using the GUI isn't something I do. GUIs, I've never trusted them after having too many failures over the decades.

---

### Post by coffeecat on 2022-08-12
Not a chat thread. *Moved to **General Help** support sub-forum.*

---

### Post by Impavidus on 2022-08-12
If you cut (as opposed to copy) from the internal harddrive and paste to the external drive, the originals on the internal drive are gone and the copies on the external drive are no backups. If you had left the photos on the internal drive, they would still be there is nothing went wrong.

Maybe the external drive is broken; maybe something went wrong when copying the files there. Maybe you removed the drive too soon. Writing 50GB takes a while. In that case, the files never were on the external drive. What filesystem is on the external drive? If they were actually written there, a filesystem check may recover some bits. Or try file recovery tools. In that case, first make a clone of the entire drive, then work from that clone.

File recovery tools may be able to find some pictures on your internal drive, but during an upgrade so much is written, that a large part will be overwritten now. Unless you kept these files on a separate partition, like a /home partition, instead of the root partition. If they were on a /home partition, the upgrade won't have overwritten them.

---

