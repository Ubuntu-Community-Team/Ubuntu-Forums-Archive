---
title: "deleted files do not appear in trash"
date: 2007-06-09
forum: General Help
---

### Post by vadania on 2007-06-09
I delete files (move them to trash), but they do not appear in trash folder and unused disk space does not improve as a result of my action. Still, the file icon does disappear from the initial directory / folder.

---

### Post by orb9220 on 2007-06-09
> I delete files (move them to trash), but they do not appear in trash folder and unused disk space does not improve as a result of my action. Still, the file icon does disappear from the initial directory / folder

Did you look in both .trash folders? There is one for root / and then there is one in your home folder.

---

### Post by vadania on 2007-06-09
Of course not! 
But there aren't just 2 trash folders:
Which ones should I check:
/home/lost+found/
/lost+and 
/home/Recycled/
/home/userName/.Trash
/home/.Trash-root...

---

### Post by FuturePilot on 2007-06-09
The /home/username/.Trash one

---

### Post by vadania on 2007-06-10
I created a folder *pi1234567* (to give it a distinctive name).
I deleted the folder pi12... I did not find the deleted folder in /home/user_name/.Trash, but I did find a bookmark on the left Dolphin toolbar saying "Trash". I clicked on it and "surprise!", I found all the deleted files.

Once I found the deleted files, I cleared (empty) Trash in Dolphin, and I got more free space.

This leaves one question though: where does exactly Trash in Dolphin point to?
I had right click on it and got an option "Edit bookmark...". When chose it a window poped up, saying something about *trash:/*. Now that trash:/ must have something to do with KDE settings, right? (Dolphin is a KDE application). 

So the problem is where does trash:/ in KDE point to?

---

### Post by rand0m on 2007-07-19
Did you figure this out? I just started using Dolphin and realized the same thing.

---

### Post by vadania on 2007-08-05
Yes, I figured it out.
Dolphin is a KDE app and uses KDE's settings for trash.
If you access Dolphin's builtin trash you will probably find all your missing junk.

---

### Post by rand0m on 2007-08-05
Yeah, I got used to using the Dolphin trash link. It's easy to forget though.

---

