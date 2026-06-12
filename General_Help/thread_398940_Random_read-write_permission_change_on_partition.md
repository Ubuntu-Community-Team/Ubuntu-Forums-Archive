---
title: "Random read-write permission change on partition"
date: 2007-04-01
forum: General Help
---

### Post by Laen on 2007-04-01
Hello,

I recently created a new ext3 partition to use with my current Linux installation. It's listed in fstab as follows:

/dev/hda2 /media/hda2 ext3 defaults 0 2

I've set the /media/hda2 to have my user as an owner so I can use it as sort of a second home directory for storage.
Everything seems to be working in the beginning - I'm able to read and write to the partition. However, after some time I lose those permissions and when attempting to write I get an error stating that the drive is read-only. I can umount and mount the partition again and everything's back to normal for about 20-30 minutes.

Instead of the defaults flag I've tried using auto,users,rw, which does the same thing.
You can imagine how annoying that can be if you're downloading a torrent for example.
I would greatly appreciate any suggestions, thanks.

---

