---
title: "Accessing computer via USD-Flash-Disk"
date: 2023-09-19
forum: General Help
---

### Post by bjngchn on 2023-09-19
Here is the situation.
This laptop has grub error, nothing helped, so  decided to format it, 
but first need to make a copy of potentially important files.

Tried to login with USB-flash (had no hope initially).
Yes, worked, in DOLPHIN clicked encrypted drive (home folder and more),
typed encryption pw and on DOLPHIN can see home folder contents. 

But, chmod status is 700, user/s can do anything, others can do nothing. 
So I'm acting as an external user, and probably not  as admin either (correct?)

So what I plan to do NOW:
Change CHMOD STATUS to 777 for all user/s under HOME directory. 

QUESTION 1: HOW DO I CHANGE CHMOD STATUS for everything under HOME directory? ,..
 while I'm only a FLASH-DISK-USER (not sure if root or admin)

QUESTION 2: I want to be able to VIEW/MOVE/.. files/directories.
HOW DO I DO IT?
I mean, can I do it with Dolphin (drag-drop)?
Also wondering how it can be done with cp. 

QUESTION 3: I want to move/copy files but to WHERE?
Can I move/copy them to another flash disk?
Can I move/copy them to the same flash disk? 

QUESTION 4: I will install a new KUBUNTU.
Which one do you recommend: Newest one has multiple serious problems.
(internet connection disconnects in minites, can't logout a user)
So newest one is not ok. 
ALSO want to be able to use K3B and write to CD/DVD. 
Unlike newest ones, this computer has CD-drive.
For sure I must be able to write to CD.
Writing to CD failed when this computer was fully alive, maybe
I should have used even an older kubuntu.
Or do I need to install K3B separately?

QUESTION 5: Can I fix grub error at this stage easily? 
I mean, I can access to computer already, up to Chmod restrictions.

You may not answer all but any answer is appreciated in advance.
The most important being, the first one.

So basically I want to understand how exactly this flash-disk-user acts.
Is it like any other user? is it like root or admin?
How do I change user? normally I would do su user, which seems to be not working.

---

### Post by SeijiSensei on 2023-09-19
If you are talking about running a session from the installation media (via "Try Ubuntu"), then the default "ubuntu" user has administrative privileges. You can, for instance, mount your hard drive partitions so you can back up the files. If you have another spare USB drive, I'd use that as the target for the backup, not the installation media.

Most recent KDE distributions don't require any special software to rip CDs. When you put the disc in the slot, Kubuntu will present it visually in a variety of versions depending on the codecs it finds on your machine. I almost always use FLAC. You can also choose between a single rip of the entire work, or ripping just individual tracks.

I'd stick to Kubuntu 22.04 until next year. The next version with long-term support will be 24.04 arriving next April.

---

