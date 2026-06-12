---
title: "Spideroak Alternative?"
date: 2019-11-04
forum: General Help
---

### Post by wpwend42 on 2019-11-04
Running 18.04...

Longtime user of Spideroak, but have had a lot of problems with it in the past few years. Right now the app won't even backup and I had to put in a support message (which they are generally helpful with).

What else is out there for backup on Ubuntu? I have a lot of music/video files and need an app that can handle that. Thanks!

---

### Post by Frogs Hair on 2019-11-04
I have not used this software , but  Tresorit for Linux comes up as an alternative.

---

### Post by TheFu on 2019-11-04
Are you tied to off-side, cloudy, storage?

If not ...

I do local backups using rdiff-backup, then rsync those between 2 external HDDs and swap those out at work (locked desk, so not exactly secure) every week.  The external HDDs are LUKS encrypted.

For a few years, I used rsync to Mom's house after taking a pre-seed disk during a visit.  Again, this was the rsync of the rdiff-backup stuff, so anything new was just relatively tiny diffs.  rdiff-backup doesn't use hardlinking for versioning, unlike straight rsync methods.

Music and video is NOT included in the data that goes offsite.  I have the original CDs and DVDs, which are part of the house insurance (photos+video for claims).  It would be a hassle to re-rip all that media, so I do keep an rsync mirror on separate disks from the primary storage.  12TB is hard to deal with off-site, unless you have 1 of those new huge-huge-huge 12TB disks. I do not.  Getting it back will be months.

What have you looked at already?  Any core requirements?

---

### Post by dragonfly41 on 2019-11-04
Not a backup media but you might also look at[ zotero]("https://www.zotero.org/") standalone app plus its associated browser connector to create a reference library for your collections.

---

### Post by ndstate on 2019-11-04
I switched from Spideroak to Crashplan a few years ago. I am also looking at a 2nd cloud backup option. What are your requirements/feature desires?

---

