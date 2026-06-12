---
title: "Help! All Emails Gone!!!"
date: 2007-01-08
forum: General Help
---

### Post by AslansWorld on 2007-01-08
I'm running Dapper Drake. I was backing up my .evolution folder and things went nuts with the folder somehow. All I did was try to drag it to write it to a disk. (I'm doing a fresh install of ubuntu so I didn't care if I completely removed it or not, I just wanted to make sure I had a copy) Before doing so I took a look at it to make sure everything was there and noted it said the file contained 4,3333 items under "properties". I drug it to the desktop to my grouping of "things to write to disk before erasing my system" but it immediately dissappeared from the desktop. I thought I had accidentally misplaced it so I began looking for it.   It was no where to be found. I went back to the home folder and tried to drag it to the desktop again but got a message saying it was already on the desktop. I told it to replace the one on the desktop and it too dissappeared. I opened up the "desktop" folder and found that I could see it in the desktop folder but not on the desktop itself. When I rechecked it's properties it had somehow magically gone from 4,3333 items to 32 items! Now, heres where it gets really interesting....

From that point on I tried moving it back to the home folder, writing it to disk, copying it and pasting various places and EVERY time it is moved, even if it is simply written to a disk without touching any file in it or anything (not even opening the folder) the amount of items in the file, it's contents, and it's size changes completely!!! It's gone from 4,3333 items to, 32 items, to 2,250 items, to 545 items, etc. It's size has ranged from over 100 MB down to a few KB, then back up again. When I open it, it's contents keep changing. Evolution is of course now blank, no emails, schedule, contacts, nothing. Taking a perfectly good .evolution folder with 4,333 items and writing it to disk somehow turns it into a folder with all the major FOLDERS in it but no FILES in them! When I try to search for an email (using Beagle) it finds the emails but when you try to tell it to open them the screen pops up blank. (VFolder is now empty by the way)

So...are my emails just gone forever?????? I've tried everything...rebooting, killing evolution, restarting evolution. The original .evolution folder in the home directory is all messed up because when I tried to give up and simply return the folder back to it's original location I ended up with a .evolution file on the desktop with a weird red - and + sign and the original file has not been the same since (a reboot got rid of that weird file but everything just seems lost. Searching for anything with "mbox" in it turns up nothing.

HELP!!!!!!!!!!!  ](*,) :confused: :frown:

---

### Post by dcstar on 2007-01-08
> **AslansWorld said:**
> I'm running Dapper Drake. I was backing up my .evolution folder and things went nuts with the folder somehow. All I did was try to drag it to write it to a disk. (I'm doing a fresh install of ubuntu so I didn't care if I completely removed it or not, I just wanted to make sure I had a copy) Before doing so I took a look at it to make sure everything was there and noted it said the file contained 4,3333 items under "properties". I drug it to the desktop to my grouping of "things to write to disk before erasing my system" but it immediately dissappeared from the desktop. I thought I had accidentally misplaced it so I began looking for it.   It was no where to be found. I went back to the home folder and tried to drag it to the desktop again but got a message saying it was already on the desktop. I told it to replace the one on the desktop and it too dissappeared. I opened up the "desktop" folder and found that I could see it in the desktop folder but not on the desktop itself. When I rechecked it's properties it had somehow magically gone from 4,3333 items to 32 items! Now, heres where it gets really interesting....

From that point on I tried moving it back to the home folder, writing it to disk, copying it and pasting various places and EVERY time it is moved, even if it is simply written to a disk without touching any file in it or anything (not even opening the folder) the amount of items in the file, it's contents, and it's size changes completely!!! It's gone from 4,3333 items to, 32 items, to 2,250 items, to 545 items, etc. It's size has ranged from over 100 MB down to a few KB, then back up again. When I open it, it's contents keep changing. Evolution is of course now blank, no emails, schedule, contacts, nothing. Taking a perfectly good .evolution folder with 4,333 items and writing it to disk somehow turns it into a folder with all the major FOLDERS in it but no FILES in them! When I try to search for an email (using Beagle) it finds the emails but when you try to tell it to open them the screen pops up blank. (VFolder is now empty by the way)

