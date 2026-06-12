---
title: "Deleting Files from USB key."
date: 2006-11-27
forum: General Help
---

### Post by Kittie Rose on 2006-11-27
I deleted some files from my USB key but no space was freed up. What's wrong? How do I fix this?

---

### Post by mssever on 2006-11-27
I'm not sure if I understand you correctly, but here's a shot: did you unmount the drive before removing it? Linux tends to cache writes for an opportune time--not necessarily when it says that it has finished. The umount command forces Linux to finish all writes. If you just pull the drive, it doesn't always have a chance to do that--sometimes it can even result in corrupted files.

---

### Post by Falcorian on 2006-11-27
Did you eject it (by right clicking it selecting eject) or just pull it out?

I noticed a few days ago that if I deleted files, and then pulled the USB drive out without ejecting it, the files were not actually deleted, it was only when I ejected the drive that it worked.

EDIT: Looks like mssever and I had the same idea at the same time... ;)

---

### Post by munkyeetr on 2006-11-27
This may help...
Check for a hidden folder .Trash and delete its contents.

---

### Post by munkyeetr on 2006-11-27
Just to clarify, that .Trash folder will be on the USB key ;-)

---

### Post by UbLnoy on 2006-11-27
It probably didn't really delete anything.

I've noticed that when I plug my thumb drive into
one of my windows machines, there's usually a trash
folder that shows up, which still has all the stuff
that I'd tried to delete in Ubuntu.

I just delete it with windows.

---

### Post by kosmic on 2006-11-27
> **munkyeetr said:**
> This may help...
Check for a hidden folder .Trash and delete its contents.

Yes that will do it. :)

---

### Post by wastrel on 2006-11-27
I bet you're using Nautilus to delete them and it is helpfully creating a 
trash folder on the usb key and moving the files there.  This removes them 
from sight, but doesn't free up space on the drive. 

You can go into Edit > Preferences > Behavior  in Nautilus and check the 
box a the bottom "Include a delete command that bypasses trash".  Then to 
delete things on the USB drive, right-click and choose "Delete".

Naturally, be careful - this will permanently delete things with no undo.  
Make sure there's nothing in those folders you really wanted :]

Cheers,

David

---

### Post by strabes on 2006-11-27
when you 'delete' files (move them to trash), they are put in a directory called .trash-username on the root directory of the volume. You can either just keep deleting this directory (press ctrl+h in nautilus to see hidden files) or you can enable the option in nautilus to delete files permanently, bypassing the trash. To do this, in nautilus go to edit, preferences, go to the behavior tab, then check the last option, "Include a Delete command that bypasses the Trash"

---

