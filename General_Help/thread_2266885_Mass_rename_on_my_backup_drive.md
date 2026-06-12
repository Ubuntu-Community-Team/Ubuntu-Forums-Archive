---
title: "Mass rename on my backup drive"
date: 2015-02-26
forum: General Help
---

### Post by jwbrase on 2015-02-26
I've been using Back In Time as a backup solution, and in a fit of complete idiocy attempted restoring a whole-filesystem backup with the system I was trying to restore booted, instead of from a live CD.

As a result, not only did the restore not complete, but it also put the system into an even worse state than what had prompted me to do the restore (I haven't tried booting from anything but I LiveCD since I borked the system, but from everything that I know wasn't working when I shut the system down, I doubt it will boot at this point).

Even worse, my error confused Back In Time so badly that it tried restoring a folder that had not been part of the original backup, which meant it "deleted" every file on my backup drive. Fortunately, no data has actually been lost, when Back In Time "deletes" or overwrites files during a restore, it renames the file on disk to have ".backup.$DATE" appended to the filename and then copies the version of the file from the backup to the original filename (or leaves only the renamed file if the file does not exist at all in the backup). So my backup still exists in a relatively consistent state, but is not immediately restorable due to the filenames being corrupted.

Can anybody advise on the best way of removing a common suffix from several hundred thousand, if not several million, files in a directory tree? And can anybody familiar with Back In Time advise whether this will be sufficient to restore my backup to usability, or whether I will need to take other steps?

---

### Post by TheFu on 2015-02-26
I used back-in-time for a few years - it works by creating new directories based on a timestamp and using hardlinks to older files that match at the current snapshot time and copying over any newly modified files from the source.

I don't think you want to rename all those files.  I think you want to restore from the prior backup, just before the one you've screwed. Does that make sense?  Hopefully you were using the beautiful backup scheme which provided hourly (for 2 days), daily (for the current week), weekly (for the current month), monthly (for the current year) snapshots - so your backup area should have plenty of options that can be restored.

You don't need to use the tool to restore anything. Just use a recursive copy.  **sudo cp -rp**

I found back-in-time to be too wasteful with storage, failed to capture permissions changes over time and I didn't like the softlink handling. Switched to rdiff-backup and haven't looked back. It isn't perfect either. I just find the warts to be the least of the 20-or-so other backup methods I've tried.

---

### Post by jwbrase on 2015-02-26
> **TheFu said:**
> 

I don't think you want to rename all those files.  I think you want to restore from the prior backup, just before the one you've screwed. Does that make sense? 

Yes, but...

>  Hopefully you were using the beautiful backup scheme which provided hourly (for 2 days), daily (for the current week), weekly (for the current month), monthly (for the current year) snapshots - so your backup area should have plenty of options that can be restored.

I was using that feature, but unfortunately, there is no backup before the one I've screwed, because I managed to screw all the ones. The entire backup drive is screwed, not just a single backup.

Fortunately, I've managed to contact the developer and obtain a solution that I think should work.

> 

You don't need to use the tool to restore anything. Just use a recursive copy.  **sudo cp -rp**

I found back-in-time to be too wasteful with storage, failed to capture permissions changes over time and I didn't like the softlink handling. Switched to rdiff-backup and haven't looked back. It isn't perfect either. I just find the warts to be the least of the 20-or-so other backup methods I've tried.

---

### Post by TheFu on 2015-02-26
So is it a state secret or will you share? ;)

---

