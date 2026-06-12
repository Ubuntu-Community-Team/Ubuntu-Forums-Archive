---
title: "backup everything in hardy"
date: 2008-04-26
forum: General Help
---

### Post by oddworld on 2008-04-26
I have my Hardy install working perfectly!
Now I want to somehow back it all up in case I do something to screw it up or crash it.
Will copying home accomplish that or do I need to do more?

---

### Post by timetunnel on 2008-04-26
That depends on what you want to achieve. If you don't care about reinstalling ubuntu and you just want to make sure that all your personal settings and documents are restored after a new install (and you have all your documents in your home folder), making a copy of the home folder should suffice.

However, reinstalling everything is quite time consuming, so what I always do after a fresh install: create a harddisk image of the partition. In case my harddisk fails I just have to restore the image into the new harddisk and everything is back there in less than an hour.

"partimage" is a good tool for that, it's part of the Knoppix distribution and the System Rescue CD.

---

### Post by ghost_ryder35 on 2008-04-26
> **timetunnel said:**
> That depends on what you want to achieve. If you don't care about reinstalling ubuntu and you just want to make sure that all your personal settings and documents are restored after a new install (and you have all your documents in your home folder), making a copy of the home folder should suffice.
 
However, reinstalling everything is quite time consuming, so what I always do after a fresh install: create a harddisk image of the partition. In case my harddisk fails I just have to restore the image into the new harddisk and everything is back there in less than an hour.
 
"partimage" is a good tool for that, it's part of the Knoppix distribution and the System Rescue CD.
copying your home directory is sufficient.  but like timetunnel said making an image (if you have the room) saves a lot of time

---

### Post by igfud on 2008-04-26
Your home folder will be sufficient for documents, pictures, music etc. that is stored there. If you want to do a full backup, you can create a tar of your disk (make sure you have enough room free to do so!).  Heliode has a nice how to [here]("http://ubuntuforums.org/showthread.php?t=35087").

You can create a script that will create a tar with any folder you like.  You can add this script to your log off process, or just run it whenever you want a backup.  You can find a thread [here]("http://ubuntuforums.org/showthread.php?t=764274&highlight=igfud") on how to do this.

igfud

---

### Post by elmer_42 on 2008-04-26
As everyone is saying, if you just want to backup your settings and documents, you can just backup your home folder. If you have an external drive, I would reccomend using it. For the purpose of this command, I am going to assume that it is /media/sda2. Whenever you want to backup your home folder, run this command. Make sure you change user and host to your username and the name of your computer.
```
rsync -av user@host:/home/user/ /media/sda2/home_backup
```

---