So...are my emails just gone forever?????? I've tried everything...rebooting, killing evolution, restarting evolution. The original .evolution folder in the home directory is all messed up because when I tried to give up and simply return the folder back to it's original location I ended up with a .evolution file on the desktop with a weird red - and + sign and the original file has not been the same since (a reboot got rid of that weird file but everything just seems lost. Searching for anything with "mbox" in it turns up nothing.

HELP!!!!!!!!!!!  ](*,) :confused: :frown:

You "moved" (instead of copying) your .evolution folder (a hidden folder) to your desktop.

You then wiped that folder out by moving a new version of the .evolution folder to the desktop to replace it.

Unless the original folder is in your Trash, I would say that you have deleted your e-mails.

---

### Post by AslansWorld on 2007-01-09
I didn't think simply dragging something to the desktop would erase everything inside every folder (actually, it erased SOME things and left others, then erased some other things on the next attempt and left different ones) It's never worked that way before. Every other folder I drug remained unchanged (even other "hidden" folders). It seems weird it only happened with the .evolution folder. Unfortunately I have no copy of it in the trash because I never tried to delete it. It's confusing. I always drag folders into the CD/DVD creator window to burn them and usually have no problem. I don't know what changed this time. Looks like I'm SOL email wise.

Anybody know WHY this occurred only with this folder??? Is the rule with this folder that you cannot copy it? I tried right clicking and copying it but it still kept changing over and over again. What's up with that? Why can't you just drag something and then, if you change your mind just drag it back without it freaking out? What did I do wrong? I "drug" it because right clicking made it disappear into thin air on the desktop. (I should probably mention that I could actually see it on the desktop for a short while before it vanished)

Any ideas???

---

### Post by koenn on 2007-01-09
you could not see the .evolution folder on your desktop because it's a hidden folder. Hidden folders are invisible (!) by default  so on your desktop, you just wouldn't see it - but it's there 
(as dcstar also suggested). 
the 'short moment' that you could see it probaby is a small "refresh" delay in the desktop. 

you can verify this by putting a creating a testfile , give it a name that starts wit ., and drag it from a nautiluswindow to the desktop. 

I'm not 100% sure about the move >< copy thing etc.

---

### Post by Revolution on 2007-01-09
Dragging files will always MOVE unless its to a different mount point.
Holding down CTRL and dragging and will COPY the files.

Evolution may have still been running when you MOVED the hidden folder to your desktop.
In this case it would create a new blank database for emails when is dicovered everything was gone.

Lesson learnt. Emails gone.

---

### Post by koenn on 2007-01-09
> In this case it would create a new blank database for emails when is dicovered everything was gone.
That's the other thing I was wondering about. If evolution does not use flat files to store emails (but some sort of database or some sort of organized directory tree, index files etc.), viewing that folder through a file browser *might* give unpredictable / unreliable results such as the "ever changing" number of items. 
And indeed, the second "drag to the desktop" could then have overwritten the original database with a freshly created empty copy.

---

### Post by Revolution on 2007-01-09
Evolution uses databases to store emails. Each mail folder has its own datafile and corresponding index. Its worth a browse through the .Evolution directories to get to know how its arranged.

I did an upgrade from Version2 to Version3 Evolution and managed to backup/move files as there were slight differences in the way the files were organised but thankfully the data files were compatible.

*edit.
After refreshing my memory (it was a while back) Evolution uses a directory structure arranged much as you see it in Evolution itself. All mail databases sit in the .evolution/mail/local folder. You'll see Inbox, Drafts, Outbox etc. Each has a set of 5 files associated with the folder name.
inbox.ev-summary
inbox.ibex.index
inbox.ibex.index.data
inbox
inbox.cmeta

Same for outbox and drafts and so on.
All user created mail folders live in their own subdirectories under the /local directory.

---

