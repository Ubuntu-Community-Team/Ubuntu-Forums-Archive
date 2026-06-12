---
title: "Is this a sound backup?"
date: 2012-12-30
forum: General Help
---

### Post by Cadeyrn on 2012-12-30
I've switched from using fsarchiver to a new system. I used dd to copy my laptop's entire hard drive to an external hard drive of identical size and changed the UUIDs of the external's copied partitions. I then learned about rsync and am now using the following commands.

backup from a live USB/CD environment:
```
rsync -vaE --delete /mnt/sda1 /mnt/sdb1
```

backup from the OS itself:
```
rsync -vaE --delete --exclude=/proc/* --exclude=/backup/drive/mount/point/* / /backup/drive/mount/point/
```

I'm asking for any criticisms. What I'm most worried about is how reliable the online, live backup method is. I figured it must be OK because TimeVault and Flyback use rsync within the live environment, but I saw errors with many files in /sys/ that make me worried.

If I use the latter command regularly, will I still have a carbon copy that, in the event of disaster, I can dd back to my laptop and boot from, losing nothing? And if I do still have to boot into a live USB/CD to update my backup with rsync, should I overwrite this one with a new dd since I've been backing it up from within my OS?

---

### Post by Cadeyrn on 2012-12-31
ba-dum-bump

---

