---
title: "Where is MY Trash Folder"
date: 2006-07-15
forum: General Help
---

### Post by cssutto on 2006-07-15
I have the trash folder repeated over and over in my various backups.

Obviously wasting a lot of space.

So I did the  rm -rf .Trash/* thing and when I look in my /home/me/.Trash folder, it is empty.

However, the Trash bin at the bottom of my desktop still has lots of very large disk eating files in it.

Also, I still have the trash files on my backup drives.

I have tried cd to backup drives and running  rm -rf .Trash/* in them, with no luck.

How do I identify the proper folder so it can be zapped?

Since many of these trash files have permission problems, that must be considered.

CSSJR

---

### Post by Ramses de Norre on 2006-07-15
Open the trash can folder by clicking on the trash can, then select an item in it, right click it and select properties. There will be a line "Location: " where you can see where the file is located.

---

### Post by utnubu001 on 2006-07-15
er...bottom right hand corner..LOL
just kiddin!

---

### Post by Unknowndeepness on 2006-07-15
> **utnubu001 said:**
> er...bottom right hand corner..LOL
just kiddin!

Lol! Yeeaaah! Ive been looking for it for months! Thanx!
Haha :D

---

### Post by cssutto on 2006-07-15
Thanks for the suggestion.

However, I thought of that earlier and changed to that directory, which is on my external backup drive, and ran rm -rf with no results.

To be clear, I ran rm -rf on the folder that contained the trash file and it did not remove anything.

I then did a  rm -rf ~/.Trash/* 
on the trash file in that folder, and it is still there.

I believe this problem will go away now that I have used  rm -rf ~/.Trash/*

to empty the trash can because I back up with rsync using the delete option and now that the trash can is empty, the trash folder in the backup folder will be deleted.

I have been dragging entire directorys to the trash can.  Perhaps that is a mistake since the empty trash button  does not like to zap files that have permissions set to root or some other restriction.

Perhaps only simple files should go to the trash can and more complex directories should be rm -rf.

CSSJR

---

### Post by hugh_h_chen on 2008-05-20
this thread seemed very old, i dig this out by having a similar problem. see this thread, you will be ok. there are more than one trash in Ubuntu.

[http://ubuntuforums.org/showthread.php?t=509596](http://ubuntuforums.org/showthread.php?t=509596)

---

