---
title: "Migrating RAID1 array from 2tb to 4tb drives"
date: 2014-01-07
forum: General Help
---

### Post by Taxcheat on 2014-01-07
I want to replace a RAID1 array on my file server that's currently a pair of tiny 2tb drives with pair of shiny new 4tb drives. I thought it would be easy: fail the array, swap in one big drive, sync, repeat, then expand the array. Presto. More storage makes me happy. I replaced a dead drive once, it's pretty straightforward.

Except I learned that 4tb requires gpt, and my 2tb drives are ext3. So I see a big problem in the "expand" step, and the partition formating. Is there actually a way to do this cleanly, or is my only option to create a brand new 2x4tb array and copy the data over from external backup? 

I googled like crazy on this question and found it asked but never answered. I have a feeling "copy data" from an external backup is easier, but knowing why will help me understand what I'm doing better.

Running 12.04 server headless. Thanks in advance for any insight.

---

### Post by TheFu on 2014-01-07
Sorry, no magic bullet solution.

RAID is not a backup, so you need this already. If there is concern that the backup won't work, then it really isn't a backup.  I've migrated to new HDDs a few times and always did the backup/restore method. For this step, rsync is usually the best tool so that downtime is minimized.  Run it once to get 99.9999% of the data moved over, then take the main RAID offline to other users and re-run the rsync. Should take just a few minutes to sync the last changed blocks.

BTW, when you partition the new array - be certain to size it so that backups of whole partitions fit on your backup media.

---

