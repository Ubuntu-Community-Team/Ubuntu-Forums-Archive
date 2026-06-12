---
title: "Migrate wubi to and from USB?"
date: 2013-03-22
forum: General Help
---

### Post by lordscales91 on 2013-03-22
is it possible to move the wubi files to an USB, for making free space on the disk and be able to create a partition, and then run the wubi automatic migration script (with the appropriate parameters) to migrate it to the partition. It will work?

---

### Post by coffeecat on 2013-03-22
@lordscales91, you posted in this thread which is for discussion of the [MigrateWubi wiki page](https://help.ubuntu.com/community/MigrateWubi):

[http://ubuntuforums.org/showthread.php?t=2012400](http://ubuntuforums.org/showthread.php?t=2012400)

Technical support questions should be posted in support forums, so I've moved your post to its own thread in General Help.

---

### Post by bcbc on 2013-03-22
You can move the files to USB and then migrate using the --root-disk= option. Note that the migration script enforces that the architecture (64bit vs 32bit) of the live CD/USB matches that of the root.disk.

Also make sure all the .disk files (excluding swap.disk) are in the same location (this only applies if you have a usr.disk or home.disk). If you only have a root.disk, then that's all that's required.

See here for some examples: [http://ubuntu-with-wubi.blogspot.ca/2012/04/how-to-migrate-updated-for-release-1204.html](http://ubuntu-with-wubi.blogspot.ca/2012/04/how-to-migrate-updated-for-release-1204.html) (note that the screen shots are for an older version and the script is now called wubi-move.sh, i.e. doesn't contain the versino: wubi-move-n.n.sh)

---

### Post by lordscales91 on 2013-03-23
Oh, yeah, maybe I will do that soon. Thanks for your help

---

