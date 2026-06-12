---
title: "How to delete a directory that won't delete due to &quot;Input/output error&quot;?"
date: 2015-11-15
forum: General Help
---

### Post by bc9 on 2015-11-15
My PC: an older Core 2 Duo Dell running Ubuntu 14.04LTS quite nicely from an internal SSD boot drive (Ext4 format), with some external USB data drives (NTFS format).


The other day, a error dialog popped up when I tried to open a directory on an external drive: 


**"Sorry, could not display all the contents of "directoryname": Error when getting informaton for file '/media/username/drivelabel/affecteddirectoryname/filename': Input/output error"**


This caused some concern as you might imagine: Ubuntu's Unity file manager GUI would only show a single subdirectory in the affected directory (instead of the hundreds it actually contained). I opened a Terminal window and went over to the affected directory and there, I COULD at least see/list the subdirectories inside and even see three null (zero byte) files that included the "...filename': Input/output error" item. I was willing to sacrifice those three now-null directories (thinking that they were corrupted) but though I could list them in a Terminal window, I couldn't delete them from the command line there, getting a "file does not exist" error (I copied/pasted the names, so the error isn't from a typo).


What I finally did was this: I used Krusader (an alternate file manager GUI) which, unlike Unity's file manager, *would* let me list *all* the contents of the affected directory (including the three null items). In Krusader, I then selected and MOVEd all the subdirectories inside the affected directory to a new/temp directory on the same drive, however I purposely did NOT move the three null items. That seemed to work alright: the new/temp directory contained everything EXCEPT the three null items and it seems to open/work fine via the Unity file manager GUI. So, the immediate problem is solved: I've got my data (I can recover the three null items (subdirectories) later from a backup) and all's well.


However, I cannot actually delete the original affected directory or the three null files inside it: when I try to delete it, I get a similar error as at the start:


**"Error while deleting.**

**There was an error getting information about the files in the folder “affecteddirectoryname”.**

**Show more details**

**Error when getting information for file '/media/username/drivelabel/affecteddirectoryname/filename'': Input/output error"**


...nor can I delete that directory using Terminal or Krusader (using the rm -rf line command, Terminal returns a **"cannot remove... Input/output error"** and Krusader returns a **"file does not exist error"**).


If anyone could suggest an explanation about what's going on, and/or tell me how to resolve it (delete the now-empty-except-for-three-null-items directory) I'd really appreciate it (I did try the 'Check If Already Posted' button here w/no results). Thanks in advance for any help. :)

---

### Post by oldos2er on 2015-11-16
Sounds like your drive is dying, if it's not dead already. You can check it with [smartctl]("https://help.ubuntu.com/community/Smartmontools") to be certain.

---

### Post by bc9 on 2015-11-16
Thanks for the quick reply oldos2er! 

Though bad media is certainly possible, the drive involved is only a couple months old. It's one of three identical (WD My Book) drives purchased at that time and there've been no other known problems with any of them. Also, I should mention that it's been many, many years since I had *any* new drive fail (from any brand/of any type) ...even cheap drives are so reliable now compared to 20 years ago, when I could expect to lose one a year (hence my backup discipline). That doesn't mean new drives can't/don't fail of course... it just seems much less common.

Since I MOVEd the files in the affected directory to a new directory on the same drive (and replaced the three lost directories from a backup) I haven't noticed any other problems (yet). All the other data on the drive seems alright. Should that change or I see any new errors, of course I'll say so. 

The original affected directory, which contains the three 'do not exist'/null directories is still there of course, and I still can't delete it (I guess I could/should try putting the drive on another PC to see if that makes any difference).

When examining the drive via the Disks tool built-in to Ubuntu, the SMART Data & Self Tests choice in the menu is greyed-out, so I'm assuming that SMART can't be used to test this drive. However, I'll ***will*** install the Smartmontools you linked to anyway (*thanks* btw!), read the instructions and then reply here if I've got any new info to share as a result. 

Thanks again!

---

### Post by yancek on 2015-11-16
Since you indicate in your original post that the partitions on your external drive including the problematic one are ntfs formatted, I'm curious as to what happens when you try to delete from windows.  Have you run chkdsk from windows?

---

### Post by bc9 on 2015-12-24
> **yancek said:**
> Since you indicate in your original post that the partitions on your external drive including the problematic one are ntfs formatted, I'm curious as to what happens when you try to delete from windows.  Have you run chkdsk from windows?

Sorry for the delayed reply. 

At this point, I've just been using the drive and renamed the directory that I can't delete to BROKENDIR. There's no other visible oddness... all of these new identical drives have been running fine, with no other weirdness. I haven't moved the drive to a Windows system... I have an Win laptop for work, but since the drive is now full of my data, I'm reluctant to mess with it. 

When I try to move BROKENDIR to the trash, I get two dialog boxes... the first says: "BROKENDIR can't be put in the trash. Do you want to delete it immediately?" I see that message frequently since moving most of my data to the external NTFS drives (didn't used to get this message when the externals were Ext4) so I click "Delete" as I always do (bearing in mind that the Delete won't be undoable since the item won't be moved to the trash... this has something to do with how Ubuntu deals with NTFS I assume). 

After I tell it to Delete, I get a second dialog which says "There was an error getting information about the files in the folder BROKENDIR" ...and more details says "Error when getting information for file '/mediarestofpath/filename that no longer exists/was already deleted' : Input/output error" It seems to be looking for info about files that NO LONGER EXIST, and since it can't get that info, it won't let me delete the BROKENDIR directory. This is the same error I get when I try to OPEN the BROKENDIR directory too by the way: it won't show any files, but the directory is empty (reports zero items inside and I moved everything out of it when I got the new drive).

At some point, I'll probably have another attempt at getting rid of the BROKENDIR, but for now, it's just there.

---

### Post by Vladlenin5000 on 2015-12-24
It looks like your drive has logical errors, not physical (hardware) errors. Equally annoying and often presenting the same symptoms, the big difference is the former are correctable. Unfortunately you can't fix it from Linux because it has no such tools for NTFS.

I bet if you connect that drive Windows as suggested the first thing you'll see is a popup telling you it has errors and offering to correct them. Accept it, wait for the error correction tool to do its job. Done!

---

### Post by bc9 on 2015-12-24
> **Vladlenin5000 said:**
> It looks like your drive has logical errors, not physical (hardware) errors. Equally annoying and often presenting the same symptoms, the big difference is the former are correctable. Unfortunately you can't fix it from Linux because it has no such tools for NTFS.

I bet if you connect that drive Windows as suggested the first thing you'll see is a popup telling you it has errors and offering to correct them. Accept it, wait for the error correction tool to do its job. Done!

Thanks for the quick feedback. As mentioned, I do have access to a Windows laptop so I can plug the drive into it, though just to be safe I think I'll probably wait until just after I've backed up the drive, as I'd kick myself if Windows borked it, costing me data (w/o a up-to-date backup).

I have this thread bookmarked, so I won't lose it and when I plug the drive into the Win laptop, I'll come back and post here about the results. Thanks again to all. :)

---

### Post by Vladlenin5000 on 2015-12-24
I agree with your strategy, better safe than sorry.
That said, over the years I stumbled upon many similar situations, and Windows always corrected them without any issues.

---

### Post by bc9 on 2015-12-24
> **Vladlenin5000 said:**
> I agree with your strategy, better safe than sorry.
That said, over the years I stumbled upon many similar situations, and Windows always corrected them without any issues.

I'm glad to hear it, as having that undeletable directory sorta irks my OCD. ;) I appreciate the help and will reply here when I know more. Thanks again Vlad!

---

