---
title: "Simple backup"
date: 2007-07-21
forum: General Help
---

### Post by Udidin on 2007-07-21
Hi all,

Linux newb alert, although I'm not a complete eejit :)

Here's a summary of my problem:

I've just installed Ubuntu Feisty, and have it set up as I like it with all my extra applications and whatnot. This is installed on one of my two HDD's, the 80gb.

I have another 200gb mounted as /media/hdb1 (ntfs with write support via ntfs-3g) which I use for long term storage.

I'm looking for an easy way of backing up my whole system (basically the entire contents of the 80gb), storing the backup on the 200gb. 
I'm thinking of just taring everything.

However, I want to exclude all the data that is currently on the 200gb from the backup, or it will be huge, and thats all backed up elsewhere anyway.

In the event of a total restore, I want the 200gb to be accessible as it is now, with the same mounting etc, but it should be untouched by the entire process.

If I exclude /mount/, would I have to mount everything again after a restore?

I'd imagine that this is quite simple, I'd imagine a tar file that I could extract over the 80gb to revert it to its pristine condition would do, it's only about 6gb, but I need to double check everything, as losing the contents of the 200gb would be a monumental pain in the neck.

Hope someone can help (preferably with terminal commansds, god I'm cheeky) and thanking you anyway,

Udi.

---

### Post by bernied on 2007-07-21
Maybe the easiest way goes something like this:
- boot a live-cd (your install cd)
- mount your root filesystem and your external drive
- create the tar archive
eg
```
sudo su
mkdir /mnt/{tempsource,tempdestination}
mount -t ext3 /dev/hda1 /mnt/tempsource
mount -t ntfs /dev/hdb1 /mnt/tempdestination # not sure about this, is ntfs write support available on live-cd?
mount   # check that all is good
cd /mnt/tempsource
tar -cvf /mnt/tempdestination/backup.tar ./
```
If you do this offline then you avoid all problems with mounted filesystems, and also the proc, tmp, sys and dev filesystems which all (maybe not all?) do funny things when you're runnng live.

If you keep any other partitions - say for home for example - then you need to mount these as well before the tar.

---

