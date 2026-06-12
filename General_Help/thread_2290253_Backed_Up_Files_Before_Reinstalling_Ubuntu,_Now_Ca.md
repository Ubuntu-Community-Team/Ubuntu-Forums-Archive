---
title: "Backed Up Files Before Reinstalling Ubuntu, Now Cannot Restore"
date: 2015-08-10
forum: General Help
---

### Post by kfgross on 2015-08-10
Hi All,

Something happened while I was updating my Ubuntu 14.04 LTS, and the machine froze up.  Eventually all I could do was restart the system using a "Live" copy off of a flash drive.  While running off the flash drive, I used Deja Dup to back up files to an external USB hard drive.

I reloaded the machine with 14.04.2, but when I try to restore the backup I receive an error message that I don't have permissions to do so.  As a Linux newbie, I'm at a loss and hope that some of you might be able to help.

Thanks in advance,

Ken

---

### Post by TheFu on 2015-08-10
Linux is a multi-user OS.  Which userid and group did you use to backup the files?  It is the numbers that matter, not the name. Use those same userids/groupids to restore.

---

### Post by kfgross on 2015-08-15
> **TheFu said:**
> Linux is a multi-user OS.  Which userid and group did you use to backup the files?  It is the numbers that matter, not the name. Use those same userids/groupids to restore.

Thanks Fu.

I thought about what you said, and realized that I'd created the backup while using the "live" CD.  So I booted off of that, and got a bit further.  I'm able to select the folder and start the restore, but now have encountered a new problem.

When the restore starts I'm asked for an encryption password.  I know for a fact that I didn't select the encryption option when creating the backup.  It won't let me continue without entering a password.

Any thoughts?

---

### Post by TheFu on 2015-08-15
Without the encryption password, you aren't going to get very far.  That is the issue with duplicity-based backups (and tools based on it), they default to using encryption even if you don't want it.  A few years ago, one of the core devs for duplicity gave a talk at my LUG. I tried to make a backup using the tool without any encryption and couldn't figure it out. Perhaps I'm just stupid.  Looking at the features of duplicity, there is much to like.  

I use rdiff-backup and have for 6+ yrs.  No surprises. When it fails, it is vocal.  Plus it doesn't make some strange backup volumes, it makes a mirror for the current backup and compressed differences for earlier versions. Get restore the most current backup, you can use the tool or you can simply copy the file back and set the permissions.

None of this will help you. Sorry.  A backup without testing the restore is "hope" - it is not a "plan."  That is what experience as taught me.

---

