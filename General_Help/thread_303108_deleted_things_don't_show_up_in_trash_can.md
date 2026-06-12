---
title: "deleted things don't show up in trash can"
date: 2006-11-19
forum: General Help
---

### Post by maniacmusician on 2006-11-19
Hey,

I was merrily using my computer today, when a program informed me that I was out of space on my hard drive. I thought to myself, "How can this be?" So resignedly set about looking for big files to delete. Found some big ol' ISOs and some home movies that had already been burned to DVD, and deleted them. Went to empty the trash can and voila, they weren't there! dissapeared! and of course, the same amount of space is left on my hard drive as before. So I'm left with no space, unable to delete things.

There is one folder in the trash can, but I am  unable to "empty" it. Maybe could be related?

I'm using KDE 3.5.5.

Thanks

edit: I found the problem...that folder I mentioned was indeed the problem...some of the items inside it were owned by root. so i chown'd the entire folder, and emptied; it's now gone, but the other items still don't show up in Trash...and if I delete them from .local/share/Trash/files, they just re-appear in them. I'm hoping a reboot will fix this, or just a restart of X. If it helps, this is the error I'm getting now: "Could not read /home/maniacmusician/.local/share/Trash/info/LimeWire 4.10.9 Pro.trashinfo."

---

### Post by maniacmusician on 2006-11-19
okay, I fixed the problem but it looks like something really weird is happening. I have some theories. But, it looks like Edgy is finally acting edgy for me. By the way, what I had to do to fix it was go in and delete all those files as root, and then go to the trash can of root, and empty them from there.

Okay, so I've been having this problem ([http://ubuntuforums.org/showthread.php?t=299914](http://ubuntuforums.org/showthread.php?t=299914) )...someone suggested a fix for it, and I tried it. It didn't work, and it also screwed up all my font settings, etc. Now here's where it gets weird. With this problem, after I rebooted, I found all my settings were back to normal. My menus were looking fine, and my fonts were looking okay. But now all my user settings for programs are screwed up...or at least "rolled back"...I didn't know this was possible in Ubuntu? For example, in Firefox, my new bookmarks from the past few days are missing and only older ones remain. And the new extensions I've installed are reverted to default/no configuration. So it looks like anything I've done recently with programs has been reverted. I havn't tried it in other programs yet, but this is definitely _weird_.

WTF is going on.

---

