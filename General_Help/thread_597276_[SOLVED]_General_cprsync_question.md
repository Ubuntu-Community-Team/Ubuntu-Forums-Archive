---
title: "[SOLVED] General cp/rsync question"
date: 2007-10-30
forum: General Help
---

### Post by dcollamore on 2007-10-30
I know this isn't an Ubuntu specific question, but all systems involved are running Ubuntu or variants, and I love the community here, so here I am.

I have four systems on a network backing home directories up via an rsync script to a backup server, on which I have rsnapshot configured to rotate these backups daily, weekly, and monthly.  My backup server is going to be completely replaced soon, and I need to migrate all of these backups and snapshots to a new server.  Here's the question: These 'snapshots' consist of almost entirely hard links, with only changed files actually moving from one snapshot to another through rotation.  All of the original backups and snapshots are under one primary directory on the same filesystem.  Everything I've tried with either cp or rsync to copy this backup tree to my new server has resulted in the hard links being treated as individual files, blowing the size of my backup directory into mammoth proportions.  

Does anyone with more knowledge of the nuances of cp or rsync have a suggestion as to how I can accomplish this without eating an inordinate amount of disk space?

Thanks in advance!

---

### Post by kebes on 2007-10-30
Have you tried using rsync with the -H (a.k.a. --hard-links) switch? This should maintain hard-linking as long as all of the links that point to the disk file are included in the rsync list to copy.

Apologies if that's one of the things you've already tried...

---

### Post by dcollamore on 2007-10-30
Perfect!  That did it!  I think I must have misread the man page....

---

