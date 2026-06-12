---
title: "Can I use Back In Time to back up the same files to more than one drive?"
date: 2019-04-22
forum: General Help
---

### Post by naomibrown on 2019-04-22
Hi,

I've already got one drive that I save backups to, using Back In Time. I'm now trying to set up my new drive so that Back In Time will also save exactly the same back up to this new drive. Is it possible? 

So far I've tried opening up settings and changing "Where to save snapshots" but then I've pressed cancel when it says "Do you want to change the snapshot folder?". I don't want to change the original snapshot folder, I want to add another folder too.

I've tried looking online and didn't find out how to do this, the closest thing that I could find was [https://answers.launchpad.net/backintime/+question/81902]("https://answers.launchpad.net/backintime/+question/81902") from 2009, where someone said it wasn't possible yet. 

As an alternative, could I just copy the backup folder from the old drive? Ideally I wouldn't need to do this manually though. 

Thanks,
Naomi

---

### Post by TheFu on 2019-04-22
I haven't looked at BiT in about 8 yrs. Had it working on Mom's PC for a few years. Her backup needs were very trivial and storage efficiency wasn't all that important for her setup.

If you need multiple backups, I'd do a chain.  
Original --> BiT --> 1st copy --> rsync --> 2nd copy.

Because BiT uses hardlinks, very specific steps are necessary to avoid having 50 full copies of the entire backup.  Hardlinks only work within a single file system.  rsync has options to control that. Actually, I suspect BiT using librsync internally to do the same stuff.

---

### Post by naomibrown on 2019-04-25
I'd completely forgotten about that (don't ask!). So I set that running once I'd figured out how to do it, and it's been running since a couple of hours after you posted. I've got about 1.5TB of data to transfer from a Seagate Expansion 3TB disk to another one the same, just 6GB. I've realised I don't know how to find out how long it's going to take.... and probably should have set that as an option before I started. I'm guessing it isn't, but is it possible to set that now?

---

### Post by naomibrown on 2019-04-29
I've been waiting for it to finish copying and I've just re-read your post. I must have been more tired than I thought as I didn't remember the part that said about hardlinks. I've used: rsync -avz media/nb/SeagateOldDrive/_backup/HomeDesktopBackup/BackInTime/backintime/ media/nb/SeagateNewDrive/OldDriveCOPY/ which I'm guessing isn't correct as it's not finished and it's been running about 6 days. 

Can anyone give a suggestion for what I should use instead? I'm getting very confused with the options I should be using instead when reading the man page to ensure that I don't get lots of copies of the same files, as I'm copying Back In Time files.

---

