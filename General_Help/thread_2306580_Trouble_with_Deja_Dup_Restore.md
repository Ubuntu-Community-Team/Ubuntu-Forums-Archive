---
title: "Trouble with Deja Dup Restore"
date: 2015-12-16
forum: General Help
---

### Post by David4321 on 2015-12-16
I'm trying to restore from a Deja Dup backup. My original system was Zorin 9, but when disk fried I moved to Ubuntu 14 installed on fresh disk. I don't think this is causing any problems, platform is the same, just thought I should mention it.

Most of the backup restored properly, but I was given a list of 46 files (unfortunately including some thunderbird inboxes and skype chatlogs I'd really like back) with the following error message: "Could not restore the following files. Please make sure you are able to write to them." I thought this might be a problem writing to areas of the new drive, so I ran the restore again, this time to a folder on another drive. Those files are not present in either extraction from the backup. 

Yes, I know, I'll find a better backup solution for next round. This is what I have to work with now.

I'm wondering:

1) Is there any way to get inside the duplicity archives and inspect for viable versions of these files?
2) What is meant by "Please make sure you are able to write to them."? What problem does this indicate?
3) Anything else I might try? Or are these files just probably just corrupted or lost? The log seems to remember them as belonging to the backup, they must have been there at some point.

Thanks!

---

